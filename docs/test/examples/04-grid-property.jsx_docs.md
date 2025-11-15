# Documentation: test/examples/04-grid-property.jsx

## File Metadata

- **Path**: `test/examples/04-grid-property.jsx`
- **Type**: .jsx
- **Size**: 1478 bytes (1.44 KB)
- **Lines**: 59
- **Last Modified**: 2025-11-15T20:36:35.104367

## Source Code

```jsx
import React from "react";
import _ from "lodash";
import RGL, { WidthProvider } from "react-grid-layout";

const ReactGridLayout = WidthProvider(RGL);

export default class GridPropertyLayout extends React.PureComponent {
  static defaultProps = {
    isDraggable: true,
    isResizable: true,
    items: 20,
    rowHeight: 30,
    onLayoutChange: function() {},
    cols: 12
  };

  generateDOM() {
    // Generate items with properties from the layout, rather than pass the layout directly
    const layout = this.generateLayout();
    return _.map(_.range(this.props.items), function(i) {
      return (
        <div key={i} data-grid={layout[i]}>
          <span className="text">{i}</span>
        </div>
      );
    });
  }

  generateLayout() {
    const p = this.props;
    return _.map(new Array(p.items), function(item, i) {
      var w = _.result(p, "w") || Math.ceil(Math.random() * 4);
      var y = _.result(p, "y") || Math.ceil(Math.random() * 4) + 1;
      return {
        x: (i * 2) % 12,
        y: Math.floor(i / 6) * y,
        w: w,
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
      <ReactGridLayout onLayoutChange={this.onLayoutChange} {...this.props}>
        {this.generateDOM()}
      </ReactGridLayout>
    );
  }
}

if (process.env.STATIC_EXAMPLES === true) {
  import("../test-hook.jsx").then(fn => fn.default(GridPropertyLayout));
}

```

## High-Level Overview

This JavaScript/TypeScript file (`04-grid-property.jsx`) defines 1 class(es): GridPropertyLayout. The file exports: GridPropertyLayout.

## Detailed Analysis

### Structure

**Classes** (1): GridPropertyLayout



### Components and Functions

#### Classes

**`GridPropertyLayout`**: Class defined in this file.



### Dependencies

This file imports from:

- `react`
- `lodash`
- `react-grid-layout`


## Usage Examples

To use this component:

```javascript
import { GridPropertyLayout } from './test/examples/04-grid-property.jsx';

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
*Documentation generated on 2025-11-15T20:39:40.841405Z*
