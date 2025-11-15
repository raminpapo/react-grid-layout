# Documentation: lib/responsiveUtils.js

## File Metadata

- **Path**: `lib/responsiveUtils.js`
- **Type**: .js
- **Size**: 3704 bytes (3.62 KB)
- **Lines**: 118
- **Last Modified**: 2025-11-15T20:36:35.100367

## Source Code

```javascript
// @flow

import { cloneLayout, compact, correctBounds } from "./utils";

import type { CompactType, Layout } from "./utils";

export type Breakpoint = string;
export type DefaultBreakpoints = "lg" | "md" | "sm" | "xs" | "xxs";

// + indicates read-only
export type ResponsiveLayout<T: Breakpoint> = {
  +[breakpoint: T]: Layout
};
export type Breakpoints<T: Breakpoint> = {
  +[breakpoint: T]: number
};

export type OnLayoutChangeCallback = (
  Layout,
  { [key: Breakpoint]: Layout }
) => void;

/**
 * Given a width, find the highest breakpoint that matches is valid for it (width > breakpoint).
 *
 * @param  {Object} breakpoints Breakpoints object (e.g. {lg: 1200, md: 960, ...})
 * @param  {Number} width Screen width.
 * @return {String}       Highest breakpoint that is less than width.
 */
export function getBreakpointFromWidth(
  breakpoints: Breakpoints<Breakpoint>,
  width: number
): Breakpoint {
  const sorted = sortBreakpoints(breakpoints);
  let matching = sorted[0];
  for (let i = 1, len = sorted.length; i < len; i++) {
    const breakpointName = sorted[i];
    if (width > breakpoints[breakpointName]) matching = breakpointName;
  }
  return matching;
}

/**
 * Given a breakpoint, get the # of cols set for it.
 * @param  {String} breakpoint Breakpoint name.
 * @param  {Object} cols       Map of breakpoints to cols.
 * @return {Number}            Number of cols.
 */
export function getColsFromBreakpoint(
  breakpoint: Breakpoint,
  cols: Breakpoints<Breakpoint>
): number {
  if (!cols[breakpoint]) {
    throw new Error(
      "ResponsiveReactGridLayout: `cols` entry for breakpoint " +
        breakpoint +
        " is missing!"
    );
  }
  return cols[breakpoint];
}

/**
 * Given existing layouts and a new breakpoint, find or generate a new layout.
 *
 * This finds the layout above the new one and generates from it, if it exists.
 *
 * @param  {Object} layouts     Existing layouts.
 * @param  {Array} breakpoints All breakpoints.
 * @param  {String} breakpoint New breakpoint.
 * @param  {String} breakpoint Last breakpoint (for fallback).
 * @param  {Number} cols       Column count at new breakpoint.
 * @param  {Boolean} verticalCompact Whether or not to compact the layout
 *   vertically.
 * @return {Array}             New layout.
 */
export function findOrGenerateResponsiveLayout(
  layouts: ResponsiveLayout<Breakpoint>,
  breakpoints: Breakpoints<Breakpoint>,
  breakpoint: Breakpoint,
  lastBreakpoint: Breakpoint,
  cols: number,
  compactType: CompactType
): Layout {
  // If it already exists, just return it.
  if (layouts[breakpoint]) return cloneLayout(layouts[breakpoint]);
  // Find or generate the next layout
  let layout = layouts[lastBreakpoint];
  const breakpointsSorted = sortBreakpoints(breakpoints);
  const breakpointsAbove = breakpointsSorted.slice(
    breakpointsSorted.indexOf(breakpoint)
  );
  for (let i = 0, len = breakpointsAbove.length; i < len; i++) {
    const b = breakpointsAbove[i];
    if (layouts[b]) {
      layout = layouts[b];
      break;
    }
  }
  layout = cloneLayout(layout || []); // clone layout so we don't modify existing items
  return compact(correctBounds(layout, { cols: cols }), compactType, cols);
}

/**
 * Given breakpoints, return an array of breakpoints sorted by width. This is usually
 * e.g. ['xxs', 'xs', 'sm', ...]
 *
 * @param  {Object} breakpoints Key/value pair of breakpoint names to widths.
 * @return {Array}              Sorted breakpoints.
 */
export function sortBreakpoints(
  breakpoints: Breakpoints<Breakpoint>
): Array<Breakpoint> {
  const keys: Array<string> = Object.keys(breakpoints);
  return keys.sort(function (a, b) {
    return breakpoints[a] - breakpoints[b];
  });
}

```

## High-Level Overview

This JavaScript/TypeScript file (`responsiveUtils.js`) It contains 4 function(s). The file exports: type, type, type, type, type, getBreakpointFromWidth, getColsFromBreakpoint, findOrGenerateResponsiveLayout, sortBreakpoints.

## Detailed Analysis

### Structure

**Functions** (4): getBreakpointFromWidth, getColsFromBreakpoint, findOrGenerateResponsiveLayout, sortBreakpoints



### Components and Functions

#### Functions

**`getBreakpointFromWidth()`**

Documentation: * Given a width, find the highest breakpoint that matches is valid for it (width > breakpoint).
 *
 * @param  {Object} breakpoints Breakpoints object (e.g. {lg: 1200, md: 960, ...})
 * @param  {Number} width Screen width.
 * @return {String}       Highest breakpoint that is less than width.

**`getColsFromBreakpoint()`**

Documentation: * Given a width, find the highest breakpoint that matches is valid for it (width > breakpoint).
 *
 * @param  {Object} breakpoints Breakpoints object (e.g. {lg: 1200, md: 960, ...})
 * @param  {Number} width Screen width.
 * @return {String}       Highest breakpoint that is less than width.

**`findOrGenerateResponsiveLayout()`**

Documentation: * Given a width, find the highest breakpoint that matches is valid for it (width > breakpoint).
 *
 * @param  {Object} breakpoints Breakpoints object (e.g. {lg: 1200, md: 960, ...})
 * @param  {Number} width Screen width.
 * @return {String}       Highest breakpoint that is less than width.

**`sortBreakpoints()`**

Documentation: * Given a width, find the highest breakpoint that matches is valid for it (width > breakpoint).
 *
 * @param  {Object} breakpoints Breakpoints object (e.g. {lg: 1200, md: 960, ...})
 * @param  {Number} width Screen width.
 * @return {String}       Highest breakpoint that is less than width.



### Dependencies

This file imports from:

- `./utils`
- `./utils`


## Usage Examples

To use this module:

```javascript
import { type, type, type } from './lib/responsiveUtils.js';
```


## Related Files

Related files can be found by examining:

- Files in the same directory: `lib/`
- Direct dependencies: 2 imports


## Notes

- **Performance**: Standard JavaScript file - ensure proper bundling and minification
- **Security**: Review for potential vulnerabilities if handling user input
- **Maintainability**: Manageable file size

---
*Documentation generated on 2025-11-15T20:39:41.037621Z*
