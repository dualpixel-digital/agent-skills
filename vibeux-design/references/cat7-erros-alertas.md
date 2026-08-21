# Cat 7 — Erros e Alertas (5 regras)

> Carregado por: `vibeux-design` SKILL.md — **sempre obrigatório**

---

**7.1 Validação em tempo real**
Não valide campos somente após o clique no botão de envio.
Prefira validação on blur (ao sair do campo) ou on input (enquanto digita).
O usuário corrige erros imediatamente — não descobre vários problemas juntos no final.
Campos que se beneficiam mais: email, telefone, senha.

**7.2 Checklist de regras visível**
Para campos com regras de preenchimento (tamanho mínimo, caracteres especiais):
- Mostre as regras antes do usuário começar a digitar
- Use checklist com check verde ao lado de cada regra atendida
- Atualize em tempo real conforme o usuário preenche
Transforma a validação em guia interativo em vez de barreira.

**7.3 Sempre avise erros de backend**
Quando ocorre erro no servidor, nunca deixe a interface silenciosa.
O usuário sem feedback acha que a ação foi concluída, ou que o sistema travou.
Exiba mensagem clara em linguagem simples (nada de "Error 500").
Se possível, sugira ação: "Tente novamente" ou "Entre em contato com o suporte".

**7.4 Abra o suporte proativamente em erros críticos**
Para erros críticos (falha no pagamento, perda de dados, integração quebrada):
não espere o usuário procurar o suporte — abra o chat proativamente com mensagem pré-preenchida
descrevendo o problema (código do erro, contexto). O usuário só precisa clicar em "Enviar".
Reduz fricção, mostra cuidado, acelera resolução.

**7.5 Corrija automaticamente quando possível**
Se a intenção do usuário é óbvia, corrija em vez de bloquear:
- Adicionar `https://` quando o usuário digita só o domínio
- Formatar telefone com máscara
- Remover espaços extras no início/fim
Regra: se você sabe o que o usuário quis dizer, resolva para ele.
