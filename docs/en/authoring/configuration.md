# Authoring Libraries

Include generated `public.typelib.js` file in the package and add information to the `package.json` about it.

```json5
{
    "name": "demo",
    "main": "dist/index.js",
    "files": [
        "dist/index.js",
        "dist/public.typelib.js" // < 1. Include the generated typelib file
    ],
    "reflection": { // < 2. Add this section
        "metadata": "dist/public.typelib.js"
    },
}
```