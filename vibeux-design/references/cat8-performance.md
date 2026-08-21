# Cat 8 — Performance (4 regras)

> Carregado por: `vibeux-design` SKILL.md — **sempre obrigatório**

---

**8.1 Comprima imagens e use .webp**
Sempre comprima imagens antes de servir.
Formato ideal: `.webp` — significativamente mais leve que `.png` e `.jpg` com mesma qualidade visual.
Imagens pesadas deixam a interface lenta e o usuário percebe instantaneamente.
Uma página que carrega rápido transmite profissionalismo e confiança.

**8.2 Pagine listas longas**
Listas com potencial de mais de 20–30 itens: paginar obrigatoriamente.
Carregar tudo de uma vez prejudica performance (navegador renderiza centenas de elementos)
e prejudica navegação (usuário se perde em scroll infinito).
Paginação organiza a informação e mantém a interface rápida e controlável.

**8.3 Feedback visual em ações em massa**
Quando o sistema executa ações em massa (excluir, editar, importar centenas de itens):
exiba barra de progresso + contador ("142 de 300 processados") + tempo estimado.
Nunca exiba apenas "Aguarde..." — o usuário não sabe se a ação está rodando, travou ou terminou.

**8.4 Skeleton Loading no lugar de spinners**
Em vez de spinner genérico: use Skeleton Loading (formas cinzas que imitam o layout real).
O cérebro começa a processar a estrutura da página antes do conteúdo aparecer.
O usuário sente a interface mais rápida — mesmo que o tempo real de carregamento seja igual.
