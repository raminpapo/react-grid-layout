# Documentation: test/examples/test_demo.jsx

## File Metadata

- **Path**: `test/examples/test_demo.jsx`
- **Type**: .jsx
- **Size**: 500 bytes (0.49 KB)
- **Lines**: 25
- **Last Modified**: 2025-11-15T20:36:35.107367

## Source Code

```jsx
import React from 'react';
import RGL, { WidthProvider } from 'react-grid-layout';

const ReactGridLayout = WidthProvider(RGL);


export const IsBounded = ({ onDragStop }) => {

  const layout = [
    { i: '0', x: 0, y: 0, w: 1, h: 1 },
    { i: '1', x: 1, y: 0, w: 1, h: 1 },
  ]

  return (
    <ReactGridLayout
      layout={layout}
      isBounded={true}
      onDragStop={onDragStop}
    >
      {
        layout.map(ele => <div key={ele.i}>{ele.i}</div>)
      }
    </ReactGridLayout>
  );
};

```

## High-Level Overview

This JavaScript/TypeScript file (`test_demo.jsx`) It contains 1 function(s). The file exports: IsBounded.

## Detailed Analysis

### Structure

**Functions** (1): IsBounded



### Components and Functions

#### Functions

**`IsBounded()`**

Function defined in this file.



### Dependencies

This file imports from:

- `react`
- `react-grid-layout`


## Usage Examples

To use this component:

```javascript
import { IsBounded } from './test/examples/test_demo.jsx';

// Use the exported components/functions
```


## Related Files

Related files can be found by examining:

- Files in the same directory: `test/examples/`
- Direct dependencies: 2 imports


## Notes

- **Performance**: Standard JavaScript file - ensure proper bundling and minification
- **Security**: Review for potential vulnerabilities if handling user input
- **Maintainability**: Manageable file size

---
*Documentation generated on 2025-11-15T20:39:40.802789Z*
