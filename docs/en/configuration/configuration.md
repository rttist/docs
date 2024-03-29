# Configuration

[//]: # (## Config file&#40;s&#41;)

[//]: # (Config file is optional. By config files, you can change default behavior of metadata and/or transformer.)

[//]: # ()
[//]: # (There are three ways how to configure **RTTIST**.)

[//]: # ()
[//]: # (1. Create file `reflect.config.json`,)

[//]: # (    ```json)

[//]: # (    {)

[//]: # (        "metadata": {)

[//]: # (            "encode": false)

[//]: # (        },)

[//]: # (        "logLevel": "Warning")

[//]: # (    })

[//]: # (    ```)

[//]: # (2. or create file `reflect.config.js` with `default` export. )

[//]: # (    Exported value can be config object directly or Promise resolved to config object.)

[//]: # (   )
[//]: # (    > To use async config &#40;JS config exporting Promise&#41; you have to install package `deasync`, because TS compiler does not allow async operations.)

[//]: # (   )
[//]: # (    ```javascript)

[//]: # (    module.exports.default = {)

[//]: # (        metadata: {)

[//]: # (            encode: false)

[//]: # (        },)

[//]: # (        logLevel: "Warning")

[//]: # (    };)

[//]: # (    ```)

[//]: # (3. In case you use ttypescript or ts-loader with webpack, you can use tsconfig.json.)

[//]: # (    ```json)

[//]: # (    {)

[//]: # (        "compilerOptions": {)

[//]: # (            // Your options...)

[//]: # (            "plugins": [)

[//]: # (                {)

[//]: # (                    "transform": "tst-reflect-transformer",)

[//]: # (                    // configuration in "reflection" property)

[//]: # (                    "reflection": {)

[//]: # (                        "metadata": {)

[//]: # (                            "encode": false)

[//]: # (                        },)

[//]: # (                        "logLevel": "Warning")

[//]: # (                    })

[//]: # (                })

[//]: # (            ])

[//]: # (        })

[//]: # (    })

[//]: # (    ```)

## Config Options
### metadata.include
List of glob patterns matching modules which should be included in metadata.

Default pattern `**/*`.

### metadata.exclude
List of glob patterns matching modules which should be excluded from metadata. Overrides `metadata.include`.

Default pattern `**/@types/node/**`.

### metadata.metadataTypelibPath
Path (fileName) of metadata type library relative to ourDir. Metadata type library file is file, where all the type information is stored.
This option has default value `metadata.typelib.js`, which will generate file of given name in the root of the outDir.

### metadata.encode
This option allows you to enable/disable base32768 UTF-16 encoding, which will reduce size of the generated metadata type library by about 75&nbsp;%.
Encoded metadata are not human readable. 
This option is enabled by default and it is recommended to keep it enabled for production. 

It's recommended to disable this feature for debugging; allowing you to check generated metadata and create an issue in case you find a bug.

### plugins
List of plugins (path or package name). Allows you to hook up into the transpilation process, do some tweak, change metadata and so on.

### devMode
Used to enable developer mode. Developer mode adds extra output to console and to metadata type library.

### logLevel
Level of logging.

Available levels are:
* None
* Trace
* Debug
* Info
* Warning
* Error

## Config Declaration

```typescript
{
	/**
	 * Optional section which tells transformer how to generate metadata.
	 */
	metadata: {
		/**
		 * List of glob patterns matching modules which should be included in metadata.
		 */
		include: string[];

		/**
		 * List of glob patterns matching modules which should be excluded from metadata.
		 */
		exclude: string[];

		/**
		 * Path (fileName) of metadata type library relative to ourDir.
		 * @default "metadata.typelib.js"
		 */
		metadataTypelibPath: string;

		/**
		 * Path (fileName) of metadata index file relative to ourDir.
		 * @default "metadata.index.json"
		 */
		metadataIndexPath: string;

		/**
		 * Enable metadata encoding.
		 * Currently, the base32768 UTF-16 encoding will be used.
		 */
		encode: "true" | "false"| boolean;
	};

	/**
	 * How to resolve dependencies.
	 */
	dependencyResolution: "direct-dependencies" | "all";

	/**
	 * List of plugins.
	 * @description It is an array of paths and/or package names.
	 */
	plugins: string[];

	/**
	 * Enable or disable DEBUG mode (progress logging and extra warnings).
	 * @default false
	 */
	devMode: "true" | "false"| boolean;

	/**
	 * Level of logging.
	 */
	logLevel: "None" | "Trace" | "Debug" | "Info" | "Warning" | "Error"
}
```