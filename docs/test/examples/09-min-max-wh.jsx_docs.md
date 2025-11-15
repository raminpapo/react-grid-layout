# Documentation: test/examples/09-min-max-wh.jsx

## File Metadata

- **Path**: `test/examples/09-min-max-wh.jsx`
- **Type**: .jsx
- **Size**: 1725 bytes (1.68 KB)
- **Lines**: 70
- **Last Modified**: 2025-11-15T20:36:35.105367

## Source Code

```jsx
import React from "react";
import _ from "lodash";
import RGL, { WidthProvider } from "react-grid-layout";

const ReactGridLayout = WidthProvider(RGL);

export default class MinMaxLayout extends React.PureComponent {
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
      const mins = [l.minW, l.minH],
        maxes = [l.maxW, l.maxH];
      return (
        <div key={l.i} data-grid={l}>
          <span className="text">{l.i}</span>
          <div className="minMax">{"min:" + mins + " - max:" + maxes}</div>
        </div>
      );
    });
  }

  generateLayout() {
    const p = this.props;
    return _.map(new Array(p.items), function(item, i) {
      const minW = _.random(1, 6),
        minH = _.random(1, 6);
      const maxW = _.random(minW, 6),
        maxH = _.random(minH, 6);
      const w = _.random(minW, maxW);
      const y = _.random(minH, maxH);
      return {
        x: (i * 2) % 12,
        y: Math.floor(i / 6) * y,
        w,
        h: y,
        i: i.toString(),
        minW,
        maxW,
        minH,
        maxH
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
  import("../test-hook.jsx").then(fn => fn.default(MinMaxLayout));
}

```

## High-Level Overview

This JavaScript/TypeScript file (`09-min-max-wh.jsx`) defines 1 class(es): MinMaxLayout. The file exports: MinMaxLayout.

## Detailed Analysis

### Structure

**Classes** (1): MinMaxLayout



### Components and Functions

#### Classes

**`MinMaxLayout`**: Class defined in this file.



### Dependencies

This file imports from:

- `react`
- `lodash`
- `react-grid-layout`


## Usage Examples

To use this component:

```javascript
import { MinMaxLayout } from './test/examples/09-min-max-wh.jsx';

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
*Documentation generated on 2025-11-15T20:39:40.825742Z*
