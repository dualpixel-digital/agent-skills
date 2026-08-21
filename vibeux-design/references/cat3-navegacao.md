# Cat 3 — Navegação (21 regras)

> Carregado por: `vibeux-design` SKILL.md — **sempre obrigatório**

---

**3.1 Home como Central de Controle**
A página inicial é a central de controle do usuário. Deve reunir:
- Atalhos para as principais ações
- Dados e insights mais relevantes
- Novidades e materiais educativos
O usuário nunca deve precisar "caçar" o que fazer.

**3.2 Menu principal: só o essencial**
Apenas ações da rotina operacional do usuário.
Ações esporádicas ficam no submenu do avatar: convidar equipe, mudar perfil/email/senha,
configurar notificações, gerenciar assinatura, solicitar suporte.

**3.3 Busca global (Cmd+K / Ctrl+K)**
Para produtos complexos: implemente busca global tipo Stripe ou Spotlight do macOS.
Permite que usuários avançados naveguem rapidamente sem depender do menu.

**3.4 Menu lateral para 4+ itens**
Sidebar é ideal para 4 ou mais itens de navegação.
Vantagens: espaço vertical para crescer, agrupamentos, subitens, sempre visível.

**3.5 Menu superior para até 4 itens**
Top bar funciona melhor com 4 ou menos itens.
Mais limpo, ocupa menos espaço, deixa largura total disponível para o conteúdo.

**3.6 Mobile: até 4 itens na navegação**
Em telas pequenas, limite de 4 itens visíveis.
Se precisar de mais: agrupe sob botão "Mais". Labels legíveis, ícones acessíveis.

**3.7 Separe por uso rotineiro vs. eventual**
Itens de uso diário: topo do menu, sempre visíveis.
Itens de uso eventual (config, integrações, plano): seção separada no final ou submenu.

**3.8 Agrupe em seções e submenus**
Com muitos itens, divida em seções lógicas com títulos claros ou submenus colapsáveis.
Usuário processa 3 grupos organizados, não 12 itens soltos.

**3.9 Posição comunica importância**
Menu superior: principal à esquerda, secundário à direita.
Sidebar: prioritário no topo, secundário no final.
Separação espacial ajuda o usuário a hierarquizar visualmente.

**3.10 Ações eventuais em submenu oculto**
Exportar dados, gerenciar integrações, alterar plano → no kebab (⋯) ou no avatar.
Acessível, mas sem poluir a navegação principal.

**3.11 Indique claramente o item ativo**
Indicadores visuais no item ativo: cor de destaque + fundo diferenciado + barra lateral colorida.
Nunca deixe todos os itens do menu com a mesma aparência.

**3.12 Ordem do menu: processo ou frequência**
Por ordem do processo: Cadastrar → Configurar → Executar → Analisar.
Por frequência: mais usado primeiro.
Escolha um critério e mantenha consistência em todo o produto.

**3.13 CTA principal direto no menu**
Se existe uma ação que o usuário faz com muita frequência ("Criar novo projeto", "Nova tarefa"),
inclua botão de ação direto no menu. Elimina cliques extras.

**3.14 Menu mobile: bottom bar ou hamburger**
- Bottom bar: até 5 itens, mais acessível ao polegar
- Hamburger (à direita da top bar): menus complexos com muitas opções

**3.15 Poucas abas com conteúdo curto = seções**
2–3 abas com conteúdo curto → exiba como seções na mesma página com scroll.
Reduz cliques e entrega visão geral completa.

**3.16 Navegação constante entre abas = una tudo**
Se o usuário alterna constantemente entre abas para comparar informações,
o conteúdo deveria estar na mesma página. "Vai e volta" = sinal para consolidar.

**3.17 Ordem das abas = mesma lógica do menu**
Se o menu é ordenado por processo, as abas dentro de cada seção também seguem essa lógica.
Cria padrão mental previsível e consistente.

**3.18 Sempre defina uma aba padrão**
Toda página com abas deve ter uma selecionada por padrão ao carregar.
Nunca deixe o usuário chegar sem nenhuma aba ativa.
A aba padrão: a mais relevante ou a primeira do fluxo.

**3.19 Badges de pendência nas abas**
Se existe pendência em uma aba, indique com badge numérico ou ponto colorido.
Usuário vê o que precisa de atenção sem abrir cada aba para verificar.

**3.20 6+ abas = abas laterais ou submenu**
6 ou mais abas horizontais ficam apertadas e ilegíveis.
Use abas laterais (vertical tabs) ou submenu lateral.
Evita scroll horizontal e acomoda nomes longos.

**3.21 Separe ações do objeto vs. ações da aba**
Ações do objeto (salvar, excluir, arquivar): fora das abas, no nível da página (cabeçalho).
Ações específicas da aba (adicionar membro, novo comentário): dentro da aba.
Misturar os dois confunde o usuário.
