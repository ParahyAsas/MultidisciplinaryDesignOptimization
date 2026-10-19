# Contribuindo com o Multidisciplinary Design Optimization

Este documento define as convenções que mantêm o repositório organizado.

## Idioma

- **Commits, branches e comentários de código:** inglês.
- **Descrições de commits/PRs, issues e documentação:** português.

## Reportando dúvidas e problemas

Use as **Issues** do GitHub para dúvidas, bugs e sugestões, com os seguintes labels:

- `duvida` — perguntas sobre o código, método ou organização
- `bug` — comportamento incorreto
- `melhoria` — sugestões de melhoria ou novas funcionalidades

Antes de abrir uma issue, verifique se já existe uma semelhante.

## Fluxo de trabalho (Git Flow)

O repositório utiliza o Git Flow com as seguintes branches:

| Branch      | Função                                         |
| ----------- | ---------------------------------------------- |
| `main`      | Versão estável; nunca recebe commits diretos   |
| `develop`   | Integração do trabalho corrente                |
| `feature/*` | Desenvolvimento de uma funcionalidade          |
| `fix/*`     | Correção de bugs                               |
| `docs/*`    | Alterações apenas em documentação              |

### Regras

1. Nunca faça commits diretos em `main` ou `develop`.
2. Crie uma branch a partir de `develop`:
   ```bash
   git checkout develop
   git pull origin develop
   git checkout -b feature/nome-curto-da-feature
   ```
3. Abra um Pull Request de `feature/*` (ou `fix/*`, `docs/*`) → `develop`.
4. Pull Requests de `develop` → `main` são feitos ao final de cada etapa/entrega.
5. Mantenha a branch atualizada com `develop` antes de abrir o PR:
   ```bash
   git fetch origin
   git rebase origin/develop
   ```

### Nomes de branches

Formato: `tipo/nome-curto-em-kebab-case` (em inglês):

- `feature/calculo-de-arrasto`
- `fix/unidade-da-massa`
- `docs/tabela-de-resultados`

## Convenção de commits

Utilizamos [Conventional Commits](https://www.conventionalcommits.org/):

```
<tipo>(<escopo>): <descrição curta em português>
```

**Tipos disponíveis:**

| Tipo       | Quando usar                                          |
| ---------- | ---------------------------------------------------- |
| `feat`     | Nova funcionalidade ou cálculo                        |
| `fix`      | Correção de bug                                       |
| `refactor` | Reestruturação sem mudar comportamento               |
| `perf`     | Mudança com foco exclusivo em desempenho              |
| `test`     | Adição ou correção de testes                          |
| `docs`     | Apenas documentação (README, relatórios, comentários) |
| `chore`    | Tarefas de manutenção (configuração, dependências)   |

**Escopo (opcional):** use o componente afetado — `otimizacao`, `modelo`, `scripts`, `analysis`, ou a sigla da ferramenta quando aplicável.

**Exemplos:**

```
feat(otimizacao): adiciona calculo do arrasto induzido
fix(modelo): corrige unidade da massa na otimizacao
docs: inclui tabela de resultados do estudo de caso
chore: configura ambiente com poetry
```

Commits devem ser atômicos: uma ideia por commit, mensagens na imperativa ("adiciona", não "adicionado" ou "adicionei").

## Pull Requests e Code Review

### Ao abrir um PR

- **Título:** mesmo padrão dos commits (ex.: `feat(otimizacao): adiciona calculo do arrasto induzido`).
- **Descrição:**
  - **O que foi feito:** resumo das alterações e a motivação.
  - **Como testar:** passos para reproduzir e verificar localmente.
  - **Issue relacionada (se houver):** `Closes #<número>`.
- Preencha a checklist do PR:
  - [ ] Branch atualizada com `develop` (rebase feito)
  - [ ] Commits seguem a convenção
  - [ ] Sem arquivos grandes de dados ou artefatos desnecessários
  - [ ] Nenhum teste existente quebrou

### Critérios antes de abrir o PR

- O código roda localmente sem erros e o resultado esperado é verificado.
- A lógica está consistente com as demais partes do projeto (mesmas unidades, mesmas convenções numéricas).
- Nenhum arquivo temporário, cache ou dado bruto grande é commitado.

### Ao revisar

- Ao menos **1 aprovação** é necessária antes do merge.
- Revise: correção lógica, legibilidade, aderência às convenções e se o "como testar" funciona.
- Comente de forma construtiva e seja específico (arquivo/linha).

## Testes

- Rode os testes **antes** de abrir um PR e comente no PR como os executou.
- Quem revisa deve verificar se os testes passam localmente antes de aprovar.
- ⚠️ **Pendente:** a ferramenta de testes e o comando exato serão definidos assim que a estrutura do projeto anterior for avaliada.

## Resumo dos fluxos

| Tipo de atividade | Onde trabalha | Branch          | PR para    |
| ----------------- | ------------- | --------------- | ---------- |
| Funcionalidade    | código-fonte   | `feature/<nome>` | `develop`  |
| Correção          | qualquer      | `fix/<nome>`    | `develop`  |
| Documentação      | docs/README   | `docs/<nome>`   | `develop`  |
| Entrega/etapa     | —             | `develop`       | `main`     |

## A definir (pendentes)

As seções abaixo serão complementadas após avaliar como o projeto anterior estava implementado:

- **Estrutura de pastas e arquivos** — onde colocar código, dados, figuras e relatórios (com tabela de nomenclatura de arquivos).
- **Ambiente e dependências** — como instalar e rodar o projeto (versão de Python, gerenciador de pacotes etc.).
- **Tipos de atividade** — fluxos detalhados por atividade (implementação, experimentação, análise), como no projeto de referência.
- **Lint e formatação** — ferramentas e comandos de verificação.
