# AGENTS.md

## Objetivo do repositório

Este repositório centraliza as automações desenvolvidas no ecossistema Microsoft Power Platform, principalmente:

- agentes do Copilot Studio;
- fluxos do Power Automate;
- Solutions da Power Platform;
- scripts de apoio com PAC CLI;
- documentação técnica.

A ideia é reduzir o trabalho manual no Copilot Studio e Power Automate, permitindo manutenção, versionamento e evolução das automações pelo VS Code sempre que possível.

## Estrutura esperada

```text
power-platform-automation/
├── agents/
├── solutions/
├── scripts/
├── docs/
├── AGENTS.md
└── README.md
```

### `agents/`

Contém os agentes do Copilot Studio clonados com PAC CLI.

Cada agente deve permanecer o mais próximo possível da estrutura original gerada pela Microsoft.

Exemplo:

```text
agents/
└── agente-gtgp/
    └── Agente - GT GP/
        ├── agent.mcs.yml
        ├── actions/
        ├── topics/
        ├── workflows/
        ├── connectionreferences.mcs.yml
        └── settings.mcs.yml
```

### `solutions/`

Contém Solutions usadas para versionar fluxos do Power Automate e outros componentes Power Platform que não pertencem diretamente a um agente.

As Solutions devem ser separadas por domínio ou finalidade, e não necessariamente uma por fluxo.

### `scripts/`

Scripts para automatizar tarefas repetitivas, como:

- atualizar agentes locais;
- clonar agentes;
- exportar ou sincronizar Solutions;
- validar alterações;
- facilitar uso do PAC CLI.

### `docs/`

Documentação de arquitetura, inventário, dependências e decisões importantes.

---

## Como o assistente deve trabalhar neste repositório

Ao realizar alterações:

1. Entender primeiro o componente existente antes de modificá-lo.
2. Preferir alterar arquivos locais em vez de instruir mudanças manuais na interface.
3. Preservar IDs, referências, conexões e contratos existentes quando não houver necessidade de alteração.
4. Não alterar componentes não relacionados à tarefa.
5. Não criar campos, tabelas, flows ou dependências extras sem necessidade.
6. Priorizar soluções simples, reutilizáveis e fáceis de manter.
7. Antes de executar `push`, `import`, `publish` ou qualquer operação que altere o ambiente remoto, mostrar claramente o que será alterado.
8. Usar Git para registrar alterações relevantes.
9. Nunca incluir senhas, tokens, secrets ou credenciais no repositório.
10. Quando uma tarefa puder ser automatizada por script ou PAC CLI, preferir isso ao processo manual de clicar e arrastar.

## Fluxo de trabalho recomendado

```text
Ambiente Microsoft
      ↓
PAC CLI
      ↓
Arquivos locais
      ↓
VS Code / agente de código
      ↓
Git / revisão
      ↓
PAC CLI
      ↓
Ambiente Microsoft
```

## Objetivo do assistente

O assistente deve ajudar principalmente a:

- analisar agentes e flows existentes;
- melhorar instruções e configurações;
- criar ou alterar ferramentas dos agentes;
- criar ou alterar fluxos do Power Automate;
- identificar problemas de configuração;
- gerar scripts para reduzir tarefas manuais;
- organizar o repositório;
- documentar componentes;
- revisar diferenças antes de sincronizar com o ambiente;
- orientar testes seguros antes de publicar alterações.

Sempre que possível, o assistente deve entregar mudanças prontas para uso em vez de apenas descrever passos manuais.
