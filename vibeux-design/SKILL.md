---
name: vibeux-design
description: >
  Especialista em UI/UX para SaaS baseado no framework VibeUX (101 regras práticas).
  Use esta skill SEMPRE que o usuário fornecer um projeto novo ou já iniciado e pedir
  para gerar decisões de design, guias de interface ou um documento de design do projeto.
  Também ative quando o usuário mencionar: "gerar design system", "definir UI do projeto",
  "criar guia de interface", "quais regras de UX aplicar", "montar design doc",
  "regras de design para o projeto", "guia de UI para o agente". Esta skill produz um
  documento de design contextualizado, filtrando apenas as regras VibeUX relevantes
  para o projeto em questão, servindo tanto para uso humano quanto para agentes de IA
  que irão implementar a interface.
---

# VibeUX Design Skill

Gera o arquivo `design_<nome-projeto>.md` — documento de design contextualizado baseado
no framework VibeUX — a partir dos documentos do projeto, da referência visual e,
quando o projeto já estiver iniciado, da análise do code base existente.

O output serve dois públicos simultaneamente:
- **Humano** (Felipe / cliente): revisão de decisões e alinhamento
- **Agente Codex**: contexto de implementação de interface

Esta skill é otimizada para Codex. Em outro agente ou IDE, adapte primeiro os caminhos, ferramentas, permissões e convenções da skill ao ambiente de destino.

---

## Mapa de referências

Cada categoria de regras VibeUX está em um arquivo separado.
Carregue **apenas os arquivos das categorias que forem relevantes** para o projeto (veja critérios no Passo 3).

| # | Categoria | Arquivo | Carregar quando... |
|---|-----------|---------|-------------------|
| 1 | Interface e Visual | `references/cat1-interface-visual.md` | **Sempre** |
| 2 | Acesso e Onboarding | `references/cat2-acesso-onboarding.md` | `tem_onboarding = sim` |
| 3 | Navegação | `references/cat3-navegacao.md` | **Sempre** |
| 4 | Interações com Dados | `references/cat4-interacoes-dados.md` | `tem_listagem_dados = sim` |
| 5 | Formulários e Fluxos Longos | `references/cat5-formularios-fluxos.md` | `tem_formularios_longos = sim` |
| 6 | Relatórios e Dashboards | `references/cat6-relatorios-dashboards.md` | `tem_dashboard = sim` |
| 7 | Erros e Alertas | `references/cat7-erros-alertas.md` | **Sempre** |
| 8 | Performance | `references/cat8-performance.md` | **Sempre** |

---

## Abordagem inicial por tipo de projeto

Antes de iniciar, classifique o projeto em uma das duas situações abaixo:

1. **Projeto novo** — ainda não existe interface implementada ou code base relevante.
   - Consulte **sempre** o Briefing, o PRD e as Specs antes de gerar qualquer decisão de design.
   - Use esses documentos como fonte principal para entender escopo, usuários, fluxos, restrições e prioridades.
   - Se Briefing, PRD ou Specs estiverem ausentes, pergunte pelo material faltante antes de prosseguir. Não invente requisitos.

2. **Projeto já iniciado** — já existe interface, protótipo funcional, repositório, app Bubble, telas implementadas ou code base parcial/completo.
   - Consulte **sempre** Briefing, PRD e Specs, quando disponíveis.
   - Além dos documentos, consulte o **code base existente** antes de recomendar padrões, tokens, navegação, componentes ou refatorações visuais.
   - Analise o código existente para identificar padrões já usados, inconsistências, dívida visual, componentes reutilizáveis, limitações técnicas e riscos de regressão.
   - As recomendações devem respeitar o produto existente quando fizer sentido, mas devem corrigir divergências claras das regras VibeUX.
   - Se o code base não estiver disponível, registre a limitação no output e gere o design doc com base nos documentos disponíveis, sem presumir detalhes de implementação.

---

## Inputs obrigatórios

Antes de iniciar, confirme que você tem acesso a:

1. **Briefing do projeto** — `.md`, `.pdf`, `.docx` ou texto inline.
   Deve conter: nome do projeto, público-alvo, tipo de SaaS, funcionalidades principais,
   tom de marca (formal/descolado), restrições técnicas.

2. **PRD do projeto** — `.md`, `.pdf`, `.docx` ou texto inline.
   Deve conter: objetivos do produto, problemas a resolver, perfis de usuários,
   funcionalidades, critérios de sucesso e prioridades.

3. **Specs do projeto** — `.md`, `.pdf`, `.docx` ou texto inline.
   Deve conter: fluxos, regras de negócio, requisitos funcionais, requisitos não funcionais,
   estados de tela, permissões, integrações e restrições técnicas.

4. **Referência visual** — qualquer um dos formatos:
   - **Imagem/screenshot** (PNG, JPG, WebP) → extraia paleta, tipografia, densidade, estilo de borda
   - **URL** (Figma, site, Dribbble) → consulte pela ferramenta de navegação disponível ou peça descrição ao usuário
   - **Descrição textual** → use diretamente como input de estilo

5. **Code base existente** — obrigatório apenas para projetos já iniciados.
   Pode ser repositório, pasta de código, arquivos exportados, componentes, CSS, screenshots do app,
   estrutura Bubble ou qualquer material que revele a implementação atual.

Para **projetos novos**, se Briefing, PRD, Specs ou referência visual estiverem ausentes,
**pergunte antes de prosseguir**. Para **projetos já iniciados**, se o code base estiver ausente,
registre a limitação e prossiga somente com os documentos disponíveis. Não invente inputs.

Antes de recomendar componentes, confirme a stack, a estratégia de estilos, os tokens e as restrições de acessibilidade pela configuração e pelo codebase reais.

---

## Processo de geração

### Passo 1 — Extraia o contexto do projeto

A partir do Briefing, PRD, Specs e, quando houver, do code base existente, preencha o mapa de contexto:

```
nome_projeto:         [nome para usar no nome do arquivo de output]
tipo_saas:            [B2B | B2C | marketplace | interno | híbrido]
publico:              [perfil do usuário final]
tom_marca:            [formal/corporativo | neutro | moderno/descolado]
funcionalidades_core: [lista das 3–7 principais]
tem_dashboard:        [sim | não]
tem_formularios_longos:[sim | não]
tem_listagem_dados:   [sim | não]
tem_onboarding:       [sim | não]
plataforma_alvo:      [web | mobile | ambos]
stack_tecnica:        [Bubble | React | Next | outro — se mencionado]
status_projeto:       [novo | já iniciado]
fontes_consultadas:   [briefing | PRD | specs | referência visual | code base]
code_base_status:     [não aplicável | consultado | indisponível]
```

### Passo 2 — Extraia a identidade visual da referência

A partir da referência visual (qualquer formato), preencha:

```
paleta_primaria:      [hex da cor brand]
estilo_borda:         [sharp 0–2px | neutro 6–8px | moderno 12–20px | pill 9999px]
densidade_visual:     [compacta | média | espaçosa]
tipografia_referencia:[sans-serif moderna | serifada | monoespaçada | mista]
uso_de_sombras:       [flat/nenhuma | sutis | marcadas]
estilo_icones:        [outline | filled | misto]
presenca_gradientes:  [sim | não]
```

Se a referência for URL inacessível, peça ao usuário que descreva os atributos acima.

> **Conflito com VibeUX:** Se a referência visual usar algo proibido pelas regras
> (gradientes, emojis, sombras pesadas), registre o conflito no documento de output
> e recomende o comportamento VibeUX. Não silencie a divergência.

### Passo 3 — Carregue apenas as referências relevantes

Use o **Mapa de referências** no topo deste arquivo.
Para cada categoria marcada como relevante pelo contexto do Passo 1:

1. Leia o arquivo da categoria correspondente
2. Filtre somente as regras que fazem sentido para este projeto específico
3. Para cada regra selecionada, adicione uma **nota de aplicação contextualizada**
   (diretiva, não sugestiva — o agente implementador precisa de certezas)

Regras de categorias não relevantes: não carregue os arquivos, não as inclua no output.

### Passo 4 — Gere o arquivo de output

Siga exatamente o template abaixo. Combine com o usuário o local de saída; na ausência de convenção do projeto, use `docs/design_<nome-projeto>.md`.

---

## Template de output: design_<nome-projeto>.md

```markdown
# Design System — <Nome do Projeto>

> Gerado com VibeUX Framework · <data>
> Uso: implementação de interface (agente IA) + revisão humana

---

## 1. Contexto do Projeto

| Campo | Valor |
|-------|-------|
| Tipo de SaaS | <tipo> |
| Público-alvo | <perfil> |
| Tom de marca | <tom> |
| Plataforma | <web/mobile/ambos> |
| Stack técnica | <stack, se conhecida> |

---

## 2. Design Tokens

> Valores exatos para implementação. Não improvise variações.

### 2.1 Paleta de Cores

| Token | Valor | Uso |
|-------|-------|-----|
| `--color-bg` | #F9FAFB | Fundo geral |
| `--color-surface` | #FFFFFF | Cards e superfícies |
| `--color-text-primary` | #1D2939 | Texto principal |
| `--color-text-muted` | #667085 | Texto secundário |
| `--color-divider` | #EAECF0 | Divisores |
| `--color-border` | #D0D5DD | Bordas de inputs |
| `--color-brand` | <hex da referência> | Cor primária da marca |
| `--color-success` | #039855 | Sucesso |
| `--color-warning` | #F79009 | Alerta |
| `--color-error` | #D92D20 | Erro / destrutivo |

> ⚠️ `--color-success`, `--color-warning` e `--color-error` são **reservados**
> para feedback semântico. Nunca use para fins decorativos ou de categorização.

### 2.2 Tipografia

| Token | Valor |
|-------|-------|
| `--font-family` | <Inter / Roboto / fonte da referência> |
| `--font-size-base` | 14px |
| `--font-size-min` | 12px |
| `--type-scale` | 32 → 24 → 18 → 16 → 14 → 12 |

### 2.3 Espaçamento e Forma

| Token | Valor | Uso |
|-------|-------|-----|
| `--radius` | <px baseado no tom da marca> | Cards, botões, inputs — consistente em tudo |
| `--padding-card-sm` | 16px | Cards secundários |
| `--padding-card-md` | 20px | Cards padrão |
| `--padding-card-lg` | 24px | Cards de destaque / full-width |
| `--height-control` | 40px | Inputs e botões — sempre iguais |
| `--shadow` | `0 4px 16px rgba(0,0,0,0.06)` | Sombra padrão — nunca colorida |

### 2.4 Hierarquia de Botões

| Tipo | Estilo |
|------|--------|
| Primário | `background: var(--color-brand)` + texto branco |
| Secundário | `border: 1px solid var(--color-brand)` + texto brand, sem fill |
| Terciário | Apenas texto, sem borda, sem fill |
| Destrutivo | Mesmo padrão hierárquico, cor substituída por `var(--color-error)` |

---

## 3. Padrões de Navegação

| Decisão | Valor |
|---------|-------|
| Estrutura principal | <sidebar / top bar — justificar> |
| Navegação mobile | <bottom bar / hamburger — justificar> |
| Itens do menu principal | <listar — somente rotina operacional> |
| Itens secundários (avatar/kebab) | <config, perfil, plano, integrações> |
| CTA principal no menu | <ação + posição> |
| Busca global Cmd+K | <sim/não — justificar> |
| Item ativo | <estilo de indicação> |

---

## 4. Padrões de Dados

> *(Seção incluída somente se `tem_listagem_dados = sim`)*

| Decisão | Valor |
|---------|-------|
| Visualização padrão | <tabela / cards — justificar> |
| Comportamento ao clicar | <popup / drawer / página — baseado no volume> |
| Ações rápidas na linha | <listar ações do objeto> |
| Estado vazio | <descrição: ilustração + texto + CTA> |
| Paginação | <sim, a partir de N itens> |
| Confirmação de exclusão | <popup com implicações / desfazer em Xs> |

---

## 5. Regras VibeUX Aplicadas

> Somente as regras relevantes para este projeto, com nota de aplicação contextualizada.

### 5.1 Interface e Visual
*(referência: `references/cat1-interface-visual.md`)*

- **[1.X] <Nome da regra>** — <nota contextualizada para este projeto>

### 5.X <Categoria relevante>
*(referência: `references/catX-<nome>.md`)*

- **[X.X] <Nome da regra>** — <nota contextualizada>

---

## 6. Regras Explicitamente Não Aplicadas

> Categorias ou regras de alta relevância geral que foram descartadas neste projeto.

| Regra | Motivo |
|-------|--------|
| [X.X] <Nome> | <motivo específico deste projeto> |

---

## 7. Instruções para Agentes de IA

> Esta seção é escrita diretamente para agentes que irão implementar a interface.
> Leia antes de gerar qualquer tela, componente ou fluxo deste projeto.

### Tokens obrigatórios
Use **exclusivamente** os valores da Seção 2. Nunca use valores hardcoded de cor,
espaçamento ou tipografia sem referência ao token correspondente.

### Proibições absolutas
- ❌ Gradientes (em qualquer elemento)
- ❌ Emojis na interface (use SVG icons: Lucide, Heroicons ou Phosphor)
- ❌ Sombras com opacidade acima de 12%
- ❌ Gráfico de pizza (use barras horizontais ou verticais)
- ❌ `width: 100%` em botões dentro de formulários largos (700px+)
- ❌ Inputs e botões com alturas diferentes

### Regras de comportamento
- Formulários com mais de 4 campos: dividir em etapas com objetivo claro por etapa
- Listas com potencial de >20 itens: implementar paginação obrigatoriamente
- Exclusão de qualquer objeto: modal de confirmação com texto descritivo das implicações
- Exclusão crítica (irrecuperável): exigir digitação do nome ou frase de confirmação
- Erros de backend: nunca deixar interface silenciosa — mensagem clara + sugestão de ação
- Imagens: sempre exportar em `.webp` comprimido


---

## Comportamento esperado do agente

- Classifique primeiro se o projeto é **novo** ou **já iniciado**.
- Em projetos novos, consulte **sempre** Briefing, PRD e Specs antes de gerar o design doc.
- Em projetos já iniciados, consulte Briefing, PRD, Specs e também o **code base existente** antes de gerar recomendações.
- Ao analisar code base existente, diferencie o que deve ser preservado, ajustado ou refatorado.
- Carregue **somente** os arquivos de referência das categorias relevantes (Passo 3).
  Não leia arquivos desnecessários — mantenha o contexto enxuto.
- As notas de aplicação nas regras devem ser **diretivas** ("use X", "implemente Y"),
  nunca sugestivas ("considere X", "pode ser Y").
- Se a referência visual contradisser uma regra VibeUX, sinalize o conflito no documento
  e recomende o caminho VibeUX. Não silencie divergências.
- Ao terminar, salve em `/mnt/user-data/outputs/design_<nome-projeto>.md`
  e apresente com `present_files`.
