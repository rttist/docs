<script>
setPagination(
    "/en/getting-started/installation",
    "/en/getting-started/setup"
);
</script>

# Vite

Install Vite plugin:

```bash
npm install vite-plugin-rttist -D
# or
pnpm add vite-plugin-rttist -D
# or
yarn add vite-plugin-rttist -D
```

Add the plugin to your esbuild config:

```typescript
import { rttistPlugin } from "vite-plugin-rttist"; // < 1. Import the plugin

import { defineConfig } from "vite";
import { join } from "path";
import solid from "vite-plugin-solid";
import packageJson from "./package.json";

export default defineConfig({
    plugins: [
        // < 2. Initialize the plugin
        rttistPlugin({
            // Package/project info used to generate type identifiers
            packageInfo: { name: packageJson.name, rootDir: __dirname },
            // "rootDir" from tsconfig
            tsRootDir: join(__dirname, "src"),
        }),
        solid(),
    ],
});
```

## Demo
All the examples are available on Stackblitz for a quick preview if not stated otherwise.

Preparing...