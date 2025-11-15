# Documentation: test/examples/17-responsive-bootstrap-style.jsx

## File Metadata

- **Path**: `test/examples/17-responsive-bootstrap-style.jsx`
- **Type**: .jsx
- **Size**: 1822 bytes (1.78 KB)
- **Lines**: 66
- **Last Modified**: 2025-11-15T20:36:35.107367

## Source Code

```jsx
import React from "react";
import { WidthProvider, Responsive } from "react-grid-layout";

const ResponsiveReactGridLayout = WidthProvider(Responsive);

/**
 * This example illustrates how to let grid items lay themselves out with a bootstrap-style specification.
 */
export default class BootstrapStyleLayout extends React.PureComponent {
  static defaultProps = {
    isDraggable: true,
    isResizable: true,
    items: 20,
    rowHeight: 30,
    onLayoutChange: function() {},
    cols: {lg: 12, md: 12, sm: 12, xs: 12, xxs: 12}
  };

  state = {
    layouts: this.generateLayouts()
  };

  onLayoutChange(layout) {
    this.props.onLayoutChange(layout);
  }

  generateDOM() {
    return [...Array(this.props.items)].map((_, i) => (
      <div key={i}>
        <span className="text">{i}</span>
      </div>
    ));
  }

  // Create responsive layouts. Similar to bootstrap, increase the pseudo width as
  // the viewport shrinks
  generateLayouts() {
    const times = [...Array(this.props.items)];
    const widths = {lg: 3, md: 4, sm: 6, xs: 12, xxs: 12};
    return Object.keys(widths).reduce((memo, breakpoint) => {
      const width = widths[breakpoint];
      const cols = this.props.cols[breakpoint];
      memo[breakpoint] = [
        // You can set y to 0, the collision algo will figure it out.
        ...times.map((_, i) => ({x: (i * width) % cols, y: 0, w: width, h: 4, i: String(i)}))
      ];
      return memo;
    }, {});
  }

  render() {
    return (
      <ResponsiveReactGridLayout
        onLayoutChange={this.onLayoutChange}
        {...this.props}
        layouts={this.state.layouts}
      >
        {this.generateDOM()}
      </ResponsiveReactGridLayout>
    );
  }
}

if (process.env.STATIC_EXAMPLES === true) {
  import("../test-hook.jsx").then(fn => fn.default(BootstrapStyleLayout));
}

```

## High-Level Overview

This JavaScript/TypeScript file (`17-responsive-bootstrap-style.jsx`) defines 1 class(es): BootstrapStyleLayout. The file exports: BootstrapStyleLayout.

## Detailed Analysis

### Structure

**Classes** (1): BootstrapStyleLayout



### Components and Functions

#### Classes

**`BootstrapStyleLayout`**: Class defined in this file.



### Dependencies

This file imports from:

- `react`
- `react-grid-layout`


## Usage Examples

To use this component:

```javascript
import { BootstrapStyleLayout } from './test/examples/17-responsive-bootstrap-style.jsx';

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
*Documentation generated on 2025-11-15T20:39:40.836901Z*
