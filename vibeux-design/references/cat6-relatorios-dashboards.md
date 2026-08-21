# Cat 6 — Relatórios e Dashboards (14 regras)

> Carregado por: `vibeux-design` SKILL.md — quando `tem_dashboard = sim`

---

**6.1 Dashboards baseados em dados reais dos usuários**
Não presuma quais métricas importam — entreviste os usuários.
O dashboard é um organismo vivo: colete feedbacks contínuos e itere.

**6.2 Hierarquia de apresentação**
A posição comunica importância. Siga a ordem:
1. KPIs (topo à esquerda)
2. Gráficos simples
3. Gráficos complexos
4. Tabelas e listas detalhadas

**6.3 Nunca use gráfico de pizza**
Humanos têm dificuldade em comparar ângulos e áreas — comprovado por estudos.
Use gráfico de barras: comparação imediata e precisa dos mesmos dados.

**6.4 Linha para contínuos, barras para discretos**
- Dados contínuos (receita ao longo do tempo, evolução de acessos) → gráfico de linha
- Dados discretos (vendas por plano, tickets por categoria) → gráfico de barras

**6.5 Eixo X com labels longos = barras horizontais**
Rótulos longos no eixo X ficam ilegíveis (sobrepostos ou rotacionados).
Solução: inverta os eixos e use barras horizontais — textos legíveis à esquerda.

**6.6 Poucos pontos = remova eixo Y e use labels diretas**
Com até 12 pontos, o eixo Y é desnecessário.
Remova o eixo Y e coloque os valores diretamente sobre cada barra ou ponto.
Reduz ruído visual e facilita leitura imediata.

**6.7 Regra dos 3 segundos**
Se o usuário precisa de mais de 3 segundos para entender o gráfico, está complexo demais.
Evite: 2 eixos Y, muitas categorias sobrepostas, escala logarítmica.
Simplifique ou quebre em gráficos menores.

**6.8 Destaque uma série com cor, cinza nas demais**
Para chamar atenção para uma curva específica:
aplique cinza neutro em todas as séries secundárias + cor de destaque apenas na que importa.
O olho vai direto para a série destacada.

**6.9 Design e consistência visual nos gráficos**
Gráficos devem parecer parte do produto, não elementos genéricos colados.
Use: mesma fonte do software, mínimo 12–14px nos labels, cor primária do produto no destaque.

**6.10 Vermelho, laranja e verde são cores reservadas**
- Verde (`#039855`) = positivo / OK / meta atingida
- Laranja (`#F79009`) = alerta / atenção / próximo do limite
- Vermelho (`#D92D20`) = negativo / erro / meta não atingida
Nunca use essas cores para fins decorativos ou de categorização nos gráficos.

**6.11 KPIs sempre com referência de comparação**
Um número isolado não diz nada.
Sempre acompanhe o KPI de: benchmark da indústria, período anterior ou média de longo prazo.
Permite que o usuário saiba instantaneamente se o valor é bom, ruim ou dentro do esperado.

**6.12 Cores e ícones para leitura rápida**
Use setas ↑↓, badges coloridos e indicadores visuais nos KPIs.
Usuário escaneia o cenário em segundos sem precisar ler cada número.

**6.13 Filtros de período práticos**
Ofereça atalhos prontos além do date picker genérico:
"Esta semana" | "Semana passada" | "Este mês" | "Últimos 30 dias" | "Personalizado"

**6.14 Métricas de valor agregado**
Exiba KPIs que mostram o impacto concreto do produto na operação do usuário:
"Tempo economizado", "Custo reduzido", "Faturamento adicionado".
Quando o usuário enxerga o impacto, cancelar se torna muito mais difícil.
