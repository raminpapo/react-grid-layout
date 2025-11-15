# Documentation: test/examples/10-dynamic-min-max-wh.jsx

## File Metadata

- **Path**: `test/examples/10-dynamic-min-max-wh.jsx`
- **Type**: .jsx
- **Size**: 2082 bytes (2.03 KB)
- **Lines**: 84
- **Last Modified**: 2025-11-15T20:36:35.105367

## Source Code

```jsx
import React from "react";
import _ from "lodash";
import RGL, { WidthProvider } from "react-grid-layout";

const ReactGridLayout = WidthProvider(RGL);

/**
 * This layout demonstrates how to use the `onResize` handler to enforce a min/max width and height.
 *
 * In this grid, all elements are allowed a max width of 2 if the height < 3,
 * and a min width of 2 if the height >= 3.
 */
export default class DynamicMinMaxLayout extends React.PureComponent {
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
    return _.map(layout, function(l) {
      return (
        <div key={l.i} data-grid={l}>
          <span className="text">{l.i}</span>
        </div>
      );
    });
  }

  generateLayout() {
    const p = this.props;
    return _.map(new Array(p.items), function(item, i) {
      const w = _.random(1, 2);
      const h = _.random(1, 3);
      return {
        x: (i * 2) % 12,
        y: Math.floor(i / 6),
        w: w,
        h: h,
        i: i.toString()
      };
    });
  }

  onLayoutChange(layout) {
    this.props.onLayoutChange(layout);
  }

  onResize(layout, oldLayoutItem, layoutItem, placeholder) {
    // `oldLayoutItem` contains the state of the item before the resize.
    // You can modify `layoutItem` to enforce constraints.

    if (layoutItem.h < 3 && layoutItem.w > 2) {
      layoutItem.w = 2;
      placeholder.w = 2;
    }

    if (layoutItem.h >= 3 && layoutItem.w < 2) {
      layoutItem.w = 2;
      placeholder.w = 2;
    }
  }

  render() {
    return (
      <ReactGridLayout
        onLayoutChange={this.onLayoutChange}
        onResize={this.onResize}
        {...this.props}
      >
        {this.generateDOM()}
      </ReactGridLayout>
    );
  }
}

if (process.env.STATIC_EXAMPLES === true) {
  import("../test-hook.jsx").then(fn => fn.default(DynamicMinMaxLayout));
}

```

## High-Level Overview

This JavaScript/TypeScript file (`10-dynamic-min-max-wh.jsx`) defines 1 class(es): DynamicMinMaxLayout. The file exports: DynamicMinMaxLayout.

## Detailed Analysis

### Structure

**Classes** (1): DynamicMinMaxLayout



### Components and Functions

#### Classes

**`DynamicMinMaxLayout`**: Class defined in this file.



### Dependencies

This file imports from:

- `react`
- `lodash`
- `react-grid-layout`


## Usage Examples

To use this component:

```javascript
import { DynamicMinMaxLayout } from './test/examples/10-dynamic-min-max-wh.jsx';

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
*Documentation generated on 2025-11-15T20:39:40.842897Z*
