# Documentation: test/examples/07-localstorage.jsx

## File Metadata

- **Path**: `test/examples/07-localstorage.jsx`
- **Type**: .jsx
- **Size**: 2365 bytes (2.31 KB)
- **Lines**: 96
- **Last Modified**: 2025-11-15T20:36:35.104367

## Source Code

```jsx
import React from "react";
import RGL, { WidthProvider } from "react-grid-layout";

const ReactGridLayout = WidthProvider(RGL);
const originalLayout = getFromLS("layout") || [];
/**
 * This layout demonstrates how to sync to localstorage.
 */
export default class LocalStorageLayout extends React.PureComponent {
  static defaultProps = {
    className: "layout",
    cols: 12,
    rowHeight: 30,
    onLayoutChange: function() {}
  };

  constructor(props) {
    super(props);

    this.state = {
      layout: JSON.parse(JSON.stringify(originalLayout))
    };

    this.onLayoutChange = this.onLayoutChange.bind(this);
    this.resetLayout = this.resetLayout.bind(this);
  }

  resetLayout() {
    this.setState({
      layout: []
    });
  }

  onLayoutChange(layout) {
    /*eslint no-console: 0*/
    saveToLS("layout", layout);
    this.setState({ layout });
    this.props.onLayoutChange(layout); // updates status display
  }

  render() {
    return (
      <div>
        <button onClick={this.resetLayout}>Reset Layout</button>
        <ReactGridLayout
          {...this.props}
          layout={this.state.layout}
          onLayoutChange={this.onLayoutChange}
        >
          <div key="1" data-grid={{ w: 2, h: 3, x: 0, y: 0 }}>
            <span className="text">1</span>
          </div>
          <div key="2" data-grid={{ w: 2, h: 3, x: 2, y: 0 }}>
            <span className="text">2</span>
          </div>
          <div key="3" data-grid={{ w: 2, h: 3, x: 4, y: 0 }}>
            <span className="text">3</span>
          </div>
          <div key="4" data-grid={{ w: 2, h: 3, x: 6, y: 0 }}>
            <span className="text">4</span>
          </div>
          <div key="5" data-grid={{ w: 2, h: 3, x: 8, y: 0 }}>
            <span className="text">5</span>
          </div>
        </ReactGridLayout>
      </div>
    );
  }
}

function getFromLS(key) {
  let ls = {};
  if (global.localStorage) {
    try {
      ls = JSON.parse(global.localStorage.getItem("rgl-7")) || {};
    } catch (e) {
      /*Ignore*/
    }
  }
  return ls[key];
}

function saveToLS(key, value) {
  if (global.localStorage) {
    global.localStorage.setItem(
      "rgl-7",
      JSON.stringify({
        [key]: value
      })
    );
  }
}

if (process.env.STATIC_EXAMPLES === true) {
  import("../test-hook.jsx").then(fn => fn.default(LocalStorageLayout));
}

```

## High-Level Overview

This JavaScript/TypeScript file (`07-localstorage.jsx`) defines 1 class(es): LocalStorageLayout. It contains 2 function(s). The file exports: LocalStorageLayout.

## Detailed Analysis

### Structure

**Classes** (1): LocalStorageLayout

**Functions** (2): getFromLS, saveToLS



### Components and Functions

#### Functions

**`getFromLS()`**

Function defined in this file.

**`saveToLS()`**

Function defined in this file.

#### Classes

**`LocalStorageLayout`**: Class defined in this file.



### Dependencies

This file imports from:

- `react`
- `react-grid-layout`


## Usage Examples

To use this component:

```javascript
import { LocalStorageLayout } from './test/examples/07-localstorage.jsx';

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
*Documentation generated on 2025-11-15T20:39:40.827761Z*
