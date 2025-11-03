# HAML Enhanced

Enhanced HAML syntax highlighting for Visual Studio Code with proper multi-line hash support.

## Features

- **Multi-line Hash Support**: Properly highlights hash keys, values, and symbols across multiple indented lines
- **Ruby Embedded Code**: Full syntax highlighting for embedded Ruby expressions
- **HAML Tags**: Complete support for HAML tags, classes, and IDs
- **Ruby Variables & Symbols**: Proper highlighting of variables, symbols, and constants
- **Block Parameters**: Highlights block parameters and pipes
- **Filters**: Syntax highlighting for Ruby filters
- **String Interpolation**: Proper highlighting of `#{}` interpolations

## Screenshots

### Before (Standard HAML Extension)
![Before - No highlighting in multiline hashes](images/before.png)
*Other extensions treat continuation lines as plain text*

### After (HAML Enhanced)
![After - Full syntax highlighting](images/after.png)
*HAML Enhanced properly highlights all elements*

## Why HAML Enhanced?

The standard HAML extensions in VS Code have limited support for multi-line hash syntax. When you write HAML code like this:

```haml
.zen-mobile-table-wrapper{
  class: local_assigns[:class],
  data: { controller: "tabbed-table", "tabbed-table-active-tab-value": local_assigns[:active_tab] }
}
```

Other extensions treat the continuation lines as plain text. HAML Enhanced properly recognizes and highlights:
- Hash keys (`class:`, `data:`)
- Symbols (`:class`, `:active_tab`)
- Variables (`local_assigns`, `tab_key`)
- Strings and their contents
- Nested hashes and arrays
- Block parameters (`|user|`, `|tab, index|`)

## Installation

### From VS Code Marketplace
1. Open VS Code
2. Go to Extensions (`Cmd+Shift+X` / `Ctrl+Shift+X`)
3. Search for "HAML Enhanced"
4. Click Install

Or install directly from the [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=EdColen.haml-enhanced)

### From VSIX (Alternative)
1. Download the `.vsix` file from [GitHub Releases](https://github.com/edcolen/haml-enhanced/releases)
2. Open VS Code
3. Go to Extensions (`Cmd+Shift+X` / `Ctrl+Shift+X`)
4. Click the "..." menu at the top
5. Select "Install from VSIX..."
6. Choose the downloaded file

## Usage

Once installed, the extension automatically activates for all `.haml` files.

## Development

To work on this extension:

```bash
# Install dependencies
npm install

# Open in VS Code
code .

# Press F5 to open Extension Development Host
```

## Known Limitations

- This extension provides syntax highlighting only
- For Ruby code completion, use a Ruby language extension alongside this one

## Contributing

Issues and pull requests are welcome!

## License

MIT

## Author

Ed Colen

