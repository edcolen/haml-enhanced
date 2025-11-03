# Publishing Checklist for HAML Enhanced

## ✅ Required Files (Complete)

- [x] **package.json** - Has all required fields
- [x] **README.md** - Good documentation
- [x] **LICENSE** - MIT License included
- [x] **CHANGELOG.md** - Version history documented
- [x] **.vscodeignore** - Excludes unnecessary files
- [x] **Grammar file** - haml.tmLanguage.json with custom patterns
- [x] **Language configuration** - haml-configuration.json

## ⚠️ Recommended Improvements (Before Publishing)

### 1. Add Extension Icon (Highly Recommended)
**Status:** ❌ Missing

Create a 128x128 PNG icon for your extension.

**Action needed:**
- Create an icon (e.g., `icon.png`)
- Add to package.json: `"icon": "icon.png"`

### 2. Add Screenshots (Highly Recommended)
**Status:** ❌ Missing

Screenshots showing the multiline hash feature in action will significantly help users understand the value.

**Action needed:**
- Take screenshots showing before/after comparison
- Create an `images/` folder
- Add screenshots to README.md
- Update .vscodeignore to NOT exclude images

**Example sections for README:**
```markdown
## Screenshots

### Before (Standard HAML Extension)
![Before](images/before.png)

### After (HAML Enhanced)
![After](images/after.png)
```

### 3. Update .vscodeignore
**Status:** ⚠️ Needs improvement

Should exclude test and development files from the published package.

**Current issues:**
- `test.haml` will be included
- `TESTING.md` and `QUICKSTART.md` will be included

**Recommended addition:**
```
test.haml
TESTING.md
QUICKSTART.md
.vscode/**
```

### 4. Update package.json
**Status:** ⚠️ Missing optional fields

Add these recommended fields:

```json
{
  "license": "MIT",
  "icon": "icon.png",
  "homepage": "https://github.com/edcolen/haml-enhanced#readme",
  "bugs": {
    "url": "https://github.com/edcolen/haml-enhanced/issues"
  },
  "galleryBanner": {
    "color": "#C80000",
    "theme": "dark"
  }
}
```

### 5. Create GitHub Repository
**Status:** ❌ Not created yet

The package.json references `https://github.com/edcolen/haml-enhanced` but this repository doesn't exist yet.

**Action needed:**
1. Create the repository on GitHub
2. Push your code
3. Verify the URL in package.json matches

## 📋 Pre-Publishing Steps

### 1. Register Publisher Account
**Status:** ⚠️ Unknown

You need to register "EdColen" as a publisher on the VS Code Marketplace.

**Steps:**
1. Go to https://marketplace.visualstudio.com/manage
2. Sign in with Microsoft/GitHub account
3. Create publisher "EdColen"
4. Get a Personal Access Token (PAT)

### 2. Install VSCE
**Status:** ⚠️ Check if installed

```bash
npm install -g @vscode/vsce
```

### 3. Test the Package Locally

```bash
# Package the extension
vsce package

# This creates haml-enhanced-0.1.0.vsix
# Test install it locally:
code --install-extension haml-enhanced-0.1.0.vsix
```

### 4. Publish to Marketplace

```bash
# Login (you'll need your PAT)
vsce login EdColen

# Publish
vsce publish
```

## 🎯 Priority Actions (Do These First)

1. **HIGH PRIORITY:**
   - [ ] Create GitHub repository
   - [ ] Push code to GitHub
   - [ ] Update .vscodeignore to exclude test files
   - [ ] Add screenshots to README
   - [ ] Register publisher account

2. **MEDIUM PRIORITY:**
   - [ ] Create an icon
   - [ ] Add icon to package.json
   - [ ] Update package.json with optional fields
   - [ ] Test package locally

3. **BEFORE PUBLISHING:**
   - [ ] Test installation from VSIX
   - [ ] Verify all features work
   - [ ] Check README renders correctly
   - [ ] Verify no sensitive files are included

## 📊 Current Status: 70% Ready

**What's working:**
- ✅ Core extension functionality is complete
- ✅ Documentation is good
- ✅ License is proper
- ✅ Version control is set up

**What's needed:**
- ❌ GitHub repository doesn't exist
- ❌ No screenshots (important for marketplace)
- ❌ No icon (makes extension look professional)
- ⚠️ Some package.json fields missing
- ⚠️ Publisher account status unknown

## 🚀 Estimated Time to Publish-Ready

- **If you have screenshots ready:** 30-60 minutes
- **If you need to create screenshots:** 1-2 hours
- **If you need to create icon:** +30 minutes

## 📝 Notes

- The extension code itself is solid and ready
- The grammar file is well-structured
- Documentation is clear and helpful
- Main blockers are presentation (icon, screenshots) and infrastructure (GitHub, publisher account)

---

**Next Steps:**
1. Create GitHub repo
2. Take screenshots showing the multiline hash feature
3. Create or find an icon
4. Update the files as noted above
5. Package and test locally
6. Register publisher account
7. Publish! 🎉

