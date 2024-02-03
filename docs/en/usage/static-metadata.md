## Static Metadata
When you generate the metadata, you can access it statically by importing `Metadata` from the generated `metadata.typelib.ts` file.

`Metadata` is an object with declaration:
```typescript
export declare class MetadataLibrary {
    /**
     * Returns the first Type from the library that satisfies the provided predicate.
     * If no Type satisfies the predicate, undefined is returned.
     * @param predicate
     * @returns {Type | undefined}
     */
    findType(predicate: (type: Type) => boolean): Type | undefined;
    
    /**
     * Returns all the Types contained in the library.
     */
    getTypes(): Type[];
    
    /**
     * Returns the first Module from the library that satisfies the provided predicate.
     * If no Module satisfies the predicate, undefined is returned.
     * @param predicate
     * @returns {Module | undefined}
     */
    findModule(predicate: (module: Module) => boolean): Module | undefined;
    
    /**
     * Returns all Modules contained in the library.
     */
    getModules(): Module[];
    
    /**
     * Returns a Type instance identified by the id. Returns Type.Invalid if no Type found.
     * @param reference
     */
    resolveType(id: string): Type;
    
    /**
     * Returns a Module instance identified by the id. Returns Module.Invalid if no Module found.
     * @param reference
     */
    resolveModule(id: string): Module;
}
```
