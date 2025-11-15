# Documentation: examples/util/template.ejs

## File Metadata

- **Path**: `examples/util/template.ejs`
- **Type**: .ejs
- **Size**: 1342 bytes (1.31 KB)
- **Lines**: 35
- **Last Modified**: 2025-11-15T20:36:35.081367

## Source Code

```
<!--
  <%= banner %>
-->
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <script src="<%= base %>/commons.js"></script>
    <script src="<%= base %>/<%= index %>-<%= source %>.js"></script>
    <style>body { padding: 20px; }</style>
    <title>RGL Example <%= index %> - <%= title %></title>
  </head>
  <body>
    <h3>React-Grid-Layout
      <a href="https://www.npmjs.com/package/react-grid-layout/v/<%= version %>">v<%= version %></a>
      Demo <%= index %> - <%= title %>
    </h3>
    <ul>
      <li><a href="https://github.com/react-grid-layout/react-grid-layout">View project on GitHub</a></li>
      <li><a href="https://github.com/react-grid-layout/react-grid-layout/blob/master/test/examples/<%= index %>-<%= source %>.jsx">View this example's source</a></li>
    <%_ if (previous) { -%>
      <li><a href="<%= previous.index %>-<%= previous.source %>.html"><b>⇠</b> View the previous example: "<%= previous.title %>"</a></li>
    <%_ } else { -%>
      <li><b>⇠</b></li>
    <%_ } -%>
    <%_ if (next) { -%>
      <li><a href="<%= next.index %>-<%= next.source %>.html"><b>⇢ </b>View the next example: "<%= next.title %>"</a></li>
    <%_ } -%>
    </ul>
    <%_ for(var i = 0; i < paragraphs.length; i++) { -%>
       <p><%- paragraphs[i] %></p>
    <%_ } -%>
    <div id="content"></div>
  </body>
</html>

```

## High-Level Overview

This file (template.ejs) is part of the repository structure.

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
*Documentation generated on 2025-11-15T20:39:40.727402Z*
