---
created: 2024-01-24 02:14:10Z
---

# Points of Interest
- No multi-threading support

# Basics
## Built-In
### Primitives
#### Variables
- `var` variable (optionally initialized)
- `let` block-scoped, variable
- `const` block-scoped, read-only

#### Data Types

- `number`
- `string`
- `boolean`
- `object`
- `function`
    - Special (Cannot contain Values)
    - `null`
    - `undefined`

#### Objects
- `Object`
- `Date`
- `Array`
- `Boolean`
- `String`
- `Number`

### Operators
- `typeof <variable>`

#### import
```js
import defaultExport from "module-name";
import * as name from "module-name";
import { export1 } from "module-name";
import { export1 as alias1 } from "module-name";
import { default as alias } from "module-name";
import { export1, export2 } from "module-name";
import { export1, export2 as alias2, /* … */ } from "module-name";
import { "string name" as alias } from "module-name";
import defaultExport, { export1, /* … */ } from "module-name";
import defaultExport, * as name from "module-name";
import "module-name";

```

# Functions
- arrow versus normal definitions


# Global Execution environment
- default outer-most scope
- a **realm** provides a JavaScript program with its own single **global execution environment**
## Declarative Environment
- `const`
- `let`
- `class`
- `module`
- `import`
- `function`
## Object Environment
- `var`
- `function`
- `async function`
- `function*`
- `async function*`
	- the `*` represents generator function
- Built-ins through its base object, the `gloabl object`
### Built-In Global Objects
- Non-platform based intrinsic objects
	- values
		- `undefined`
		- `Infinity`
	- functions
		- `eval`
		- `parseInt`
	- constructors
		- `Boolean`
		- `Date`
	- others
		- `JSON`
		- `Math`
- APIs
	- Platform specific s.a. in browsers
		- `fetch`
		- `alert`
		- `document`
		- `DOM`
- referenced as
	- `window` for browsers
	- `global` for NodeJS
	- `globalThis` for both

```javascript
// `const` declrations fall under the "declarative environment"
const constant = 1;

// and therefore they are not accessible via the global object
console.log(window.constant); // undefined

// however,

// `var` declrations fall under the "object environment"
var variable = 2;

// and therefore they are accessible via the global object
console.log(window.variable); // 2
```

# Agents
- Evrery **realm** lives insides an **agent**, which can parent multiple **realms**
- An entity which provides resources to the realms it hosts s.a. the `event loop`