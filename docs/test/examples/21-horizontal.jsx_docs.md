# Documentation: test/examples/21-horizontal.jsx

## File Metadata

- **Path**: `test/examples/21-horizontal.jsx`
- **Type**: .jsx
- **Size**: 1478 bytes (1.44 KB)
- **Lines**: 71
- **Last Modified**: 2025-11-15T20:36:35.107367

## Source Code

```jsx
import React from "react";
import _ from "lodash";
import RGL, { WidthProvider } from "react-grid-layout";

const ReactGridLayout = WidthProvider(RGL);

export default class Horizontal extends React.PureComponent {
  static defaultProps = {
    className: "layout",
    items: 5,
    rowHeight: 5,
    onLayoutChange: function() {},
    cols: 12,
    compactType: "horizontal",
    maxRows: 1,
    allowOverlap: false
  };

  constructor(props) {
    super(props);

    const layout = this.generateLayout();
    this.state = { layout };
  }

  generateDOM() {
    return _.map(_.range(this.props.items), function(i) {
      return (
        <div key={i}>
          <span className="text">{i}</span>
        </div>
      );
    });
  }

  generateLayout() {
    const p = this.props;
    return _.map(new Array(p.items), function(item, i) {
      const y = 5;
      return {
        x: (i * 2) % 12,
        y: Math.floor(i / 6) * y,
        w: 2,
        h: y,
        i: i.toString()
      };
    });
  }

  onLayoutChange(layout) {
    this.props.onLayoutChange(layout);
  }

  render() {
    return (
      <ReactGridLayout
        layout={this.state.layout}
        onLayoutChange={this.onLayoutChange}
        useCSSTransforms={true}
        allowOverlap={true}
        {...this.props}
      >
        {this.generateDOM()}
      </ReactGridLayout>
    );
  }
}

if (process.env.STATIC_EXAMPLES === true) {
  import("../test-hook.jsx").then(fn => fn.default(Horizontal));
}

```

## High-Level Overview

This JavaScript/TypeScript file (`21-horizontal.jsx`) defines 1 class(es): Horizontal. The file exports: Horizontal.

## Detailed Analysis

### Structure

**Classes** (1): Horizontal



### Components and Functions

#### Classes

**`Horizontal`**: Class defined in this file.



### Dependencies

This file imports from:

- `react`
- `lodash`
- `react-grid-layout`


## Usage Examples

To use this component:

```javascript
import { Horizontal } from './test/examples/21-horizontal.jsx';

// Use the exported components/functions
```


## Related Files

Related files can be found by examining:

- Files in the same directory: `test/examples/`
- Direct dependencies: 3 imports


## Notes

- **Performance**: Standard JavaScript file - ensure proper bundling and minification
- **Security**: Review for potential vulnerabilities if handling user input
- **Maintainability**: Manageable file size

---
*Documentation generated on 2025-11-15T20:39:40.830765Z*
