# Documentation: test/examples/03-messy.jsx

## File Metadata

- **Path**: `test/examples/03-messy.jsx`
- **Type**: .jsx
- **Size**: 1830 bytes (1.79 KB)
- **Lines**: 80
- **Last Modified**: 2025-11-15T20:36:35.104367

## Source Code

```jsx
// @flow
import * as React from "react";
import _ from "lodash";
import RGL from '../../lib/ReactGridLayout';
import WidthProvider from '../../lib/components/WidthProvider';
import type {Layout, ReactChildren} from '../../lib/utils';

const ReactGridLayout = WidthProvider(RGL);

type Props = {|
  className: string,
  cols: number,
  items: number,
  onLayoutChange: Function,
  rowHeight: number,
|};
type State = {|
  layout: Layout
|};

export default class MessyLayout extends React.PureComponent<Props, State> {
  static defaultProps: Props = {
    className: "layout",
    cols: 12,
    items: 20,
    onLayoutChange: function() {},
    rowHeight: 30,
  };

  state: State = {
    layout: this.generateLayout()
  };

  generateDOM(): ReactChildren {
    return _.map(_.range(this.props.items), function(i) {
      return (
        <div key={i}>
          <span className="text">{i}</span>
        </div>
      );
    });
  }

  generateLayout(): Layout {
    const p = this.props;
    return _.map(new Array(p.items), function(item, i) {
      const w = Math.ceil(Math.random() * 4);
      const y = Math.ceil(Math.random() * 4) + 1;
      return {
        x: (i * 2) % 12,
        y: Math.floor(i / 6) * y,
        w: w,
        h: y,
        i: i.toString()
      };
    });
  }

  onLayoutChange: (Layout) => void = (layout: Layout) => {
    this.props.onLayoutChange(layout);
  };

  render(): React.Node {
    // eslint-disable-next-line no-unused-vars
    const {items, ...props} = this.props;
    return (
      <ReactGridLayout
        layout={this.state.layout}
        onLayoutChange={this.onLayoutChange}
        {...props}
      >
        {this.generateDOM()}
      </ReactGridLayout>
    );
  }
}

if (process.env.STATIC_EXAMPLES === true) {
  import("../test-hook.jsx").then(fn => fn.default(MessyLayout));
}

```

## High-Level Overview

This JavaScript/TypeScript file (`03-messy.jsx`) defines 1 class(es): MessyLayout. The file exports: MessyLayout.

## Detailed Analysis

### Structure

**Classes** (1): MessyLayout



### Components and Functions

#### Classes

**`MessyLayout`**: Class defined in this file.



### Dependencies

This file imports from:

- `react`
- `lodash`
- `../../lib/ReactGridLayout`
- `../../lib/components/WidthProvider`
- `../../lib/utils`


## Usage Examples

To use this component:

```javascript
import { MessyLayout } from './test/examples/03-messy.jsx';

// Use the exported components/functions
```


## Related Files

Related files can be found by examining:

- Files in the same directory: `test/examples/`
- Direct dependencies: 5 imports


## Notes

- **Performance**: Standard JavaScript file - ensure proper bundling and minification
- **Security**: Review for potential vulnerabilities if handling user input
- **Maintainability**: Manageable file size

---
*Documentation generated on 2025-11-15T20:39:40.801067Z*
