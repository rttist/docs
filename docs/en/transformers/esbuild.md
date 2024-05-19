<script>
setPagination(
    "/en/getting-started/installation",
    "/en/getting-started/setup"
);
</script>

# esbuild

Install esbuild plugin:

```bash
npm install esbuild-plugin-rttist -D
# or
pnpm add esbuild-plugin-rttist -D
# or
yarn add esbuild-plugin-rttist -D
```

Add the plugin to your esbuild config:

```javascript
const { rttistPlugin } = require('esbuild-plugin-rttist'); // < 1. Import the plugin

const path = require('path');
const esbuild = require('esbuild');
const packageJson = require('./package.json');

esbuild
    .build({
        entryPoints: ['src/index.ts'],
        outfile: 'dist/index.js',
        platform: 'node',
        format: 'cjs',
        target: 'es2022',
        bundle: true,
        external: Object.keys(packageJson.dependencies).concat(
            Object.keys(packageJson.peerDependencies || {})
        ),
        plugins: [
            // < 2. Initialize the plugin
            rttistPlugin({
                // Package/project info used to generate type identifiers
                packageInfo: { name: packageJson.name, rootDir: __dirname },
                // "rootDir" from tsconfig
                tsRootDir: path.join(__dirname, 'src'),
            }),
        ],
    })
    .catch((err) => {
        console.error(err);
    });
```

## Demo
All the examples are available on Stackblitz for a quick preview if not stated otherwise.
- [Logging](https://stackblitz.com/edit/rttist-playground-esbuild-init?file=src%2Findex.ts)