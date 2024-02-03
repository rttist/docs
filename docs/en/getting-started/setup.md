<script>
setPagination(
    "/en/getting-started/installation",
    "/en/usage/how-to-access-type?id=how-to-get-a-type"
);
</script>

# Setup

Use the installed [TypeGen](/en/typegen.md) cmd tool to initialize the RTTIST inside a project.

```bash
rttist init
# or
typegen init
# or
npx rttist init
# or
pnpm exec rttist init
```

Example output:
```bash
❯ npx rttist init
✓ Config file created.
? Is this project intended to be a library? (It will add a reflection section to package.json) Yes
✓ Package json file patched.
✓ Done
Continue by running:  rttist generate
```

This will create a `reflect.config.json` file and add a `reflection` section to the `package.json` file (optional).

Continue by running the `rttist generate` command.

```bash
rttist generate
```

This will generate a `metadata.typelib.ts` file in the project root directory. 
This file now becomes part of the project and should be committed to the repository.



[//]: # (After [Installation]&#40;/en/getting-started/installation.md&#41; you just have to import `rttist`; )

[//]: # (ideally as first import in your main module. This first import loads the generated metadata.)

[//]: # ()
[//]: # ()
[//]: # (```typescript)

[//]: # (import "rttist";)

[//]: # (import { Employee } from "./entities/Employee")

[//]: # (// ...)

[//]: # ()
[//]: # (const type: Type = Reflect.getType<Employee>&#40;&#41;;)

[//]: # (// ...)

[//]: # (```)

[//]: # ()
[//]: # (or)

[//]: # ()
[//]: # (```typescript)

[//]: # (import "rttist";)

[//]: # (import { Employee } from "./entities/Employee")

[//]: # (// ...)

[//]: # ()
[//]: # (const type: Type = Rttist.getType<Employee>&#40;&#41;;)

[//]: # (// ...)

[//]: # (```)

[//]: # ()
[//]: # (or)

[//]: # ()
[//]: # (```typescript)

[//]: # (import { getType } from "rttist";)

[//]: # (import { Employee } from "./entities/Employee")

[//]: # (// ...)

[//]: # ()
[//]: # (const type: Type = getType<Employee>&#40;&#41;;)

[//]: # (// ...)

[//]: # (```)