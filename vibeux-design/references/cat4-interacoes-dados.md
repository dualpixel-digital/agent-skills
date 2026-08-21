# Cat 4 — Interações com Dados (17 regras)

> Carregado por: `vibeux-design` SKILL.md — quando `tem_listagem_dados = sim`

---

**4.1 Listagem mostra o essencial**
Tabela ou card de listagem exibe apenas o suficiente para identificar o item e decidir abrir.
Dados demais na visualização geral poluem a interface e dificultam leitura rápida.
Detalhes completos ficam na tela interna do objeto.

**4.2 Tabela como padrão, cards para apelo visual**
Tabela é mais densa, escaneável e eficiente — use como padrão.
Cards apenas quando o objeto tem apelo visual que ajuda na identificação:
produtos com fotos, posts com thumbnails, templates com previews.

**4.3 Ações rápidas na listagem**
Inclua ações padrão diretamente na visualização geral: duplicar, excluir, arquivar, postar.
Evita que o usuário abra cada item só para executar uma ação simples.

**4.4 Muitas ações = submenu oculto**
Quando o objeto tem muitas ações, filtre as 2–3 principais e agrupe o resto no kebab (⋯).
Interface limpa sem perder funcionalidade.

**4.5 Objetos complexos pedem abas ou seções**
Muitos dados e relações: use abas ou seções bem definidas.
Exemplos: "Dados gerais", "Histórico", "Configurações".
Nunca uma página infinita com tudo jogado junto.

**4.6 Clique proporcional ao volume de dados**
- 3–5 campos → abra popup/modal
- Volume intermediário → use drawer lateral (desliza pela lateral, mantém contexto)
- Muitos dados → abra página dedicada
Usar página inteira para 3 campos é desperdício. Usar popup para 20 campos é sufocante.

**4.7 Criação: popup primeiro, página depois**
Se o objeto tem muitos campos mas poucos obrigatórios para criar:
popup com mínimo (nome, tipo) → redirecionar para página completa após criação.
Reduz a fricção inicial sem sacrificar completude.

**4.8 Botão de criar = onde for mais visível**
Pode ficar no cabeçalho da página, no menu lateral, ou entre os cards.
O mais importante: visível e acessível no contexto onde o usuário mais precisa.

**4.9 Salvamento automático quando possível**
Salve automaticamente e exiba feedback sutil: "Salvo" ou "Salvando...".
Exceção: quando a edição tem efeitos colaterais externos (disparar emails, alterar integrações,
afetar outros usuários) — nesses casos, use botão explícito "Salvar alterações".

**4.10 Sempre confirme antes de excluir**
Popup de confirmação antes de excluir qualquer objeto.
O popup deve informar as implicações: "Isso removerá permanentemente o projeto e 12 tarefas associadas."
Nunca exclua direto no clique sem aviso.

**4.11 Exclusão crítica pede fricção extra**
Para exclusões irrecuperáveis (conta inteira, workspace, dados permanentes):
exija que o usuário digite o nome do objeto ou uma frase de confirmação.
Protege contra cliques acidentais em ações irreversíveis.

**4.12 Objetos simples dispensam confirmação**
Se o objeto é fácil de recriar e não é crítico (rascunho, tag, filtro salvo):
exclua diretamente e ofereça "Desfazer" por 5–10 segundos via toast.

**4.13 Permita desfazer exclusões**
Opções de implementação:
- Toast "Item excluído" + botão "Desfazer" que desaparece em 5–10s
- Lixeira onde itens excluídos ficam disponíveis por período definido (ex: 30 dias)

**4.14 Cuidado com textos ambíguos nos botões**
Em popups de confirmação, nunca use "Cancelar/Confirmar" genérico.
Se a ação é "Cancelar campanha", use: "Voltar" e "Sim, cancelar campanha".
O usuário precisa saber exatamente o que cada botão faz.

**4.15 Estado vazio = orientação**
Nunca mostre apenas tabela vazia.
No estado vazio: ilustração + texto explicativo + CTA principal ("Crie seu primeiro projeto").
Transforme o vazio em oportunidade de onboarding.
