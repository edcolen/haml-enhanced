# Quick Start - Testing Your Extension

## Method 1: Using F5 (Recommended)

1. **Make sure you're in the extension project folder**
   ```
   /Users/edcolen/code/edcolen/haml-enhanced/
   ```

2. **Press F5** (or Run → Start Debugging)
   - A new VS Code window will open (titled "[Extension Development Host]")
   - Your extension is now active in that window

3. **Open the test file in the new window:**
   - Press `Cmd+O` (Mac) or `Ctrl+O` (Windows/Linux)
   - Browse to: `/Users/edcolen/code/edcolen/haml-enhanced/test.haml`
   - Or use `Cmd+P` and type "test.haml"

4. **Check the language mode:**
   - Look at the bottom-right corner of VS Code
   - It should say "HAML"
   - If it says something else, click it and select "HAML" from the list

5. **See the colors!**
   - Scroll through the file
   - Different elements should have different colors:
     - Comments: gray/green
     - Tags: blue/purple
     - Classes/IDs: yellow/orange
     - Strings: green/red
     - Ruby keywords: purple
     - Hash keys: cyan/blue

## Method 2: Manual Installation (For Permanent Use)

If you want to use the extension permanently:

1. **Install vsce** (if you haven't):
   ```bash
   npm install -g @vscode/vsce
   ```

2. **Package the extension:**
   ```bash
   cd /Users/edcolen/code/edcolen/haml-enhanced/
   vsce package
   ```
   This creates a `.vsix` file

3. **Install the VSIX:**
   - In VS Code: `Cmd+Shift+P` → "Extensions: Install from VSIX..."
   - Select the `.vsix` file that was created
   - Reload VS Code

4. **Open any .haml file** and it will use your extension!

---

## Troubleshooting

### "No colors appearing"

**Check 1:** Is the language set to HAML?
- Look at bottom-right corner
- Click the language indicator
- Select "HAML"

**Check 2:** Did the Extension Development Host open?
- You should see two VS Code windows
- The new one should say "[Extension Development Host]" in the title

**Check 3:** Try reloading
- In the Extension Development Host window
- Press `Cmd+R` (Mac) or `Ctrl+R` (Windows/Linux)

### "I see colors but multiline hashes aren't highlighted"

**Check:** Make sure the file is properly indented
- Multiline hash lines must be indented relative to the opening `{`
- Example:
  ```haml
  .wrapper{
    key: "value",    ← indented
    another: "test"  ← indented
  }                  ← closing brace
  ```

### "Ruby code isn't highlighted"

**Check:** Install Ruby extension support
- The Ruby syntax highlighting depends on the Ruby grammar
- Install "Ruby" extension by Shopify or similar
- Reload the Extension Development Host

---

## What You Should See

Here's what to look for in `test.haml`:

### ✅ Section 5 (Lines 50-95) - The Main Feature!
This is where multiline hash highlighting should really shine:

```haml
.component{
  string: "value",           ← "string:" should be colored as key
  symbol: :symbol_value,     ← ":symbol_value" should be colored
  number: 42,                ← "42" should be colored as number
  boolean_true: true,        ← "true" should be colored as keyword
  array: [1, 2, 3],         ← brackets and numbers colored
  nested: { key: "value" }  ← nested hash should work
}
```

**Each element should have distinct colors!**

### ✅ Section 8 (Lines 134-140) - String Interpolation
```haml
%p Welcome, #{user.name}!
```
The `#{user.name}` part should be highlighted differently than the surrounding text.

### ✅ Section 10 (Lines 157-203) - Real World Example
This combines everything - if this looks good, your extension is working perfectly!

---

## Comparing with Standard HAML Extensions

To see the improvement:

1. **Disable HAML Enhanced temporarily:**
   - In Extension Development Host, close it
   - Install a standard HAML extension (like "Better Haml")

2. **Open test.haml with the standard extension**
   - Notice lines 54-58, 75-85, 88-91
   - **The multiline hash contents will be plain/uncolored!**

3. **Now run HAML Enhanced (F5)**
   - Open test.haml again
   - **The multiline hash contents should now be colorful!**

This is your extension's superpower! 🎨

---

## Keyboard Shortcuts

| Action | Mac | Windows/Linux |
|--------|-----|---------------|
| Start debugging (F5) | F5 | F5 |
| Stop debugging | Cmd+Shift+F5 | Ctrl+Shift+F5 |
| Reload extension window | Cmd+R | Ctrl+R |
| Open file | Cmd+O | Ctrl+O |
| Quick open | Cmd+P | Ctrl+P |
| Change language | Click bottom-right | Click bottom-right |

---

## Next: Take Screenshots!

Once you see the colors working:

1. Take screenshots of the multiline hash sections (lines 50-95)
2. Add them to your README.md
3. Show the "before" (standard extension) and "after" (HAML Enhanced)
4. This will help users understand the value!

Happy testing! 🚀

