# Testing Guide for HAML Enhanced

This guide will help you systematically test the HAML Enhanced syntax highlighting extension.

## Setup

1. **Open Extension Development Host**
   - Open this project in VS Code
   - Press `F5` to launch the Extension Development Host
   - In the new window, open the `test.haml` file

2. **Verify Extension is Active**
   - Check the status bar at the bottom right - it should show "HAML" as the language
   - If not, click on the language indicator and select "HAML"

## What to Test

The `test.haml` file is organized into sections. Go through each section and verify the syntax highlighting works correctly.

### ✅ 1. Comments (Lines 8-12)

**Expected Behavior:**
- `-#` comments should be highlighted as comments (usually green/gray)
- `/` HTML comments should also be highlighted as comments

**How to Verify:**
- Both comment types should have distinct coloring from regular code
- Comment text should be dimmed/grayed out

---

### ✅ 2. Basic HAML Tags (Lines 16-23)

**Expected Behavior:**
- Tag names like `%div`, `%section`, `%article` should be highlighted as HTML tags (usually blue/purple)
- Text content after tags should be plain text

**How to Verify:**
- The `%` symbol and tag name should have a distinct color
- Regular text should be in default color

---

### ✅ 3. Classes and IDs (Lines 27-36)

**Expected Behavior:**
- `.class-name` should be highlighted as CSS class (usually orange/yellow)
- `#id-name` should be highlighted as CSS ID (usually orange/yellow)
- Multiple chained classes should each be highlighted

**How to Verify:**
- Dots and hash symbols should be visible and colored
- Each class/id segment should be highlighted
- `.implicit-div` and `#implicit-id` should work without `%div`

---

### ✅ 4. Single-Line Hash Attributes (Lines 40-46)

**Expected Behavior:**
- Curly braces `{}` should be highlighted as punctuation
- Hash keys (`class:`, `href:`) should be highlighted as symbols/keys
- Colon separator should be visible
- String values in quotes should be highlighted as strings
- Nested hashes should also be highlighted

**How to Verify:**
- Keys like `class`, `id`, `href` should have symbol/key coloring
- String values in quotes should have string coloring
- Nested `data: { controller: "stimulus" }` should highlight properly

---

### ✅ 5. **Multiline Hash Attributes** (Lines 50-95) ⭐ **MAIN FEATURE**

This is the key feature of your extension! Test carefully.

**Expected Behavior:**
- Opening `{` on the tag line should be highlighted
- **Each line inside the hash should be properly highlighted:**
  - Hash keys should be colored as symbols/keys
  - Colons should be visible
  - String values should be highlighted as strings
  - Symbols (`:symbol_value`) should be highlighted
  - Numbers should be highlighted as numbers
  - Booleans (`true`, `false`, `nil`) should be highlighted
  - Arrays `[1, 2, 3]` should have proper bracket highlighting
  - Nested hashes should work recursively
  - String interpolation `#{...}` should be highlighted
- Closing `}` should be highlighted

**How to Verify - Test 1 (Lines 54-58):**
```haml
.zen-mobile-table-wrapper{
  class: local_assigns[:class],
  id: "unique-id",
  data: { controller: "tabbed-table" }
}
```
- `class:` and `id:` and `data:` should be highlighted as keys
- `"unique-id"` and `"tabbed-table"` should be strings
- Nested `{ controller: "tabbed-table" }` should work
- The closing `}` should be highlighted

**How to Verify - Test 3 (Lines 75-85):**
This tests all data types:
- `string: "value"` - key and string value
- `symbol: :symbol_value` - key and symbol (`:symbol_value` should be colored)
- `number: 42` and `float: 3.14` - numbers should be highlighted
- `boolean_true: true` - boolean should be highlighted
- `nil_value: nil` - nil should be highlighted
- `array: [1, 2, 3]` - brackets and numbers should be highlighted
- `nested: { key: "value" }` - nested hash should work

**How to Verify - Test 4 (Lines 88-91):**
String interpolation in multiline hashes:
- `"container-#{size}"` - the `#{size}` should be highlighted differently than the string
- Nested interpolation should work in nested hashes

---

### ✅ 6. Ruby Code Blocks (Lines 99-119)

**Expected Behavior:**
- Lines starting with `-` should highlight the Ruby code after it
- Ruby keywords (`if`, `else`, `each`, `do`, `case`, `when`) should be highlighted
- Variables and method calls should have Ruby syntax highlighting

**How to Verify:**
- `- if user.present?` - the `if` keyword should be highlighted
- `- users.each do |user|` - keywords and block parameters should be highlighted
- `- case status` / `- when :active` - case/when should be highlighted

---

### ✅ 7. Output Ruby Code (Lines 123-130)

**Expected Behavior:**
- Lines starting with `=` should highlight as output code
- The `=` symbol should be highlighted
- Ruby code after `=` should have Ruby syntax highlighting

**How to Verify:**
- `= title` - the `=` should be highlighted
- `= render "partial", locals: { key: "value" }` - method calls, strings, hashes should be highlighted

---

### ✅ 8. String Interpolation (Lines 134-140)

**Expected Behavior:**
- `#{...}` within text or strings should be highlighted differently
- The content inside `#{}` should have Ruby syntax highlighting

**How to Verify:**
- `%p Welcome, #{user.name}!` - `#{user.name}` should be distinct from regular text
- `.alert-#{type}` - interpolation in class names should work
- Interpolation in hash values should work

---

### ✅ 9. Ruby Filters (Lines 144-153)

**Expected Behavior:**
- `:ruby` should be highlighted as a keyword
- All code inside the Ruby filter should have full Ruby syntax highlighting
- Method definitions, variables, blocks should all be highlighted

**How to Verify:**
- `:ruby` at line 147 should be highlighted
- The `def helper_method` should have Ruby highlighting
- Arrays and blocks like `[1, 2, 3].map { |n| n * 2 }` should be highlighted

---

### ✅ 10. Complex Real-World Example (Lines 157-203)

This combines multiple features. Verify that:
- Nested conditionals work
- Multiline hashes inside conditionals work
- Ruby code blocks maintain highlighting
- All previously tested features work in combination

---

### ✅ 11. Edge Cases (Lines 207-237)

**Expected Behavior:**
- Empty tags `%div` should work
- Self-closing tags `%br/`, `%img{...}/` should work
- Deeply nested structures should maintain highlighting
- Mixed attribute styles should work (though unusual)

---

## Visual Checklist

When reviewing the `test.haml` file, look for these color patterns (exact colors depend on your theme):

| Element | Expected Highlighting |
|---------|---------------------|
| `-#` and `/` | Comment color (gray/green) |
| `%tag` | HTML tag color (blue/purple) |
| `.class`, `#id` | Class/ID color (orange/yellow) |
| Hash keys `key:` | Symbol/key color (cyan/blue) |
| Strings `"..."` | String color (green/red) |
| Symbols `:symbol` | Symbol color (cyan) |
| Numbers `42`, `3.14` | Number color (orange) |
| Booleans `true`, `false`, `nil` | Keyword color (purple) |
| `#{}` interpolation | Embedded code color |
| Ruby keywords | Keyword color (purple/pink) |
| `{}`, `[]`, `()` | Punctuation color |

## Common Issues to Check

### ❌ Multiline Hash Not Working
**Symptom:** Lines inside `{...}` are not highlighted, appear as plain text

**Check:**
1. Is the opening `{` on the same line as the tag/class?
2. Are the continuation lines properly indented?
3. Does the closing `}` align with the indentation level?

### ❌ Ruby Code Not Highlighted
**Symptom:** Ruby code after `=` or `-` appears as plain text

**Check:**
1. Is there a space after the `=` or `-`?
2. Is the Ruby extension installed in the Extension Development Host?

### ❌ Interpolation Not Working
**Symptom:** `#{...}` is not highlighted

**Check:**
1. The pattern should match `#{...}` exactly
2. This should work in strings, class names, and hash values

## Testing Different Themes

The syntax highlighting appearance varies by theme. Test with multiple themes:
1. Dark+ (default dark)
2. Light+ (default light)
3. Any theme you commonly use

To change theme: `Cmd+K Cmd+T` (Mac) or `Ctrl+K Ctrl+T` (Windows/Linux)

## Comparison Test

To see the difference between HAML Enhanced and standard HAML extensions:

1. Install a standard HAML extension (e.g., "Better Haml")
2. Open `test.haml` with the standard extension
3. Note which parts are **not** highlighted (especially multiline hashes)
4. Switch to HAML Enhanced (press F5 in your extension project)
5. The multiline hash sections should now be properly highlighted!

## Reporting Issues

If you find issues during testing:

1. Note the line number in `test.haml`
2. Describe what you expected vs. what you see
3. Take a screenshot if possible
4. Check the `syntaxes/haml.tmLanguage.json` patterns

## Next Steps After Testing

Once testing is complete:

1. ✅ Fix any highlighting issues found
2. ✅ Add more test cases if needed
3. ✅ Update README.md with screenshots
4. ✅ Build the VSIX package: `vsce package`
5. ✅ Publish to VS Code Marketplace: `vsce publish`

---

## Quick Test Command

Press `F5` → Open `test.haml` → Scroll through all sections → Verify colors match expectations.

Good luck with your testing! 🚀

