# Change Log

All notable changes to the "haml-enhanced" extension will be documented in this file.

## [0.1.0] - 2025-11-03

### Added
- Initial release
- **Multi-line hash support** with proper token scopes for all elements
- **Ruby variable highlighting** in all contexts (hash values, method calls, etc.)
- **Symbol highlighting** including symbols inside brackets (`:symbol_value`, `[:key]`)
- **Block parameter highlighting** with pipe delimiters (`|user|`, `|tab, index|`)
- **Ruby code fallback patterns** for full highlighting without external Ruby extension
- **Inline Ruby output** highlighting on tag lines (`%h3= user.name`)
- **HTML-style attributes** with string highlighting (`%img(src="..." alt="...")`)
- Enhanced HAML syntax highlighting for tags, classes, and IDs
- Ruby embedded code highlighting (`#{}` interpolation)
- String interpolation support in all contexts
- Comment support (HAML comments `-#` and HTML comments `/`)
- Ruby filter support (`:ruby` blocks)
- Comprehensive Ruby operator, keyword, and constant highlighting

