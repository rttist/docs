# Setup
After [Installation](/en/getting-started/installation.md) you just have to import `rttist`; 
ideally as first import in your main module. This first import loads the generated metadata.


```typescript
import "rttist";
import { Employee } from "./entities/Employee"
// ...

const type: Type = Reflect.getType<Employee>();
// ...
```

or

```typescript
import "rttist";
import { Employee } from "./entities/Employee"
// ...

const type: Type = Rttist.getType<Employee>();
// ...
```

or

```typescript
import { getType } from "rttist";
import { Employee } from "./entities/Employee"
// ...

const type: Type = getType<Employee>();
// ...
```