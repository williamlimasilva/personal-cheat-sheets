# 📝 Cheat Sheet - Git Commit Patterns

> 📝 **Guia prático para criar commits semânticos e organizados no Git, seguindo as melhores práticas de versionamento.**

---

## 📑 Índice

1. [Conceitos Básicos](#-conceitos-básicos)
2. [Sintaxe Fundamental](#-sintaxe-fundamental)
3. [Estruturas Principais](#-estruturas-principais)
4. [Recursos Avançados](#-recursos-avançados)
5. [Melhores Práticas](#-melhores-práticas)
6. [Links Úteis](#-links-úteis)

---

## 📘 Conceitos Básicos

### 🔑 Fundamentos de Commits Semânticos

| Conceito | Descrição | Exemplo | Observação |
| -------- | --------- | ------- | ---------- |
| `Commit Semântico` | Mensagem de commit estruturada e significativa | `feat(auth): adicionar login via Google` | Facilita a compreensão das mudanças |
| `Tipo de Commit` | Categoria que descreve a natureza da mudança | `fix`, `feat`, `docs` | Padroniza a comunicação no repositório |

---

## 🚀 Sintaxe Fundamental

### 📝 Estrutura Básica de Commit

| Estrutura | Descrição | Exemplo | Resultado |
| --------- | --------- | ------- | --------- |
| `tipo(escopo)` | Categoria e área afetada | `feat(auth)` | Identifica o contexto da mudança |
| `: descrição` | Resumo conciso da alteração | `: adicionar autenticação OAuth` | Explica rapidamente a mudança |

### 💡 Formato Completo

```markdown
tipo(escopo opcional): descrição curta

Mensagem detalhada opcional.

Refs: número ou link do ticket/issue opcional.
```

---

## 🔍 Estruturas Principais

### 📊 Tipos Comuns de Commits

| Tipo | Descrição | Escopos Sugeridos | Uso |
| ---- | --------- | ----------------- | --- |
| `feat` | Nova funcionalidade | `auth`, `api`, `core` | Adições de recursos |
| `fix` | Correção de bug | `ui`, `backend`, `database` | Resolução de problemas |
| `docs` | Mudanças na documentação | `readme`, `changelog` | Atualizações de docs |
| `refactor` | Refatoração de código | `api`, `models`, `services` | Melhorias estruturais |
| `test` | Adição/correção de testes | `unit`, `integration` | Cobertura de testes |
| `chore` | Tarefas de manutenção | `deps`, `tooling` | Atualizações gerais |

---

## 🎯 Recursos Avançados

### ⚡ Exemplos de Commits Avançados

| Recurso | Descrição | Exemplo | Observação |
| ------- | --------- | ------- | ---------- |
| `Refs` | Referência a issues | `Refs: #123` | Rastreabilidade |
| `Escopo Múltiplo` | Múltiplas áreas afetadas | `fix(ui,api): corrigir autenticação` | Contexto abrangente |

---

## 📚 Melhores Práticas

### ✅ Recomendações

| Prática | Descrição | Exemplo | Benefício |
| ------- | --------- | ------- | --------- |
| `Imperativo` | Use linguagem imperativa | `Adicionar` em vez de `Adicionado` | Clareza |
| `Concisão` | Limite título a 50 caracteres | `feat(auth): add Google login` | Legibilidade |
| `Detalhamento` | Explique o porquê da mudança | Descreva motivações e impactos | Contexto |

---

## 📑 Dicas e Alertas

> [!NOTE]
> Commits semânticos melhoram a comunicação em equipes de desenvolvimento.

> [!TIP]
> Use ferramentas como `commitizen` para facilitar a criação de commits padronizados.

> [!WARNING]
> Evite commits muito genéricos como "fix" ou "update".

> [!IMPORTANT]
> Mantenha a consistência nos tipos e escopos de commit.

---

## 🔗 Links Úteis

- [📘 Conventional Commits](https://www.conventionalcommits.org/)
- [📚 Git Book: Mensagens de Commit](https://git-scm.com/book/pt-br/v2/Git-Essentials-Committing)
- [💻 Commitizen CLI](https://github.com/commitizen/cz-cli)

---

## 🎨 Exemplos Práticos no Terminal

### Fluxo Completo de Commits

#### Preparando Mudanças

```bash
# Verificar status dos arquivos modificados
git status

# Adicionar arquivos específicos
git add src/components/PaymentForm.js
git add src/services/PaymentService.js

# Ou adicionar todas as mudanças
git add .
```

### Exemplos Detalhados por Tipo

#### Funcionalidades (feat)

```bash
# Adicionar novos arquivos para feature de pagamento PIX
git add src/components/PIXPayment.js
git add src/services/PIXService.js

# Commit com mensagem detalhada
git commit -m "feat(payment): adicionar suporte a pagamentos via PIX

Implementa integração com API de pagamentos do banco para processamento de transações PIX.
Adiciona validações de chave PIX e tratamento de erros específicos.

Refs: #456"
```

#### Commits Interativos

```bash
# Modo interativo para commits mais detalhados
git commit

# Abrirá seu editor de texto padrão (vim, nano, etc.)
# Digite a mensagem de commit:
"""
feat(analytics): criar dashboard de métricas de usuário

Desenvolve componente de visualização de dados com gráficos interativos.
Inclui filtros de período e exportação de relatórios em CSV.

Refs: #789
"""
# Salve e feche o editor
```

#### Correções (fix)

```bash
# Corrigir bug de autenticação
git add src/auth/LoginManager.js
git commit -m "fix(auth): corrigir vazamento de memória no processo de login

Otimiza gerenciamento de sessões e elimina referências pendentes após logout.
Reduz consumo de memória em 30% durante múltiplos ciclos de autenticação.

Refs: #234"
```

#### Commits Parciais

```bash
# Adicionar apenas partes específicas de um arquivo
git add -p src/database/UserQueries.js

# Commit seletivo
git commit -m "fix(database): resolver consulta lenta de usuários

Adiciona índice composto para melhorar performance de buscas complexas.
Reduz tempo de consulta de 500ms para 50ms em tabelas grandes."
```

#### Refatorações (refactor)

```bash
# Refatorar estrutura de serviços
git add src/services/
git commit -m "refactor(api): modularizar camada de serviços

Separa responsabilidades em módulos menores e mais coesos.
Facilita manutenção e adiciona injeção de dependência.

Refs: #567"
```

#### Documentação (docs)

```bash
# Atualizar documentação de API
git add docs/api-specification.md
git commit -m "docs(api): atualizar especificação de endpoints

Adiciona descrições detalhadas de parâmetros e códigos de resposta.
Inclui exemplos de requisição e casos de uso.

Refs: #345"
```

#### Manutenção (chore)

```bash
# Atualizar dependências
git add package.json
git add package-lock.json
git commit -m "chore(deps): atualizar dependências de segurança

Upgrade do React de 17.0.2 para 18.2.0
Corrige vulnerabilidades de segurança identificadas.

Refs: #678"
```

#### Testes (test)

```bash
# Adicionar novos testes de autenticação
git add tests/auth/
git commit -m "test(auth): adicionar testes de integração para fluxo de login

Cobre cenários de:
- Autenticação bem-sucedida
- Falha de credenciais
- Recuperação de senha
- Bloqueio por tentativas inválidas"
```

#### Performance (perf)

```bash
# Otimizar algoritmo de busca
git add src/search/
git commit -m "perf(search): otimizar algoritmo de busca

Substitui busca linear por índice invertido.
Reduz tempo de busca de O(n) para O(log n)."
```

### Dicas Avançadas de Commit

```bash
# Corrigir último commit sem criar novo commit
git commit --amend

# Fazer commit pulando stage (apenas para arquivos modificados)
git commit -am "fix(ui): corrigir alinhamento de botão"

# Fazer commit com escopo múltiplo
git commit -m "fix(ui,api): corrigir autenticação e layout"
```

### Boas Práticas no Terminal

1. **Sempre use `git status` antes de commitar**
2. **Utilize `git add -p` para commits parciais**
3. **Prefira commits atômicos e focados**
4. **Use o modo interativo para mensagens detalhadas**

---

## 🎉 Considerações Finais

### Diretrizes de Qualidade

- Priorize clareza e objetividade
- Mantenha consistência nos padrões
- Documente o contexto das mudanças
- Facilite a revisão de código
- Melhore a rastreabilidade do projeto

### Resultado Esperado

- Histórico de commits limpo e compreensível
- Comunicação eficiente entre desenvolvedores
- Facilitação de revisões e manutenção de código

### Exemplos de Commits

#### Adicionando uma funcionalidade:

```markdown
feat(auth): adicionar suporte à autenticação via Google OAuth

Implementa o fluxo de autenticação usando a biblioteca XYZ para integração com o Google OAuth.

Refs: #123
```

#### Corrigindo um bug:

```markdown
fix(ui): corrigir exibição incorreta do botão de login no Safari

Ajusta o alinhamento do botão no Safari alterando o estilo CSS.
```

#### Melhorias no código:

```markdown
refactor(api): otimizar função de busca por usuários

Reduz a complexidade do código removendo loops desnecessários.
```

#### Escrevendo documentação:

```markdown
docs(readme): atualizar seção de instalação

Inclui passos para instalação em ambientes Windows.
```