# Cat 5 — Formulários e Fluxos Longos (9 regras)

> Carregado por: `vibeux-design` SKILL.md — quando `tem_formularios_longos = sim`

---

**5.1 Separe fluxos em etapas curtas**
Formulários longos assustam antes de começar.
Quebre em etapas curtas, cada uma com objetivo claro e formulário próprio.
O usuário sente progresso a cada passo — não enfrenta um bloco infinito de campos.

**5.2 Largura do formulário influencia a percepção de esforço**
Use a largura estrategicamente:
- Onboarding → formulário estreito (parece rápido e simples)
- Fluxo de cancelamento → formulário mais largo (cria percepção de que cancelar dá trabalho, ajuda na retenção)

**5.3 Altura do campo regula a expectativa de input**
- Campo fino → sugere resposta curta (nome, email)
- Campo alto → encoraja resposta mais completa (feedback, descrição)
Ajuste a altura ao volume de texto esperado.

**5.4 Tooltips em etapas que geram dúvidas**
Para campos com raciocínio mais complexo ou que possam gerar dúvidas:
adicione ícone "?" com tooltip explicativa ao lado do label.
Evita abandono do fluxo sem poluir a interface com texto permanente.

**5.5 Mostrar ou esconder progresso depende da prioridade**
- Prioridade = transparência: mostre progresso (Etapa X de Y, barra com labels)
- Prioridade = conversão: esconda o progresso — usuário não sabe quantas etapas faltam
  e tende a continuar sem desistir por achar que "falta muito"

**5.6 Nomeie cada etapa pelo objetivo**
Ao indicar progresso, mostre o que cada etapa representa:
"Dados pessoais" → "Endereço" → "Pagamento" → "Confirmar"
Não apenas "50% completo" — isso não diz o que falta.

**5.7 Pré-visualização em tempo real**
Para fluxos de construção visual (site, card, landing page):
mostre preview em tempo real do resultado enquanto o usuário avança.
Usuário vê o progresso concreto do que está criando e se sente motivado a concluir.

**5.8 Etapa de revisão em fluxos críticos**
Em fluxos críticos ou irreversíveis (pagamento, envio de contrato, cadastro definitivo):
adicione etapa final de revisão com todos os dados preenchidos + link "Editar" em cada item.
Reduz arrependimento e chamados de suporte.

**5.9 Confirmação via canal externo**
Após pagamento, contrato ou agendamento: envie resumo por email, WhatsApp ou outro canal externo.
Reforça confiança, serve como comprovante e evita que o usuário volte ao app só para conferir.
Em fluxos de pagamento e contrato: praticamente obrigatório.
