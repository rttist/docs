<script>
setPagination(
    undefined,
    "/en/getting-started/installation"
);
</script>

[![tst-reflect](https://img.shields.io/npm/v/rttist.svg?color=brightgreen&style=flat-square&logo=npm&label=rttist)](https://www.npmjs.com/package/rttist)
[![License MIT](https://img.shields.io/badge/License-MIT-brightgreen?style=flat-square)](https://opensource.org/licenses/MIT)

<!-- ![Code coverage](docs/_images/coverage-badge.svg) -->

# RTTIST
<sup><i>Pronounce /ˈɑː(r)tɪst/ the same as Artist.</i> Means Run-Time Type Information System for Typescript.</sup>

> Advanced TypeScript runtime reflection system, inspired by the C#'s reflection.


<img src="/_images/logo-mark.png" alt="Reflect" align="left" style="padding: 2em 2em 2em 0;">


## About
<p style="text-align: justify">
This project is all about runtime <strong>reflection</strong>. 
TypeScript itself contains rich type information but it is all dev time only. 
But TypeScript provide its compiler API, with access to type checker and ability to transform the code. 
Using this API we wrote a transformer plugin for TypeScript which generates runtime type information 
and modify your code slightly so you can reflect your types, even type parameters of classes, methods and functions.
</p>

<p style="clear: both;"></p>

For more information check our website [rttist.org](https://rttist.org) or docs [docs.rttist.org](https://docs.rttist.org).


## Alpha
This project is currently in alpha phase.
There still may be some major changes, but no such changes are expected.

If you participate in Alpha, use our discord mentioned in the [github.com/rttist/rttist](https://github.com/rttist/rttist) README.


## Showcase
[//]: # (TODO: List of StackBlitz examples)

```typescript
import { getType, Type, PropertyInfo, MethodInfo } from "rttist";

interface Employee {
    name: string;
    salary: number;
    sayHello();
    sayHello(toSomebody: string);
}

const type: Type = getType<Employee>();

if (type.isInterface()) {
    const properties = type.getProperties().map((prop: PropertyInfo) => prop.name);
    const methods = type.getMethods().map((method: MethodInfo) => method.name);

    console.log(properties); // > [ name, salary ]
    console.log(methods); // > [ sayHello ]

    const sayHelloMethod: MethodInfo = type.getMethods().find(m => m.name === "sayHello");
    const signatures = sayHelloMethod.getSignatures()
        .map(sig => {
            const parameters = sig.getParameters()
                .map(param => param.name + ": " + param.type.name);

            return `sayHello(${parameters.join(", ")})`
        });

    console.log(signatures); // > [ sayHello(), sayHello(toSomebody: string) ]
}
```

## Performance & Compatibility
**Performance**

Because of generic type parameters, the source code is modified. 
Several function calls and variable declarations are added to the source code which will make your program a little slower.

**Compatibility**

> This package introduces real generic classes, so for example class `Logger` is not the same class as `Logger<User>`!
> 
> `Logger<User>` is subclass of `Logger`.

To fully support **generic class** type parameters, all generic classes are wrapped by our classes which change default behavior a little.
If you use `instanceof` operator, there will be no problem. 
If you access constructors of class instances from their prototype, you'll get different constructor than you expect.

Each specific generic class is a subclass of your generic class declaration.

Lets have any generic class.
```typescript
export class Logger<TContext> {
	
}
```

If you use this class like this:
```typescript
const logger = new Logger<User>();
```
new class `Logger<User>` will be created and instantiated at runtime instead of base `Logger` class. 
It's the same behavior as C#, Java and other languages have (they just generate those classes at compile time).


```typescript
class Logger<TContext> // This is a declaration of generic type
{
	log(...args: any[])
	{
		console.log(...args);
	}
}

const logger = new Logger<User>(); // Logger<User> is generic class, inheriting from Logger<T> declaration

// This will not work as expected
if (Object.getPrototypeOf(logger).constructor === Logger) // false
{
	// ...
}

// This is OK
if (logger instanceof Logger) // true
{
	// ...
}

const userLoggerType: Type = getType<Logger<User>>();
const loggerType: Type = getType(Logger);

if (userLoggerType.isClass() && userLoggerType.isSubclassOf(loggerType)
	&& userLoggerType.isGenericType()
	&& userLoggerType.genericTypeDefinition.is(loggerType)
	&& userLoggerType.genericTypeDefinition.isGenericType()
	&& userLoggerType.genericTypeDefinition.isGenericTypeDefinition()) // true
{
	// ...
}
```


## License
This project is licensed under the [MIT license](./LICENSE).
