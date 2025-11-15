# Documentation: test/examples/11-no-vertical-compact.jsx

## File Metadata

- **Path**: `test/examples/11-no-vertical-compact.jsx`
- **Type**: .jsx
- **Size**: 1509 bytes (1.47 KB)
- **Lines**: 68
- **Last Modified**: 2025-11-15T20:36:35.105367

## Source Code

```jsx
import React from "react";
import _ from "lodash";
import RGL, { WidthProvider } from "react-grid-layout";

const ReactGridLayout = WidthProvider(RGL);

export default class NoCompactingLayout extends React.PureComponent {
  static defaultProps = {
    className: "layout",
    items: 50,
    cols: 12,
    rowHeight: 30,
    onLayoutChange: function() {},
    // This turns off compaction so you can place items wherever.
    verticalCompact: false
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
      const y = _.result(p, "y") || Math.ceil(Math.random() * 4) + 1;
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
        {...this.props}
      >
        {this.generateDOM()}
      </ReactGridLayout>
    );
  }
}

if (process.env.STATIC_EXAMPLES === true) {
  import("../test-hook.jsx").then(fn => fn.default(NoCompactingLayout));
}

```

## High-Level Overview

This JavaScript/TypeScript file (`11-no-vertical-compact.jsx`) defines 1 class(es): NoCompactingLayout. The file exports: NoCompactingLayout.

## Detailed Analysis

### Structure

**Classes** (1): NoCompactingLayout



### Components and Functions

#### Classes

**`NoCompactingLayout`**: Class defined in this file.



### Dependencies

This file imports from:

- `react`
- `lodash`
- `react-grid-layout`


## Usage Examples

To use this component:

```javascript
import { NoCompactingLayout } from './test/examples/11-no-vertical-compact.jsx';

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
*Documentation generated on 2025-11-15T20:39:40.816732Z*
