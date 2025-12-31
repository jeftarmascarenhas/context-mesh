# Release Guide - Context Mesh v1.1.0

This guide contains instructions for creating the v1.1.0 release on GitHub.

## Prerequisites

1. All files must be committed
2. Repository must be on GitHub
3. You must have administrator permissions on the repository
4. CHANGELOG.md and README.md have been updated

## Step 1: Create Tag

In the terminal, execute:

```bash
# Navigate to the project directory
cd /Users/jeffmascarenhas/AI-First/ai-first-framework

# Create the tag
git tag -a v1.1.0 -m "Release v1.1.0: Improved prompts with bidirectional linking and optional patterns"

# Push the tag to GitHub
git push origin v1.1.0
```

## Step 2: Create Release on GitHub

1. Access the repository on GitHub
2. Click on the **"Releases"** tab (or access: `https://github.com/jeftarmascarenhas/context-mesh/releases`)
3. Click **"Draft a new release"**
4. Select the **v1.1.0** tag from the dropdown
5. Fill in the fields:

### Release Title:
```
Context Mesh v1.1.0 - Improved Prompts & Bidirectional Linking
```

### Release Description:
```markdown
## 🚀 Release v1.1.0 - Improved Prompts & Bidirectional Linking

This release focuses on improving prompt quality, fixing link consistency, and adding flexibility to project initialization.

### ✨ What's New

#### New Features
- **Optional Initial Patterns** in `new-project.md`
  - Add patterns during project initialization
  - Template for pattern files included
  - Maintains flexibility (can be added later)

#### Improvements
- **Bidirectional Linking** across all prompts
  - Feature files now properly link to decision files
  - Decision files link back to feature files
  - Standardized markdown link format throughout
- **Enhanced Prompt Templates**
  - All prompts use consistent link format
  - Templates match examples in repository
  - Better instructions for AI agents

#### Fixes
- Fixed missing bidirectional links between features and decisions
- Corrected link format in all templates
- Improved consistency across all prompts

### 📝 Changed Prompts

- `new-project.md` - Added optional patterns, improved hybrid approach
- `add-feature.md` - Explicit bidirectional linking instructions
- `update-feature.md` - Link maintenance when updating features
- `existing-project.md` - Corrected link formats
- `freelance-project.md` - Corrected link formats

### 🔗 Links Format

All prompts now use standardized format:
```markdown
## Related
- [Project Intent](project-intent.md)
- [Decision: Feature Name](../decisions/[number]-[name].md)
- [Feature: Feature Name](../intent/feature-[name].md)
```

### 📚 Documentation Updates

- CHANGELOG.md updated with all changes
- README.md version badge updated to v1.1.0
- All prompts reference complete AGENTS.md template

### 🎯 Migration Guide

**No breaking changes** - This is a minor version update. Existing projects continue to work.

If you want to update your existing Context Mesh projects:
1. Review your feature and decision files
2. Ensure bidirectional links exist
3. Update link formats if needed (optional, but recommended)

### 📖 Full Changelog

See [CHANGELOG.md](CHANGELOG.md) for complete list of changes.

---

**Upgrade from v1.0.0**: No action required. All changes are backward compatible.

**Questions?** Open an [issue](https://github.com/jeftarmascarenhas/context-mesh/issues) or check [FAQ.md](FAQ.md).
```

6. Mark as **"Latest release"**
7. Click **"Publish release"**

## Step 3: Verify

After creating the release, verify:

1. ✅ The release appears on the releases page
2. ✅ The version badge in README points to v1.1.0
3. ✅ The v1.1.0 tag is created in the repository
4. ✅ CHANGELOG.md is updated
5. ✅ The release description is complete

## Summary of Changes

### Modified Files
- `CHANGELOG.md` - Added v1.1.0 section
- `README.md` - Version updated to 1.1.0
- `prompts/new-project.md` - Added optional question about patterns
- `prompts/add-feature.md` - Explicit bidirectional linking instructions
- `prompts/update-feature.md` - Instructions to maintain links
- `prompts/existing-project.md` - Corrected link formats
- `prompts/freelance-project.md` - Corrected link formats

### Release Type
- **MINOR** (v1.1.0): New features and improvements (compatible with v1.0.0)

