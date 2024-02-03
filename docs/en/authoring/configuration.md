# Authoring Libraries

## Configuration
Update your `package.json` file to include the `reflection` property with the path to the `public.typelib.js` file. 

Don't forget to include the `public.typelib.js` file in the `files` property.

```json
{
    "name": "demo",
    "main": "dist/index.js",
	"reflection": {
		"metadata": "dist/public.typelib.js"
	},
    "files": [
        "dist/index.js",
        "dist/public.typelib.js"
    ]
}
```



[//]: # (There is nothing special to do. You don't have to add any special JSDoc tags, any special decorators nor parameters. Everything just works out of the box.)

[//]: # ()
[//]: # (In your library you will have access to all the types and modules of your library and end-user applications and they will have access to all your types and modules.)

[//]: # ()
[//]: # (## Optimizations)

[//]: # (To im prove the performance of end-user's transpillation, you can include your `typelib.metadata.js` file in the package and add information to the `package.json` about it.)


[//]: # (```json)

[//]: # ({)

[//]: # (    "name": "",)

[//]: # (    "reflection": {)

[//]: # (        "typelib": "dist/metadata.typelib.js")

[//]: # (    },)

[//]: # (    "files": [)

[//]: # (        "dist/index.js",)

[//]: # (        "dist/metadata.typelib.js")

[//]: # (    ],)

[//]: # (    "dependencies": {)

[//]: # (        "rttist": "latest")

[//]: # (    },)

[//]: # (    "devDependencies": {)

[//]: # (        "tst-reflect-transformer": "latest")

[//]: # (    })

[//]: # (})

[//]: # (```)