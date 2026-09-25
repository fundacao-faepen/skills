# Skills da Fundação FAEPEN para Codex

Este repositório reúne skills locais do Codex para tarefas recorrentes da Fundação FAEPEN. As skills ficam em `.agents/skills/`, o caminho de descoberta do repositório; ao abrir este repositório no Codex, elas ficam disponíveis também nos subdiretórios.

## Catálogo

| Skill | Uso |
| --- | --- |
| [`consultar-cpf-receita`](.agents/skills/consultar-cpf-receita/SKILL.md) | Consultar a situação cadastral de CPF no portal oficial da Receita Federal e registrar somente os dados minimizados. |
| [`post-aniversario`](.agents/skills/post-aniversario/SKILL.md) | Criar a arte de aniversário de colaborador para o feed do Instagram usando o modelo oficial da FAEPEN. |
| [`vaga-instagram`](.agents/skills/vaga-instagram/SKILL.md) | Criar artes de feed e story e a legenda para divulgar vagas de estágio da FAEPEN no Instagram. |

## Estrutura

```text
.agents/
└── skills/
    ├── consultar-cpf-receita/
    │   ├── .gitignore
    │   └── SKILL.md
    ├── post-aniversario/
    │   ├── SKILL.md
    │   ├── assets/
    │   └── scripts/
    └── vaga-instagram/
        ├── SKILL.md
        ├── assets/
        └── scripts/
```

Cada skill tem seu próprio `SKILL.md`. Arquivos de apoio, como `assets/` e `scripts/`, ficam junto da skill que os utiliza. Dados locais produzidos pela consulta de CPF são ignorados pelo Git conforme o `.gitignore` dessa skill.

## Adicionar uma skill

1. Crie `.agents/skills/<nome-da-skill>/SKILL.md`.
2. Use o mesmo nome da pasta no campo `name` do front matter YAML e escreva uma `description` clara sobre quando a skill deve ser usada.
3. Coloque scripts, referências e modelos necessários em subpastas da própria skill e indique no `SKILL.md` como utilizá-los.

Este repositório contém skills locais de projeto; não é um plugin e não inclui instalador. Para usá-las em outro repositório, instale ou copie as pastas escolhidas para a pasta de skills do usuário (`$HOME/.agents/skills/`).
