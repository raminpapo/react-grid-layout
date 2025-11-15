# Documentation: test/examples/00-showcase.jsx

## File Metadata

- **Path**: `test/examples/00-showcase.jsx`
- **Type**: .jsx
- **Size**: 4723 bytes (4.61 KB)
- **Lines**: 159
- **Last Modified**: 2025-11-15T20:36:35.103367

## Source Code

```jsx
// @flow
import * as React from "react";
import _ from "lodash";
import Responsive from '../../lib/ResponsiveReactGridLayout';
import WidthProvider from '../../lib/components/WidthProvider';
import type {CompactType, Layout, LayoutItem, ReactChildren} from '../../lib/utils';
import type {Breakpoint, OnLayoutChangeCallback} from '../../lib/responsiveUtils';
const ResponsiveReactGridLayout = WidthProvider(Responsive);

type Props = {|
  className: string,
  cols: {[string]: number},
  onLayoutChange: Function,
  rowHeight: number,
|};
type State = {|
  currentBreakpoint: string,
  compactType: CompactType,
  mounted: boolean,
  resizeHandles: string[],
  layouts: {[string]: Layout}
|};

const availableHandles = ["s", "w", "e", "n", "sw", "nw", "se", "ne"];

export default class ShowcaseLayout extends React.Component<Props, State> {
  static defaultProps: Props = {
    className: "layout",
    rowHeight: 30,
    onLayoutChange: function() {},
    cols: { lg: 12, md: 10, sm: 6, xs: 4, xxs: 2 },
  };

  state: State = {
    currentBreakpoint: "lg",
    compactType: "vertical",
    resizeHandles: ['se'],
    mounted: false,
    layouts: { lg: generateLayout(['se']) }
  };

  componentDidMount() {
    this.setState({ mounted: true });
  }

  generateDOM(): ReactChildren {
    return _.map(this.state.layouts.lg, function(l, i) {
      return (
        <div key={i} className={l.static ? "static" : ""}>
          {l.static ? (
            <span
              className="text"
              title="This item is static and cannot be removed or resized."
            >
              Static - {i}
            </span>
          ) : (
            <span className="text">{i}</span>
          )}
        </div>
      );
    });
  }

  onBreakpointChange: (Breakpoint) => void = (breakpoint) => {
    this.setState({
      currentBreakpoint: breakpoint
    });
  };

  onCompactTypeChange: () => void = () => {
    const { compactType: oldCompactType } = this.state;
    const compactType =
      oldCompactType === "horizontal"
        ? "vertical"
        : oldCompactType === "vertical"
        ? null
        : "horizontal";
    this.setState({ compactType });
  };

  onResizeTypeChange: () => void = () => {
    const resizeHandles = this.state.resizeHandles === availableHandles ? ['se'] : availableHandles;
    this.setState({resizeHandles, layouts: {lg: generateLayout(resizeHandles)}});
  };


  onLayoutChange: OnLayoutChangeCallback = (layout, layouts) => {
    this.props.onLayoutChange(layout, layouts);
  };

  onNewLayout: EventHandler = () => {
    this.setState({
      layouts: { lg: generateLayout(this.state.resizeHandles) }
    });
  };

  onDrop: (layout: Layout, item: ?LayoutItem, e: Event) => void = (elemParams) => {
    alert(`Element parameters: ${JSON.stringify(elemParams)}`);
  };

  render(): React.Node {
    // eslint-disable-next-line no-unused-vars
    return (
      <div>
        <div>
          Current Breakpoint: {this.state.currentBreakpoint} (
          {this.props.cols[this.state.currentBreakpoint]} columns)
        </div>
        <div>
          Compaction type:{" "}
          {_.capitalize(this.state.compactType) || "No Compaction"}
        </div>
        <button onClick={this.onNewLayout}>Generate New Layout</button>
        <button onClick={this.onCompactTypeChange}>
          Change Compaction Type
        </button>
        <button onClick={this.onResizeTypeChange}>
          Resize {this.state.resizeHandles === availableHandles ? "One Corner" : "All Corners"}
        </button>
        <ResponsiveReactGridLayout
          {...this.props}
          layouts={this.state.layouts}
          onBreakpointChange={this.onBreakpointChange}
          onLayoutChange={this.onLayoutChange}
          onDrop={this.onDrop}
          // WidthProvider option
          measureBeforeMount={false}
          // I like to have it animate on mount. If you don't, delete `useCSSTransforms` (it's default `true`)
          // and set `measureBeforeMount={true}`.
          useCSSTransforms={this.state.mounted}
          compactType={this.state.compactType}
          preventCollision={!this.state.compactType}
        >
          {this.generateDOM()}
        </ResponsiveReactGridLayout>
      </div>
    );
  }
}

function generateLayout(resizeHandles) {
  return _.map(_.range(0, 25), function(item, i) {
    var y = Math.ceil(Math.random() * 4) + 1;
    return {
      x: Math.round(Math.random() * 5) * 2,
      y: Math.floor(i / 6) * y,
      w: 2,
      h: y,
      i: i.toString(),
      static: Math.random() < 0.05,
      resizeHandles
    };
  });
}

if (process.env.STATIC_EXAMPLES === true) {
  import("../test-hook.jsx").then(fn => fn.default(ShowcaseLayout));
}

```

## High-Level Overview

This JavaScript/TypeScript file (`00-showcase.jsx`) defines 1 class(es): ShowcaseLayout. It contains 1 function(s). The file exports: ShowcaseLayout.

## Detailed Analysis

### Structure

**Classes** (1): ShowcaseLayout

**Functions** (1): generateLayout



### Components and Functions

#### Functions

**`generateLayout()`**

Function defined in this file.

#### Classes

**`ShowcaseLayout`**: Class defined in this file.



### Dependencies

This file imports from:

- `react`
- `lodash`
- `../../lib/ResponsiveReactGridLayout`
- `../../lib/components/WidthProvider`
- `../../lib/utils`
- `../../lib/responsiveUtils`


## Usage Examples

To use this component:

```javascript
import { ShowcaseLayout } from './test/examples/00-showcase.jsx';

// Use the exported components/functions
```


## Related Files

Related files can be found by examining:

- Files in the same directory: `test/examples/`
- Direct dependencies: 6 imports


## Notes

- **Performance**: Standard JavaScript file - ensure proper bundling and minification
- **Security**: Review for potential vulnerabilities if handling user input
- **Maintainability**: Manageable file size

---
*Documentation generated on 2025-11-15T20:39:40.833117Z*
