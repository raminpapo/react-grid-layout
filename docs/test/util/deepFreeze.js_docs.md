# Documentation: test/util/deepFreeze.js

## File Metadata

- **Path**: `test/util/deepFreeze.js`
- **Type**: .js
- **Size**: 1810 bytes (1.77 KB)
- **Lines**: 54
- **Last Modified**: 2025-11-15T20:36:35.111367

## Source Code

```javascript
// @flow

// Deep freeze an object by using a Proxy.
// This is better than Object.freeze() as we can create coherent error messages
// and easily only deliver frozen subobjects when they are accessed. We can
// even add custom logic, like warning if you access a property that doesn't exist.
/* eslint-disable no-console */
export default function deepFreeze<T: { [key: string]: any }>(
  inputObj: T,
  options: { get: boolean, set: boolean } = { get: true, set: true }
): $ReadOnly<{| ...T |}> {
  // Our handler that rejects any change to the object and any nested objects inside it
  const deepFreezer = {};
  if (options.get) {
    deepFreezer.get = function get(
      obj: T,
      prop: $Keys<T>,
      _receiver: Proxy<T>
    ): any {
      // Clone w/o Proxy
      if (prop === "toJSON") return () => obj;
      // If dealing with nested object, nest the proxy untill it reaches the direct property of it's parent proxy
      if (typeof obj[prop] === "object" && obj[prop] !== null) {
        return new Proxy(obj[prop], deepFreezer);
      }
      // If prop is directly accessible, just do the default operation
      else {
        if (
          !(prop in obj) &&
          prop !== "length" &&
          prop !== "__esModule" &&
          typeof prop !== "symbol"
        ) {
          throw new Error(
            `Can not get unknown prop "${String(prop)}" on frozen object.`
          );
        }
        return obj[prop];
      }
    };
  }
  if (options.set) {
    deepFreezer.set = function set(
      obj: T,
      prop: string,
      _val: any,
      _rec: Proxy<T>
    ): boolean {
      throw new Error(`Can not set unknown prop "${prop}" on frozen object.`);
    };
  }
  // $FlowIgnore for all useful purposes the output type is T here
  return new Proxy(inputObj, deepFreezer);
}

```

## High-Level Overview

This JavaScript/TypeScript file (`deepFreeze.js`) It contains 3 function(s). The file exports: deepFreeze.

## Detailed Analysis

### Structure

**Functions** (3): deepFreeze, get, set



### Components and Functions

#### Functions

**`deepFreeze()`**

Function defined in this file.

**`get()`**

Function defined in this file.

**`set()`**

Function defined in this file.



### Dependencies

No external dependencies detected.

## Usage Examples

To use this module:

```javascript
import { deepFreeze } from './test/util/deepFreeze.js';
```


## Related Files

Related files can be found by examining:

- Files in the same directory: `test/util/`


## Notes

- **Performance**: Standard JavaScript file - ensure proper bundling and minification
- **Security**: Review for potential vulnerabilities if handling user input
- **Maintainability**: Manageable file size

---
*Documentation generated on 2025-11-15T20:39:40.748302Z*
