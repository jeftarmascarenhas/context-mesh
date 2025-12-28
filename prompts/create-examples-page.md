# Prompt: Criar Página de Exemplos do Site

Use este prompt para criar a página de exemplos do site Context Mesh (https://www.context-mesh.org/pt/docs/examples).

## Contexto

A página de exemplos deve mostrar como Context Mesh funciona na prática. O exemplo principal será **Portfólio de Desenvolvedor** (ou outro exemplo escolhido).

## Estrutura da Página

A página deve usar **single page com seções** (não tabs), seguindo esta estrutura:

---

## 🎯 Seção 1: Visão Geral

### Conteúdo Obrigatório:

1. **O que vamos construir**
   - Descrição breve do projeto
   - Stack tecnológico (Next.js, MDX, Tailwind, etc.)
   - Tempo estimado (2-3 horas)

2. **Comparação: Método Tradicional vs Context Mesh**
   - **Método Tradicional:**
     - Planejamento: 30 min (rápido, sem estrutura)
     - Desenvolvimento: 8-12 horas (muitas idas e vindas, decisões no meio do caminho)
     - Documentação: 2-3 horas (depois, quando sobra tempo)
     - **Total: 10-15 horas** + contexto perdido ao longo do tempo
   
   - **Com Context Mesh:**
     - **Intent (Planejamento)**: 2-3 horas (estruturado, completo, decisões documentadas)
     - **Build (Desenvolvimento)**: 1-2 horas (AI gera código baseado no context)
     - **Learn (Atualização)**: 15-30 min (context atualizado continuamente)
     - **Total: 3-5 horas** + contexto preservado para sempre
   
   - **Economia: 7-10 horas** + contexto nunca se perde

3. **Visualização do Tempo** (opcional, mas recomendado)
   ```
   ┌─────────────────────────────────────┐
   │ Método Tradicional: 10-15 horas    │
   │ Context Mesh: 3-5 horas             │
   │                                      │
   │ Economia: 7-10 horas ⚡             │
   └─────────────────────────────────────┘
   ```

---

## 📋 Seção 2: Passo 1 - Intent (Planejamento)

> 💡 **Filosofia Context Mesh**: Invista tempo no Intent. Um bom planejamento reduz drasticamente o tempo de desenvolvimento e garante que decisões sejam tomadas com contexto completo.

### Conteúdo Obrigatório:

1. **Project Intent**
   - Mostrar `project-intent.md` completo
   - Incluir: What, Why, Scope, Acceptance Criteria, Constraints
   - Formatar de forma clara e legível

2. **Features (Funcionalidades)**
   - Listar todas as `feature-*.md` files
   - Mostrar conteúdo de cada feature:
     - `feature-homepage.md`
     - `feature-blog.md`
     - `feature-projects.md`
     - `feature-contact.md`
   - Cada feature deve mostrar: What, Why, Acceptance Criteria

3. **Decisions (Decisões Técnicas)**
   - Mostrar todas as `decisions/001-*.md` files
   - Incluir decisões principais:
     - `001-tech-stack.md` (Next.js, MDX, Tailwind)
     - `002-blog-approach.md` (MDX vs CMS)
     - `003-contact-form.md` (Resend vs SendGrid)
     - `004-styling-approach.md` (Tailwind vs CSS Modules)
   - Cada decision deve mostrar: Context, Decision, Rationale, Alternatives Considered

4. **Outros Elementos do Intent**
   - Constraints (limitações)
   - Success Criteria (critérios de sucesso)
   - Related files (relacionamentos entre arquivos)

5. **Destaque de Tempo**
   - Badge ou destaque: "Investir tempo aqui economiza horas depois"
   - Estatística: "70% do tempo economizado vem do Intent bem feito"
   - **Tempo investido aqui: 2-3 horas**

### Formatação:
- Usar seções colapsáveis para não ficar muito longo
- Destacar a importância do Intent
- Mostrar que tudo está planejado antes de começar a codar

---

## 🚀 Seção 3: Passo 2 - Build (Implementação)

### Conteúdo Obrigatório:

1. **Context Completo Disponível**
   - Mostrar estrutura de pastas completa:
     ```
     portfolio-project/
     ├── context/
     │   ├── intent/
     │   │   ├── project-intent.md
     │   │   ├── feature-homepage.md
     │   │   ├── feature-blog.md
     │   │   └── feature-contact.md
     │   ├── decisions/
     │   │   ├── 001-tech-stack.md
     │   │   ├── 002-blog-approach.md
     │   │   └── ...
     │   ├── knowledge/
     │   │   └── patterns/
     │   └── agents/
     │       ├── agent-setup.md
     │       ├── agent-homepage.md
     │       └── ...
     └── AGENTS.md
     ```
   - Enfatizar: "Você já tem toda a estrutura de context pronta"

2. **Como Executar (sem precisar ir para o repositório)**
   - Explicar que o usuário tem acesso à pasta `context/` completa
   - Mostrar como usar o `AGENTS.md` como roteador:
     ```markdown
     # Para implementar a homepage:
     @context/agents/agent-homepage.md
     @context/intent/feature-homepage.md
     @context/decisions/001-tech-stack.md
     ```
   
   - Explicar o processo:
     1. Use o AGENTS.md como roteador
     2. AI carrega todos os arquivos de context
     3. AI entende o que fazer (intent)
     4. AI sabe como fazer (decisions)
     5. AI segue os padrões (knowledge/patterns)
     6. AI gera código baseado no context completo

3. **Implementação Fase por Fase**
   - Listar as fases:
     - Setup → Homepage → Blog → Projects → Contact
   - Explicar que cada fase usa o context completo
   - Mostrar que não há necessidade de ir para o repositório

4. **Tempo de Desenvolvimento**
   - **Tempo: 1-2 horas**
   - Explicar por que é rápido:
     - AI trabalha com context completo
     - Menos idas e vindas
     - Código consistente desde o início

### Formatação:
- Mostrar código real quando possível
- Explicar o processo passo a passo
- Enfatizar que tudo está no context, não precisa buscar em outro lugar

---

## 📚 Seção 4: Passo 3 - Learn (Aprendizado e Atualização)

### Conteúdo Obrigatório:

1. **O Ciclo Completo: Intent → Build → Learn**
   - Explicar que após implementar, você **atualiza o context** com o que aprendeu
   - Mostrar o ciclo:
     ```
     Intent (Plan) → Build (Implement) → Learn (Update)
          ↑                                          ↓
          └─────────── Context Atualizado ───────────┘
     ```

2. **Como Atualizar o Context (Learn)**

   a. **Atualizar Decisions com Outcomes**
      - Mostrar exemplo:
        ```markdown
        # 001-tech-stack.md
        
        ## Outcomes (após implementação)
        - ✅ Next.js 14 funcionou perfeitamente
        - ✅ MDX foi fácil de integrar
        - ✅ Tailwind CSS acelerou desenvolvimento
        - ⚠️ Resend tem limite de 100 emails/dia (free tier)
        ```
   
   b. **Documentar Patterns Aprendidos**
      - Mostrar exemplo:
        ```markdown
        # knowledge/patterns/mdx-blog.md
        Como estruturar posts MDX no Next.js 14...
        ```
   
   c. **Atualizar Feature Intents**
      - Mostrar exemplo:
        ```markdown
        # feature-blog.md
        ## Status: ✅ Implemented
        ## Learnings:
        - MDX funciona melhor com frontmatter
        - Adicionar syntax highlighting melhorou UX
        ```
   
   d. **Usar Agents para Manutenção**
      - Mostrar exemplo:
        ```markdown
        # context/agents/agent-update-blog.md
        Para adicionar nova feature ao blog:
        1. Atualizar feature-blog.md
        2. Criar decision se necessário
        3. Implementar
        4. Atualizar context (Learn)
        ```

3. **O Ciclo Contínuo**
   - Explicar que o Learn não é só no final
   - Context é atualizado continuamente
   - Próximas features serão mais rápidas
   - Conhecimento preservado para sempre

4. **Tempo de Atualização**
   - **Tempo: 15-30 min**
   - Explicar que é rápido porque:
     - Context sempre atualizado
     - Próximas features mais rápidas
     - Conhecimento preservado

5. **Demonstrar as 3 Steps do Framework**
   - Mostrar claramente:
     - **Intent**: Planejamento completo (2-3h)
     - **Build**: Implementação com AI (1-2h)
     - **Learn**: Atualização contínua (15-30min)
   - Enfatizar que Agent faz parte do processo Build

### Formatação:
- Mostrar exemplos reais de atualização
- Explicar o ciclo contínuo
- Destacar que o Learn não é opcional, é parte do processo

---

## 🎯 Seção 5: Resultado Final

### Conteúdo Obrigatório:

- ✅ Projeto completo implementado
- ✅ Context preservado para sempre
- ✅ Próximas features serão mais rápidas
- ✅ Qualquer desenvolvedor pode entender o projeto
- ✅ AI pode trabalhar com context completo

### Opcional:
- Screenshot ou demo do projeto final
- Comparação visual antes/depois (se aplicável)

---

## 📖 Seção 6: Próximos Passos

### Conteúdo Obrigatório:

- [ ] Ver exemplo completo no repositório
- [ ] Adaptar para seu projeto
- [ ] Experimentar o ciclo Intent → Build → Learn

---

## Diretrizes de Formatação

1. **Usar seções colapsáveis** para conteúdo longo (especialmente no Passo 1)
2. **Destacar números e estatísticas** (tempo economizado, etc.)
3. **Usar código real** quando possível
4. **Mostrar estrutura de pastas** de forma clara
5. **Incluir exemplos práticos** em cada seção
6. **Manter tom educativo** mas não condescendente
7. **Enfatizar o valor** (tempo economizado, contexto preservado)

---

## Elementos Visuais Recomendados

1. **Comparação de Tempo** (gráfico ou tabela)
2. **Diagrama do Ciclo** Intent → Build → Learn
3. **Estrutura de Pastas** (árvore visual)
4. **Screenshots** do resultado final (se disponível)
5. **Badges** para destacar informações importantes

---

## Notas Importantes

- A página deve ser **autossuficiente** - não deve exigir que o usuário vá para o repositório para entender
- O **Passo 1 (Intent)** deve mostrar TUDO: project-intent, features, decisions, etc.
- O **Passo 2 (Build)** deve mostrar como executar com o context que já está disponível
- O **Passo 3 (Learn)** deve demonstrar as 3 steps do framework e mostrar o ciclo completo
- Enfatizar que **Agent faz parte do Build**, não é uma etapa separada
- Manter foco em **educar sobre o framework**, não apenas mostrar código

---

## Exemplo de Uso

1. Escolher o exemplo (ex: Portfólio de Desenvolvedor)
2. Coletar todos os arquivos de context do exemplo
3. Seguir esta estrutura para criar a página
4. Garantir que todos os arquivos de context estejam acessíveis na página
5. Testar a navegação e clareza

---

## Checklist Final

- [ ] Visão Geral com comparação de tempo
- [ ] Passo 1 mostra project-intent, features, decisions completos
- [ ] Passo 2 mostra como executar sem ir para repositório
- [ ] Passo 3 demonstra as 3 steps e o ciclo completo
- [ ] Agent explicado como parte do Build
- [ ] Resultado final mostrado
- [ ] Próximos passos claros
- [ ] Formatação clara e legível
- [ ] Elementos visuais quando apropriado



