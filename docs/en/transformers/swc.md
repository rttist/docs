<script>
setPagination(
    "/en/getting-started/installation",
    "/en/getting-started/setup"
);
</script>

# SWC

Install SWC plugin:

```bash
npm install swc-plugin-rttist -D
# or
pnpm add swc-plugin-rttist -D
# or
yarn add swc-plugin-rttist -D
```

Add the plugin to your SWC configuration:

```json
{
	"jsc": {
		"experimental": {
			"plugins": [
				[
					"swc-plugin-rttist",
					{
						"name": "@demo", // Your project/package name
						"rootDir": "src" // TS rootDir
					}
				]
			]
		}
	}
}
```

## Demo

Preparing...