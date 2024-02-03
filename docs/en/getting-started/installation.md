<script>
setPagination(
    undefined,
    "/en/getting-started/setup"
);
</script>

# Installation

## Metadata Generator - TypeGen

> Still under development. Published with `@proto` tag.

To generate a metadata, you need to install the TypeGen tool.

```bash
npm install -g @rttist/typegen@proto
# or
pnpm add -g @rttist/typegen@proto
# or
yarn global add @rttist/typegen@proto
```

> TypeGen is a standalone noninvasive command-line tool.
> It does not depend on your project setup; it is completely decoupled from your build/bundle tool.


## Runtime Library

To use the metadata in your application, you need to install the RTTIST runtime library.

```bash
npm install rttist@beta
# or
pnpm add rttist@beta
# or
yarn add rttist@beta
```

<h2>Transformers (Extended Functionality) <sub><small>optional</small></sub></h2>
Based on your stack, pick one of these options to continue.

- [esbuild](/en/transformers/esbuild.md)
- [Vite](/en/transformers/vite.md)
- [SWC](/en/transformers/swc.md)
- [TypeScript](/en/transformers/vanilla-ts.md)
- [Webpack](/en/transformers/webpack.md)
- [Angular](/en/transformers/angular.md)
- [Parcel](/en/transformers/parcel.md)
- [Rollup](/en/transformers/rollup.md)
- [ts-node](/en/transformers/ts-node.md)
- [Deno](/en/transformers/deno.md)

then continue by [Setup](/en/getting-started/setup.md).
