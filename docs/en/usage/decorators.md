# Decorators

```typescript
@decorateClass
class Foo {
	@decorateProperty
	propName: string = "";

	@decorateMethod
	methodName(@decorateParam param: boolean): true {
		return true;
	}
}
```


## Class Decorator
```typescript
function decorateClass(target: Function) {
	const type: Type = getType(target);

	console.log(type.name);
}
```


## Property Decorator
```typescript
function decorateProperty(targetPrototype: any, prop: string) {
	const type = getType(targetPrototype);
	const propInfo: PropertyInfo = type.isClass() && type.getProperty(prop);
	
	console.log(propInfo.name, propInfo.type.toString());
}
```


## Method Decorator
```typescript
function decorateMethod(targetPrototype: any, method: string) {
	const type = getType(targetPrototype);
	const methodInfo: MethodInfo = type.isClass() && type.getMethod(method);

	console.log(methodInfo.name);
}
```


## Parameter Decorator
```typescript
function decorateParam(targetPrototype: any, method: string, parameterIndex: number) {
	const type = getType(targetPrototype);
	const methodInfo = type.isClass() && type.getMethod(method);
	const paramInfo: ParameterInfo = methodInfo.getSignatures()[0].getParameters()[parameterIndex];

	console.log(paramInfo.name, paramInfo.type.toString());
}
```

## Demo
Try this out on [StackBlitz](https://stackblitz.com/edit/rttist-playground-decorators?file=src%2Findex.ts).