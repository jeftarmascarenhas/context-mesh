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
git tag -a v1.1.0 -m "Release v1.1.0: Improved prompts with bidirectional linking, optional patterns, and prompt pack reorganization"

# Push the tag to GitHub
git push origin v1.1.0
```

## Step 2: Create ZIP File for Context Mesh Hub

Before creating the release, create a ZIP file containing the prompt pack for Context Mesh Hub:

```bash
# Navigate to the project directory
cd /Users/jeffmascarenhas/AI-First/ai-first-framework

# Create ZIP file with the prompt pack
zip -r context-mesh-core-1.1.0.zip prompt-packs/context-mesh-core/1.1.0/

# Verify the ZIP was created
ls -lh context-mesh-core-1.1.0.zip
```

**ZIP Contents:**
- `prompt-packs/context-mesh-core/1.1.0/` directory with all prompt files:
  - `new-project.md`
  - `existing-project.md`
  - `freelance-project.md`
  - `add-feature.md`
  - `update-feature.md`
  - `fix-bug.md`
  - `learn-update.md`
  - `create-agent.md`
  - `README.md`

**Note:** This ZIP file will be downloaded by the Context Mesh Hub tool for prompt pack distribution.

## Step 3: Create Release on GitHub

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

This release focuses on improving prompt quality, fixing link consistency, adding flexibility to project initialization, and reorganizing prompts into a versioned structure for Context Mesh Hub compatibility.

### ✨ What's New

#### New Features
- **Optional Initial Patterns** in `new-project.md`
  - Add patterns during project initialization
  - Template for pattern files included
  - Maintains flexibility (can be added later)
- **Prompt Pack Structure** - Reorganized prompts for Context Mesh Hub
  - Prompts moved to `prompt-packs/context-mesh-core/1.1.0/`
  - Versioned structure enables prompt pack management
  - Compatible with Context Mesh Hub tooling

#### Improvements
- **Bidirectional Linking** across all prompts
  - Feature files now properly link to decision files
  - Decision files link back to feature files
  - Standardized markdown link format throughout
- **Enhanced Prompt Templates**
  - All prompts use consistent link format
  - Templates match examples in repository
  - Better instructions for AI agents
- **Prompt Organization**
  - Prompts organized in versioned directory structure
  - All documentation links updated to new prompt locations
  - Structure supports future prompt pack versions

#### Fixes
- Fixed missing bidirectional links between features and decisions
- Corrected link format in all templates
- Improved consistency across all prompts

### 📝 Changed Prompts

All prompts are now located in `prompt-packs/context-mesh-core/1.1.0/`:

- `prompt-packs/context-mesh-core/1.1.0/new-project.md` - Added optional patterns, improved hybrid approach
- `prompt-packs/context-mesh-core/1.1.0/add-feature.md` - Explicit bidirectional linking instructions
- `prompt-packs/context-mesh-core/1.1.0/update-feature.md` - Link maintenance when updating features
- `prompt-packs/context-mesh-core/1.1.0/existing-project.md` - Corrected link formats
- `prompt-packs/context-mesh-core/1.1.0/freelance-project.md` - Corrected link formats
- `prompt-packs/context-mesh-core/1.1.0/fix-bug.md` - Bug fix prompt
- `prompt-packs/context-mesh-core/1.1.0/learn-update.md` - Context update prompt
- `prompt-packs/context-mesh-core/1.1.0/create-agent.md` - Agent creation prompt

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
- README.md version badge updated to v1.1.0, all prompt links updated to new structure
- GETTING_STARTED.md - All prompt references updated to `prompt-packs/context-mesh-core/1.1.0/`
- FRAMEWORK.md - Prompt references updated
- RELEASE_v1.1.0.md - Updated with prompt reorganization details
- CONTRIBUTING.md - Updated prompt directory reference
- .github/pull_request_template.md - Updated prompt directory reference
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

6. **Attach ZIP file** (for Context Mesh Hub):
   - Scroll down to the "Attach binaries" section
   - Click **"Attach files by dropping them here or selecting them"**
   - Select the `context-mesh-core-1.1.0.zip` file (created in Step 2)
   - Wait for upload to complete

7. Mark as **"Latest release"**
8. Click **"Publish release"**

## Step 4: Verify

After creating the release, verify:

1. ✅ The release appears on the releases page
2. ✅ The version badge in README points to v1.1.0
3. ✅ The v1.1.0 tag is created in the repository
4. ✅ CHANGELOG.md is updated
5. ✅ The release description is complete
6. ✅ The ZIP file (`context-mesh-core-1.1.0.zip`) is attached to the release
7. ✅ ZIP file can be downloaded from the release assets

## Summary of Changes

### Modified Files
- `CHANGELOG.md` - Added v1.1.0 section
- `README.md` - Version updated to 1.1.0, all prompt links updated
- `GETTING_STARTED.md` - All prompt references updated to new structure
- `FRAMEWORK.md` - Prompt references updated
- `RELEASE_v1.1.0.md` - Updated with prompt reorganization
- `CONTRIBUTING.md` - Updated prompt directory reference
- `.github/pull_request_template.md` - Updated prompt directory reference
- `prompt-packs/context-mesh-core/1.1.0/README.md` - Fixed relative links
- `context-mesh-site/context/agents/agent-resources.md` - Updated prompt path reference
- `context-mesh-site/prompts/update-quick-start-page.md` - Updated prompt path references

### Prompt Files (Moved)
All prompts moved from `prompts/` to `prompt-packs/context-mesh-core/1.1.0/`:
- `prompt-packs/context-mesh-core/1.1.0/new-project.md` - Added optional question about patterns
- `prompt-packs/context-mesh-core/1.1.0/add-feature.md` - Explicit bidirectional linking instructions
- `prompt-packs/context-mesh-core/1.1.0/update-feature.md` - Instructions to maintain links
- `prompt-packs/context-mesh-core/1.1.0/existing-project.md` - Corrected link formats
- `prompt-packs/context-mesh-core/1.1.0/freelance-project.md` - Corrected link formats
- `prompt-packs/context-mesh-core/1.1.0/fix-bug.md`
- `prompt-packs/context-mesh-core/1.1.0/learn-update.md`
- `prompt-packs/context-mesh-core/1.1.0/create-agent.md`

### Release Type
- **MINOR** (v1.1.0): New features and improvements (compatible with v1.0.0)

