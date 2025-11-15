# Documentation: test/examples/08-localstorage-responsive.jsx

## File Metadata

- **Path**: `test/examples/08-localstorage-responsive.jsx`
- **Type**: .jsx
- **Size**: 2546 bytes (2.49 KB)
- **Lines**: 97
- **Last Modified**: 2025-11-15T20:36:35.105367

## Source Code

```jsx
import React from "react";
import { WidthProvider, Responsive } from "react-grid-layout";

const ResponsiveReactGridLayout = WidthProvider(Responsive);
const originalLayouts = getFromLS("layouts") || {};

/**
 * This layout demonstrates how to sync multiple responsive layouts to localstorage.
 */
export default class ResponsiveLocalStorageLayout extends React.PureComponent {
  constructor(props) {
    super(props);

    this.state = {
      layouts: JSON.parse(JSON.stringify(originalLayouts))
    };
  }

  static get defaultProps() {
    return {
      className: "layout",
      cols: { lg: 12, md: 10, sm: 6, xs: 4, xxs: 2 },
      rowHeight: 30
    };
  }

  resetLayout() {
    this.setState({ layouts: {} });
  }

  onLayoutChange(layout, layouts) {
    saveToLS("layouts", layouts);
    this.setState({ layouts });
  }

  render() {
    return (
      <div>
        <button onClick={() => this.resetLayout()}>Reset Layout</button>
        <ResponsiveReactGridLayout
          className="layout"
          cols={{ lg: 12, md: 10, sm: 6, xs: 4, xxs: 2 }}
          rowHeight={30}
          layouts={this.state.layouts}
          onLayoutChange={(layout, layouts) =>
            this.onLayoutChange(layout, layouts)
          }
        >
          <div key="1" data-grid={{ w: 2, h: 3, x: 0, y: 0, minW: 2, minH: 3 }}>
            <span className="text">1</span>
          </div>
          <div key="2" data-grid={{ w: 2, h: 3, x: 2, y: 0, minW: 2, minH: 3 }}>
            <span className="text">2</span>
          </div>
          <div key="3" data-grid={{ w: 2, h: 3, x: 4, y: 0, minW: 2, minH: 3 }}>
            <span className="text">3</span>
          </div>
          <div key="4" data-grid={{ w: 2, h: 3, x: 6, y: 0, minW: 2, minH: 3 }}>
            <span className="text">4</span>
          </div>
          <div key="5" data-grid={{ w: 2, h: 3, x: 8, y: 0, minW: 2, minH: 3 }}>
            <span className="text">5</span>
          </div>
        </ResponsiveReactGridLayout>
      </div>
    );
  }
}

function getFromLS(key) {
  let ls = {};
  if (global.localStorage) {
    try {
      ls = JSON.parse(global.localStorage.getItem("rgl-8")) || {};
    } catch (e) {
      /*Ignore*/
    }
  }
  return ls[key];
}

function saveToLS(key, value) {
  if (global.localStorage) {
    global.localStorage.setItem(
      "rgl-8",
      JSON.stringify({
        [key]: value
      })
    );
  }
}

if (process.env.STATIC_EXAMPLES === true) {
  import("../test-hook.jsx").then(fn =>
    fn.default(ResponsiveLocalStorageLayout)
  );
}

```

## High-Level Overview

This JavaScript/TypeScript file (`08-localstorage-responsive.jsx`) defines 1 class(es): ResponsiveLocalStorageLayout. It contains 2 function(s). The file exports: ResponsiveLocalStorageLayout.

## Detailed Analysis

### Structure

**Classes** (1): ResponsiveLocalStorageLayout

**Functions** (2): getFromLS, saveToLS



### Components and Functions

#### Functions

**`getFromLS()`**

Function defined in this file.

**`saveToLS()`**

Function defined in this file.

#### Classes

**`ResponsiveLocalStorageLayout`**: Class defined in this file.



### Dependencies

This file imports from:

- `react`
- `react-grid-layout`


## Usage Examples

To use this component:

```javascript
import { ResponsiveLocalStorageLayout } from './test/examples/08-localstorage-responsive.jsx';

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
*Documentation generated on 2025-11-15T20:39:40.809533Z*
