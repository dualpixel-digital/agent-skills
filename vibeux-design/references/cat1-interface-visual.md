# Cat 1 — Interface e Visual (15 regras)

> Carregado por: `vibeux-design` SKILL.md — **sempre obrigatório**

---

**1.1 Light e Dark Mode**
Ofereça os dois modos. O padrão deve seguir `prefers-color-scheme` do sistema operacional.
Usuário que usa o sistema em dark mode deve entrar no app já no modo correto, sem configurar nada.

**1.2 Paleta de cores harmônica**
Tokens fixos do sistema:
- Fundo: `#F9FAFB` | Surface: `#FFFFFF` | Texto: `#1D2939` | Muted: `#667085`
- Divisores: `#EAECF0` | Bordas: `#D0D5DD`
- Sucesso: `#039855` | Alerta: `#F79009` | Erro: `#D92D20`
A cor brand é escolhida uma vez e mantida em todo o produto.

**1.3 Nunca use emojis na interface**
Use sempre ícones vetoriais SVG. Emojis variam entre sistemas operacionais (Android, iOS, Windows)
e quebram a consistência visual. Bibliotecas recomendadas: Lucide, Heroicons, Phosphor.

**1.4 Paddings proporcionais em cards**
Entre 16px e 24px. Quanto mais importante o card, maior o padding.
Cards full-width comportam paddings maiores. Evitar 40px+ (aparência de vazio).

**1.5 Sombras sempre suaves e neutras**
`box-shadow: 0 4px 16px rgba(0,0,0,0.06)`. Nunca coloridas.
Opacidade entre 5% e 12%: abaixo de 5% é invisível, acima de 12% é pesada demais.

**1.6 Nunca use gradientes**
Estilo totalmente flat. Nenhum gradiente em fontes, botões, sombras, backgrounds ou divisores.
Use cor sólida: `background: #FF7505` — nunca `linear-gradient(...)`.

**1.7 Tamanho mínimo de fonte: 12px**
Texto padrão da aplicação: 14px. Mínimo absoluto: 12px, apenas para rodapés ou labels muito secundários.

**1.8 Escala tipográfica progressiva**
A diferença entre tamanhos vizinhos deve ser gradual. Escala recomendada: 32 → 24 → 18 → 16 → 14 → 12.
Nunca pule de 32px direto para 14px.

**1.9 Prefira fontes sem serifa**
Ordem de preferência: Inter (gratuita, universal) → Roboto → Manrope → Segoe UI → Helvetica Neue.
Na dúvida, use Inter.

**1.10 Alinhamento homogêneo**
Todos os elementos na tela seguem a mesma lógica de alinhamento.
Se título e inputs estão à esquerda, o botão também fica à esquerda. Nunca misture sem propósito.

**1.11 Não estique botões desnecessariamente**
Em formulários de 700–1000px de largura, nunca use `width: 100%` no botão.
Largura máxima ideal: 400–500px. Em formulários largos, alinhe o botão à direita.

**1.12 Hierarquia visual de botões**
- Primário (salvar, confirmar): `background: var(--color-brand)` + texto branco
- Secundário (cancelar): apenas border + texto brand, sem fill
- Terciário (voltar, pular): apenas texto, sem borda
- Destrutivo (excluir, remover): mesma hierarquia, cor substituída por `var(--color-error)`

**1.13 Raio de borda consistente**
Escolha um valor e mantenha em **todos** os elementos do produto:
- Moderno/descolado: ~20px | Neutro/corporativo: 8px | Enterprise/robusto: 0–2px

**1.14 Botões e inputs com mesma altura**
Sempre 40px para ambos. Garante harmonia quando estão lado a lado em formulários.

**1.15 Text areas com altura proporcional**
A altura inicial do textarea reflete o volume de texto esperado:
- Campo de slogan: ~2 linhas | Campo de descrição/público-alvo: ~5–6 linhas
- Use auto-resize que acompanha o conteúdo enquanto o usuário digita.
