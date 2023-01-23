# Generic Functions

```typescript
function printFunctionTypeArgName<T>()
{
    const TType: Type = getType<T>();
    console.log(TType.name);
}
```

## Demo
Try this out on [StackBlitz](https://stackblitz.com/edit/rttist-playground-generic-function?file=src%2Findex.ts).