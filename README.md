# Dualpixel Agent Skills

Skills reutilizáveis para transformar uma ideia em uma entrega de software verificável.

## Compatibilidade

Estas skills são otimizadas para **Codex**. Em outra IDE, editor ou agente, peça primeiro ao agente responsável para auditar e adaptar cada skill ao formato de skills, ferramentas disponíveis, permissões, políticas de segurança e convenções daquele ambiente. Não assuma compatibilidade direta.

Skills de repositório orientam o trabalho; elas não concedem acesso ao workspace, a modelos, credenciais, APIs ou sistemas conectados.

## Antes de usar qualquer skill

1. Leia `AGENTS.md`, `README.md`, PRD, Spec e documentação de arquitetura que existirem no projeto.
2. Detecte a stack real pelos arquivos de configuração e lockfiles. Identifique runtime, framework, pacote/gerenciador de dependências, banco, autenticação, testes, CI e destino de deploy; não infira tecnologia sem evidência.
3. Confirme versões e convenções do repositório antes de recomendar APIs, comandos ou dependências.
4. Verifique se as skills e ferramentas necessárias estão instaladas. Quando faltar uma capacidade, descreva a lacuna e peça decisão; não simule uma ferramenta inexistente.
5. Para uma biblioteca, framework, SDK, API, CLI ou serviço de nuvem, consulte a documentação atual e oficial antes de alterar a integração.
6. Respeite as aprovações, o escopo e as regras locais. Não instale dependências, altere banco, publique, faça push ou exponha segredos sem a autorização apropriada.

## Fluxo recomendado

| Etapa | Skill | Resultado |
| --- | --- | --- |
| Definição | `prd-builder` | PRD aprovado: problema, usuários, escopo e regras de negócio. |
| Especificação | `spec-builder` | Spec técnica: stack validada, sprints e critérios verificáveis. |
| Interface | `vibeux-design` | Decisões de UI/UX contextualizadas pelo produto e codebase. |
| Execução | `workflow-builder` | Mapa de dependências, capacidades disponíveis e acompanhamento. |
| Segurança | `secure-code` | Revisão contínua de acesso, dados, validação e segredos. |

`secure-code` é transversal: use-o sempre que houver alteração de código, não apenas na etapa final.

## Instalação no Codex

Depois de escolher a skill, instale-a pelo mecanismo de skills do seu ambiente apontando para este repositório e informe o nome canônico da pasta. Exemplo de intenção: instalar `prd-builder` a partir de `dualpixel-digital/agent-skills`.

Confirme o comando de instalação na documentação do seu cliente Codex e verifique a skill instalada antes do primeiro uso; o formato de distribuição pode variar entre clientes e versões.

## Skills publicadas

- [`prd-builder`](./prd-builder/SKILL.md): requisitos de produto sem misturar detalhes de implementação.
- [`spec-builder`](./spec-builder/SKILL.md): especificação técnica a partir de um PRD aprovado.
- [`vibeux-design`](./vibeux-design/SKILL.md): guia de interface baseado em documentação, referência visual e codebase.
- [`workflow-builder`](./workflow-builder/SKILL.md): orquestração baseada em dependências e inventário de capacidades reais.
- [`secure-code`](./secure-code/SKILL.md): revisão defensiva para código, dados e integrações.

## Manutenção e contribuições

Abra uma proposta antes de alterar o contrato de uma skill. Mudanças devem preservar o nome canônico, revisar gatilhos de ativação, evitar instruções específicas de um cliente e validar o pacote em um workspace Codex limpo.

Reporte possíveis vulnerabilidades conforme [SECURITY.md](./SECURITY.md). As skills não substituem uma revisão humana, testes ou requisitos regulatórios do projeto.
