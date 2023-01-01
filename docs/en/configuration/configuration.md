# Configuration

## Config file(s)
Config file is optional. By config files, you can change default behavior of metadata and/or transformer.

There are three ways how to configure **RTTIST**.

1. Create file `reflect.config.json`,
    ```json
    {
        "metadata": {
            "encode": true
        },
        "logLevel": "Warning"
    }
    ```
2. or create file `reflect.config.js` with `default` export. Exported value can be config object directly or Promise resolved to config object.
    ```javascript
    module.exports.default = {
        metadata: {
            encode: true
        },
        logLevel: "Warning"
    };
    ```
3. In case you use ttypescript or ts-loader with webpack, you can use tsconfig.json.
    ```json
    {
        "compilerOptions": {
            // Your options...
            "plugins": [
                {
                    "transform": "tst-reflect-transformer",
                    // configuration in "reflection" property
                    "reflection": {
                        "metadata": {
                            "encode": true
                        },
                        "logLevel": "Warning"
                    }
                }
            ]
        }
    }
    ```

## Config Options
### metadata.include
List of glob patterns matching modules which should be included in metadata.

### metadata.exclude
List of glob patterns matching modules which should be excluded from metadata. Overrides `metadata.include`.

### metadata.metadataTypelibPath
Path (fileName) of metadata type library relative to ourDir. Metadata type library file is file, where all the type information is stored.
This option has default value `metadata.typelib.js`, which will generate file of given name in the root of the outDir.

### metadata.encode
This option allows you to enable base32768 UTF-16 encoding, which will reduce size of the generated metadata type library by about 75%.
Encoded metadata are not human readable. 
It's recommended to enable this option for production. 
Disabled by default because of Alpha version; allowing you to check generated metadata and create an issue in case you find a bug.

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