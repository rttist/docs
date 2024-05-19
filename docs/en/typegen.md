# TypeGen
TypeGen is a standalone cmd tool that generates metadata type library for static usage, and it is powered by TypeScript compiler API. When you generate metadata, you can simply import the metadata and use it in your project without any additional dependencies.

## CLI

```bash
Usage: typegen [options] [command]

RTTIST typelib generator

Options:
  -v, --version         Output the version number.
  -p, --project <path>  Path to project root directory where the reflect config and the tsconfig.json files are. Path can be absolute or relative to cwd. (default: ".")
  -h, --help            Display help for command.

Commands:
  generate [options]    Generate typelib, a metadata library containing metadata about types and modules in your project.
  init                  Create config file with recommended options and add reflection section to package.json.
```

### `typegen init`
Initializes the RTTIST inside a project.

```bash
typegen init
```

This command will create a `reflect.config.json` file and add a `reflection` section to the `package.json` file (optional).

### `typegen generate`

Generates a typelib, a metadata library containing metadata about types and modules in your project.

```bash
typegen generate
```

This command will generate a `metadata.typelib.ts` file in the project root directory. This file now becomes part of the project and should be committed to the repository.
`metadata.typelib.ts` imports other generated files that contain metadata for each module in the project. These files should be marked as external and should not be committed to the repository.

## Using Generated Metadata

See [Static Metadata](/en/usage/static-metadata.md?id=static-metadata) section for more information.