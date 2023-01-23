# Generic Classes

```typescript
class Foo<T>
{
	constructor()
	{
		const TType: Type = getType<T>();
		console.log(TType.name);
	}

	printClassAndMethodTypeArgName<U>()
	{
		const TType: Type = getType<T>();
		const UType: Type = getType<U>();
		console.log(TType.name, UType.name);
	}
}
```

## Demo
Try this out on [StackBlitz](https://stackblitz.com/edit/rttist-playground-generic-class?file=src%2Findex.ts).