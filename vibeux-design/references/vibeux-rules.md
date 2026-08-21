# VibeUX Rules Reference

> 101 regras práticas de UX para SaaS, organizadas em 8 categorias.
> Este arquivo é consultado pela skill vibeux-design para filtrar regras relevantes por projeto.

---

## Categoria 1 — Interface e Visual (15 regras)

**1.1 Light e Dark Mode**
Ofereça os dois modos. O padrão deve seguir `prefers-color-scheme` do sistema operacional.

**1.2 Paleta de cores harmônica**
Use tokens fixos: bg `#F9FAFB`, surface `#FFFFFF`, text `#1D2939`, muted `#667085`,
divider `#EAECF0`, border `#D0D5DD`, success `#039855`, warning `#F79009`, error `#D92D20`.

**1.3 Nunca use emojis na interface**
Use sempre ícones vetoriais SVG (Lucide, Heroicons, Phosphor). Emojis variam entre sistemas.

**1.4 Paddings proporcionais em cards**
Entre 16px e 24px. Quanto mais importante o card, maior o padding. Evitar 40px+.

**1.5 Sombras sempre suaves e neutras**
`rgba(0,0,0,0.06)`. Nunca coloridas. Opacidade entre 5% e 12%.

**1.6 Nunca use gradientes**
Estilo totalmente flat. Nada de gradientes em botões, fundos, fontes ou divisores.

**1.7 Tamanho mínimo de fonte: 12px**
Texto padrão: 14px. Mínimo absoluto: 12px (apenas rodapés/labels secundários).

**1.8 Escala tipográfica progressiva**
32 → 24 → 18 → 16 → 14. Sem saltos bruscos entre tamanhos vizinhos.

**1.9 Prefira fontes sem serifa**
Inter (primeira escolha), Roboto, Manrope, Segoe UI, Helvetica Neue.

**1.10 Alinhamento homogêneo**
Todos os elementos seguem a mesma lógica de alinhamento. Nunca misture sem propósito.

**1.11 Não estique botões desnecessariamente**
Em formulários largos (700-1000px), largura máxima do botão: 400-500px. Não use `width: 100%`.

**1.12 Hierarquia visual de botões**
Primário: cor brand + texto branco. Secundário: outline. Terciário: só texto. Destrutivo: vermelho.

**1.13 Raio de borda consistente**
Moderno/descolado: ~20px. Neutro/corporativo: 8px. Enterprise/robusto: 0-2px. Escolha um e mantenha.

**1.14 Botões e inputs com mesma altura**
40px para ambos. Sempre. Garante harmonia em formulários.

**1.15 Text areas com altura proporcional**
Altura reflete o volume de texto esperado. Campo de nome: fino. Campo de descrição: 5-6 linhas.

---

## Categoria 2 — Acesso e Onboarding (16 regras)

**2.1 Tela de login mostra novidades**
Use a coluna lateral para comunicar features novas e lançamentos.

**2.2 Redirecione ao destino correto após login**
Salve a URL de destino e redirecione após autenticação. Nunca jogue no dashboard genérico.

**2.3 Tela de cadastro vende o produto**
Use o espaço restante para screenshots, depoimentos e benefícios enquanto o usuário preenche.

**2.4 Cadastro em etapas, mínimo primeiro**
Etapa 1: só email + senha. Dados adicionais nas etapas seguintes.

**2.5 Use máscaras em campos de formulário**
Telefone, CPF, CNPJ, CEP, cartão — formatar automaticamente enquanto o usuário digita.

**2.6 Ofereça login social**
Google é quase obrigatório em B2B. GitHub, Microsoft ou Apple dependendo do nicho. Mantenha fallback email/senha.

**2.7 Não peça confirmação de senha**
Um campo + botão mostrar/ocultar. Campo duplicado é fricção desnecessária.

**2.8 Sugira upgrade ao escolher plano barato**
Popup leve com 2-3 benefícios concretos do plano superior + diferença de preço.

**2.9 Onboarding em formato wizard**
Passo a passo com barra de progresso. Objetivo: levar ao Aha Moment o mais rápido possível.

**2.10 Pré-popule campos e peça apenas revisão**
Deduza informações e preencha automaticamente. Usuário só confirma.

**2.11 Missões com progresso e recompensas**
Checklist de ações iniciais com recompensas concretas (dias de trial, créditos).

**2.12 Dados fictícios para acelerar o Aha Moment**
Popule com dados demo realistas para que o usuário veja a ferramenta funcionando imediatamente.

**2.13 Gamificação para retenção**
Identifique comportamentos que reduzem churn e crie sistema de pontos/medalhas/níveis.

**2.14 Vídeos demonstrativos curtos (30s a 2min)**
Por funcionalidade importante. Embutido próximo à feature, não na central de ajuda.

**2.15 Vídeos com rosto humano**
Webcam visível nos screencasts. Cria conexão e reduz churn nos primeiros dias.

**2.16 Sequências de mensagens educativas**
Automatize emails/in-app: Dia 1 boas-vindas, Dia 3 integração, Dia 7 dica avançada, Dia 14 features ocultas.

---

## Categoria 3 — Navegação (21 regras)

**3.1 Home como Central de Controle**
Atalhos para ações principais + dados relevantes + novidades. Nunca deixe a home vazia.

**3.2 Menu principal: só o essencial**
Apenas ações da rotina operacional. Config/perfil/plano ficam no submenu do avatar.

**3.3 Busca global (Cmd+K / Ctrl+K)**
Para produtos complexos. Permite navegação avançada sem depender do menu.

**3.4 Menu lateral para 4+ itens**
Sidebar oferece espaço vertical, agrupamentos e subitens sempre visíveis.

**3.5 Menu superior para até 4 itens**
Top bar mais limpa para produtos simples ou navegação enxuta.

**3.6 Mobile: até 4 itens na navegação**
Mais que isso: agrupe sob "Mais". Labels legíveis e ícones acessíveis.

**3.7 Separe por uso rotineiro vs. eventual**
Rotineiro no topo/visível. Eventual (config, integrações, plano) em seção separada.

**3.8 Agrupe em seções e submenus**
Títulos de seção ou submenus colapsáveis. Usuário vê grupos, não lista corrida.

**3.9 Posição comunica importância**
Menu superior: principal à esquerda, secundário à direita. Sidebar: prioritário no topo.

**3.10 Ações eventuais em submenu oculto**
Kebab (⋯) ou menu do avatar para exportar dados, gerenciar integrações, alterar plano.

**3.11 Indique claramente o item ativo**
Cor de destaque + fundo diferenciado ou barra lateral colorida. Nunca todos iguais.

**3.12 Ordem do menu: processo ou frequência**
Por ordem do processo (Cadastrar → Configurar → Executar → Analisar) OU por frequência. Mantenha consistência.

**3.13 CTA principal direto no menu**
Ação mais frequente como botão no menu. Elimina cliques extras.

**3.14 Menu mobile: bottom bar ou hamburger**
Bottom bar para até 5 itens. Hamburger (à direita) para menus complexos.

**3.15 Poucas abas com conteúdo curto = seções**
2-3 abas com conteúdo curto → exiba como seções na mesma página com scroll.

**3.16 Navegação constante entre abas = una tudo**
"Vai e volta" entre abas é sinal de que o conteúdo deve estar na mesma página.

**3.17 Ordem das abas = mesma lógica do menu**
Consistência entre menu e abas cria padrão mental previsível.

**3.18 Sempre defina uma aba padrão**
Nunca deixe o usuário chegar em página sem aba ativa. A mais relevante ou a primeira.

**3.19 Badges de pendência nas abas**
Números ou pontos coloridos indicam atenção necessária sem abrir a aba.

**3.20 6+ abas = abas laterais ou submenu**
Evita scroll horizontal. Acomoda nomes longos e facilita legibilidade.

**3.21 Separe ações do objeto vs. ações da aba**
Salvar/excluir/arquivar ficam no nível da página. Adicionar membro/novo comentário ficam dentro da aba.

---

## Categoria 4 — Interações com Dados (17 regras)

**4.1 Listagem mostra o essencial**
Apenas o suficiente para identificar e decidir abrir. Detalhes ficam na tela interna.

**4.2 Tabela como padrão, cards para apelo visual**
Tabela é mais densa e escaneável. Cards apenas quando há imagens/previews que ajudam na identificação.

**4.3 Ações rápidas na listagem**
Duplicar, excluir, arquivar, postar — ações direto na linha. Evita abrir cada item.

**4.4 Muitas ações = submenu oculto**
Filtre 2-3 principais e agrupe o resto no kebab (⋯).

**4.5 Objetos complexos pedem abas ou seções**
"Dados gerais", "Histórico", "Configurações". Nunca uma página infinita com tudo.

**4.6 Clique proporcional ao volume de dados**
3-5 campos → popup. Volume médio → drawer lateral. Muitos dados → página dedicada.

**4.7 Criação: popup primeiro, página depois**
Popup com campos obrigatórios mínimos → redirecionar para página completa após criar.

**4.8 Botão de criar = onde for mais visível**
No cabeçalho da página, no menu lateral ou entre os cards. Visível no contexto de uso.

**4.9 Salvamento automático quando possível**
Feedback sutil "Salvo" ou "Salvando...". Exceção: quando edição tem efeitos colaterais externos.

**4.10 Sempre confirme antes de excluir**
Popup com implicações claras: "Isso removerá permanentemente o projeto e 12 tarefas associadas."

**4.11 Exclusão crítica pede fricção extra**
Digitação do nome do objeto ou frase de confirmação para exclusões irrecuperáveis.

**4.12 Objetos simples dispensam confirmação**
Rascunhos, tags, filtros → excluir direto + oferecer desfazer por 5-10 segundos.

**4.13 Permita desfazer exclusões**
Toast "Item excluído" + botão "Desfazer" por 5-10s, ou lixeira com retenção de 30 dias.

**4.14 Cuidado com textos ambíguos nos botões**
Use "Voltar" e "Sim, cancelar campanha" — nunca "Cancelar/Confirmar" genérico.

**4.15 Estado vazio = orientação**
Ilustração + texto explicativo + CTA principal ("Crie seu primeiro projeto"). Nunca tabela vazia.

---

## Categoria 5 — Formulários e Fluxos Longos (9 regras)

**5.1 Separe fluxos em etapas curtas**
Cada etapa com objetivo claro. Usuário sente progresso a cada passo.

**5.2 Largura do formulário influencia a percepção**
Onboarding: estreito (parece rápido). Cancelamento: largo (parece trabalhoso).

**5.3 Altura do campo regula a expectativa**
Campo fino → resposta curta. Campo alto → encoraja resposta longa.

**5.4 Tooltips em etapas que geram dúvidas**
Ícone "?" ao lado do label. Evita abandono sem poluir a interface com texto permanente.

**5.5 Mostrar ou esconder progresso depende da prioridade**
Transparência: mostre etapas e percentual. Conversão: esconda para não deixar usuário desistir.

**5.6 Nomeie cada etapa pelo objetivo**
"Dados pessoais", "Endereço", "Pagamento" — não apenas "50% completo".

**5.7 Pré-visualização em tempo real**
Para fluxos de construção visual (site, card, landing page): mostre preview enquanto o usuário avança.

**5.8 Etapa de revisão em fluxos críticos**
Antes de confirmar pagamento/contrato: tela de revisão com "Editar" ao lado de cada dado.

**5.9 Confirmação via canal externo**
Email/WhatsApp com resumo após pagamento, contrato ou agendamento. Praticamente obrigatório.

---

## Categoria 6 — Relatórios e Dashboards (14 regras)

**6.1 Dashboards baseados em dados reais dos usuários**
Entreviste usuários. Colete feedback contínuo. Dashboard é um organismo vivo.

**6.2 Hierarquia de apresentação**
KPIs (topo esquerda) → gráficos simples → gráficos complexos → tabelas detalhadas.

**6.3 Nunca use gráfico de pizza**
Humanos são ruins em comparar ângulos. Use barras — sempre mais claro.

**6.4 Linha para contínuos, barras para discretos**
Receita ao longo do tempo → linha. Vendas por plano → barras.

**6.5 Eixo X com labels longos = barras horizontais**
Inverta os eixos quando os rótulos são nomes longos de cidades/categorias.

**6.6 Poucos pontos = remova eixo Y e use labels diretas**
Até 12 pontos: remova eixo Y e coloque valores diretamente sobre cada barra.

**6.7 Regra dos 3 segundos**
Se o usuário precisa de mais de 3s para entender, está complexo demais. Simplifique.

**6.8 Destaque uma série com cor, cinza nas demais**
Todas as séries em cinza, exceto a que importa. Foco imediato.

**6.9 Design e consistência visual nos gráficos**
Mesma fonte do produto, mínimo 12-14px nos labels, cor primária do produto no destaque.

**6.10 Vermelho, laranja e verde são cores reservadas**
Verde = OK. Laranja = alerta. Vermelho = erro. Nunca use para fins decorativos.

**6.11 KPIs sempre com referência de comparação**
Período anterior, benchmark da indústria ou média. Número isolado não diz nada.

**6.12 Cores e ícones para leitura rápida**
Setas ↑↓, badges coloridos, indicadores visuais. Usuário escaneia em segundos.

**6.13 Filtros de período práticos**
"Esta semana", "Semana passada", "Este mês", "Últimos 30 dias" + opção customizada.

**6.14 Métricas de valor agregado**
"Tempo economizado", "Custo reduzido", "Faturamento adicionado". Dificulta o churn.

---

## Categoria 7 — Erros e Alertas (5 regras)

**7.1 Validação em tempo real**
On blur ou on input — não só no submit. Campo a campo, não tudo junto no final.

**7.2 Checklist de regras visível**
Mostre as regras de preenchimento antes de o usuário digitar. Checklist com check verde em tempo real.

**7.3 Sempre avise erros de backend**
Nunca deixe interface silenciosa. Mensagem clara em linguagem simples + sugestão de ação.

**7.4 Abra o suporte proativamente em erros críticos**
Falha no pagamento/dados/integração → chat abre automaticamente com mensagem pré-preenchida.

**7.5 Corrija automaticamente quando possível**
Se a intenção é óbvia (domínio sem https://, espaços extras) → corrija silenciosamente em vez de bloquear.

---

## Categoria 8 — Performance (4 regras)

**8.1 Comprima imagens e use .webp**
.webp é significativamente mais leve que .png e .jpg mantendo qualidade.

**8.2 Pagine listas longas**
Mais de 20-30 itens → paginação obrigatória. Scroll infinito prejudica performance e navegação.

**8.3 Feedback visual em ações em massa**
Barra de progresso + contador ("142 de 300") + tempo estimado. Nunca apenas "Aguarde...".

**8.4 Skeleton Loading no lugar de spinners**
Formas cinzas que imitam o layout real. Reduz percepção de espera sem mudar o tempo real.
