# Documentation: examples/util/example-styles.css

## File Metadata

- **Path**: `examples/util/example-styles.css`
- **Type**: .css
- **Size**: 1620 bytes (1.58 KB)
- **Lines**: 100
- **Last Modified**: 2025-11-15T20:36:35.080367

## Source Code

```css
body {
  padding: 20px;
}
#content {
  width: 100%;
}
.react-grid-layout {
  background: #eee;
  margin-top: 10px;
}
.layoutJSON {
  background: #ddd;
  border: 1px solid black;
  margin-top: 10px;
  padding: 10px;
}
.columns {
  -moz-columns: 120px;
  -webkit-columns: 120px;
  columns: 120px;
}
.react-grid-item {
  box-sizing: border-box;
}
.react-grid-item:not(.react-grid-placeholder) {
  background: #ccc;
  border: 1px solid black;
}
.react-grid-item.resizing {
  opacity: 0.9;
}
.react-grid-item.static {
  background: #cce;
}
.react-grid-item .text {
  font-size: 24px;
  text-align: center;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
  height: 24px;
}
.react-grid-item .minMax {
  font-size: 12px;
}
.react-grid-item .add {
  cursor: pointer;
}
.react-grid-dragHandleExample {
  cursor: move; /* fallback if grab cursor is unsupported */
  cursor: grab;
  cursor: -moz-grab;
  cursor: -webkit-grab;
}

.toolbox {
  background-color: #dfd;
  width: 100%;
  height: 120px;
  overflow: scroll;
}

.hide-button {
  cursor: pointer;
  position: absolute;
  font-size: 20px;
  top: 0px;
  right: 5px;
}

.toolbox__title {
  font-size: 24px;
  margin-bottom: 5px;
}
.toolbox__items {
  display: block;
}
.toolbox__items__item {
  display: inline-block;
  text-align: center;
  line-height: 40px;
  cursor: pointer;
  width: 40px;
  height: 40px;
  padding: 10px;
  margin: 5px;
  border: 1px solid black;
  background-color: #ddd;
}
.droppable-element {
  width: 150px;
  text-align: center;
  background: #fdd;
  border: 1px solid black;
  margin: 10px 0;
  padding: 10px;
}

```

## High-Level Overview

This is a stylesheet (example-styles.css) defining visual styles.

## Detailed Analysis

### Structure

Structure analysis not applicable for this file type.

### Components and Functions

Component analysis not applicable for this file type.

### Dependencies

No external dependencies detected.

## Usage Examples

Refer to other files in the repository for usage examples.

## Related Files

Related files can be found by examining:

- Files in the same directory: `examples/util/`


## Notes

- **Performance**: No specific performance concerns
- **Security**: Review for potential vulnerabilities if handling user input
- **Maintainability**: Manageable file size

---
*Documentation generated on 2025-11-15T20:39:40.720438Z*
