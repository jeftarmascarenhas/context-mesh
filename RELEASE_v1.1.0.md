# Release Guide - Context Mesh v1.1.0

Este guia contém as instruções para criar a release v1.1.0 no GitHub.

## Pré-requisitos

1. Todos os arquivos devem estar commitados
2. Repositório deve estar no GitHub
3. Você deve ter permissões de administrador no repositório
4. CHANGELOG.md e README.md já foram atualizados

## Passo 1: Criar Tag

No terminal, execute:

```bash
# Navegue até o diretório do projeto
cd /Users/jeffmascarenhas/AI-First/ai-first-framework

# Crie a tag
git tag -a v1.1.0 -m "Release v1.1.0: Improved prompts with bidirectional linking and optional patterns"

# Envie a tag para o GitHub
git push origin v1.1.0
```

## Passo 2: Criar Release no GitHub

1. Acesse o repositório no GitHub
2. Clique na aba **"Releases"** (ou acesse: `https://github.com/jeftarmascarenhas/context-mesh/releases`)
3. Clique em **"Draft a new release"**
4. Selecione a tag **v1.1.0** no dropdown
5. Preencha os campos:

### Título da Release:
```
Context Mesh v1.1.0 - Improved Prompts & Bidirectional Linking
```

### Descrição da Release:
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

6. Marque como **"Latest release"**
7. Clique em **"Publish release"**

## Passo 3: Verificar

Após criar a release, verifique:

1. ✅ A release aparece na página de releases
2. ✅ O badge de versão no README aponta para v1.1.0
3. ✅ A tag v1.1.0 está criada no repositório
4. ✅ O CHANGELOG.md está atualizado
5. ✅ A descrição da release está completa

## Resumo das Mudanças

### Arquivos Modificados
- `CHANGELOG.md` - Adicionada seção v1.1.0
- `README.md` - Versão atualizada para 1.1.0
- `prompts/new-project.md` - Adicionada pergunta opcional sobre patterns
- `prompts/add-feature.md` - Instruções explícitas sobre links bidirecionais
- `prompts/update-feature.md` - Instruções para manter links
- `prompts/existing-project.md` - Formatos de links corrigidos
- `prompts/freelance-project.md` - Formatos de links corrigidos

### Tipo de Release
- **MINOR** (v1.1.0): Novas features e melhorias (compatível com v1.0.0)

