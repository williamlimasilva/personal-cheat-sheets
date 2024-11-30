# 📦 Cheat Sheet - Git Commands

> 📚 Um guia completo sobre comandos Git e suas utilizações

## 📑 Índice
1. [Configuração Inicial](#configuração-inicial)
2. [Comandos Básicos](#comandos-básicos)
3. [Branches e Merging](#branches-e-merging)
4. [Trabalho Remoto](#trabalho-remoto)
5. [Inspeção e Comparação](#inspeção-e-comparação)
6. [Desfazer Mudanças](#desfazer-mudanças)
7. [Recursos Avançados](#recursos-avançados)

## Configuração Inicial

### Configurações Globais
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `git config --global user.name` | Define nome do usuário | `git config --global user.name "João Silva"` | Define nome para commits |
| `git config --global user.email` | Define email do usuário | `git config --global user.email "joao@email.com"` | Define email para commits |
| `git config --global core.editor` | Define editor padrão | `git config --global core.editor "code --wait"` | VS Code como editor |
| `git config --list` | Lista configurações | `git config --list` | Mostra todas configs |

### Inicialização
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `git init` | Inicia repositório | `git init` | Cria repositório vazio |
| `git clone` | Clona repositório | `git clone https://github.com/user/repo.git` | Copia repositório remoto |
| `git clone --depth` | Clona com histórico limitado | `git clone --depth 1 url` | Clone mais rápido |

## Comandos Básicos

### Área de Trabalho
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `git status` | Estado do working dir | `git status` | Mostra status atual |
| `git add` | Adiciona à staging area | `git add arquivo.txt` | Prepara para commit |
| `git add .` | Adiciona tudo | `git add .` | Prepara todos arquivos |
| `git commit` | Cria commit | `git commit -m "mensagem"` | Salva alterações |
| `git commit -am` | Add + commit | `git commit -am "mensagem"` | Add e commit direto |

### Histórico
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `git log` | Mostra histórico | `git log` | Lista commits |
| `git log --oneline` | Histórico resumido | `git log --oneline` | Uma linha por commit |
| `git log --graph` | Histórico gráfico | `git log --graph` | Árvore de commits |
| `git show` | Detalhes do commit | `git show abc123` | Info do commit |

## Branches e Merging

### Gerenciamento de Branches
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `git branch` | Lista branches | `git branch` | Mostra branches locais |
| `git branch nome` | Cria branch | `git branch feature` | Nova branch |
| `git checkout` | Muda de branch | `git checkout feature` | Troca para branch |
| `git checkout -b` | Cria e muda | `git checkout -b feature` | Cria e troca |
| `git branch -d` | Deleta branch | `git branch -d feature` | Remove branch |

### Merging e Rebase
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `git merge` | Une branches | `git merge feature` | Integra mudanças |
| `git rebase` | Reaplica commits | `git rebase main` | Reorganiza histórico |
| `git merge --abort` | Cancela merge | `git merge --abort` | Desfaz merge com conflito |
| `git rebase --abort` | Cancela rebase | `git rebase --abort` | Desfaz rebase |

## Trabalho Remoto

### Repositórios Remotos
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `git remote` | Lista remotes | `git remote -v` | Mostra remotes |
| `git remote add` | Adiciona remote | `git remote add origin url` | Novo remote |
| `git push` | Envia commits | `git push origin main` | Atualiza remote |
| `git pull` | Baixa e integra | `git pull origin main` | Atualiza local |
| `git fetch` | Baixa refs | `git fetch origin` | Atualiza refs |

### Sincronização
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `git push -u` | Define upstream | `git push -u origin main` | Configura tracking |
| `git branch -vv` | Mostra tracking | `git branch -vv` | Info de tracking |
| `git remote show` | Info do remote | `git remote show origin` | Detalhes do remote |

## Inspeção e Comparação

### Diferenças
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `git diff` | Mostra mudanças | `git diff` | Difs não staged |
| `git diff --staged` | Difs staged | `git diff --staged` | Difs para commit |
| `git diff branch1..branch2` | Entre branches | `git diff main..feature` | Difs entre branches |

### Inspeção
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `git blame` | Autoria de linhas | `git blame arquivo.txt` | Quem mudou o quê |
| `git bisect` | Busca binária | `git bisect start` | Encontra bug |
| `git grep` | Busca no código | `git grep "TODO"` | Encontra padrão |

## Desfazer Mudanças

### Working Directory
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `git checkout --` | Descarta mudanças | `git checkout -- arquivo.txt` | Restaura arquivo |
| `git clean` | Remove não tracked | `git clean -fd` | Remove arquivos novos |
| `git restore` | Restaura arquivos | `git restore arquivo.txt` | Descarta mudanças |

### Staged e Commits
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `git reset` | Desfaz staging | `git reset arquivo.txt` | Remove do stage |
| `git reset --soft` | Desfaz commit | `git reset --soft HEAD~1` | Mantém mudanças |
| `git reset --hard` | Reset completo | `git reset --hard HEAD~1` | Remove mudanças |
| `git revert` | Reverte commit | `git revert abc123` | Novo commit reverso |
| `git commit --amend` | Modifica último commit | `git commit --amend -m "Nova mensagem"` | Altera mensagem |
| `git push --force` | Força push | `git push --force origin main` | Sobrescreve histórico |
| `git push --force-with-lease` | Força push seguro | `git push --force-with-lease origin main` | Força push com verificação |

## Recursos Avançados

### Stash
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `git stash` | Salva WIP | `git stash` | Guarda mudanças |
| `git stash list` | Lista stashes | `git stash list` | Mostra stashes |
| `git stash pop` | Aplica e remove | `git stash pop` | Restaura e remove último stash |
| `git stash apply` | Aplica sem remover | `git stash apply` | Restaura mantendo stash |
| `git stash show` | Mostra alterações | `git stash show stash@{0}` | Exibe conteúdo do stash |
| `git stash apply stash@{n}` | Aplica stash específico | `git stash apply stash@{2}` | Restaura stash específico |
| `git stash drop` | Remove stash | `git stash drop stash@{0}` | Deleta stash |

### Tags
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `git tag` | Lista tags | `git tag` | Mostra tags |
| `git tag -a` | Cria tag anotada | `git tag -a v1.0 -m "Versão 1.0"` | Nova tag |
| `git push --tags` | Envia tags | `git push origin --tags` | Atualiza tags |

### Submodules
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `git submodule add` | Adiciona submódulo | `git submodule add url path` | Novo submódulo |
| `git submodule update` | Atualiza submódulos | `git submodule update --init` | Sincroniza submódulos |

### Exemplos Práticos

#### Fluxo Básico
```bash
# Iniciando um projeto
git init
git add .
git commit -m "Commit inicial"

# Trabalhando com branches
git checkout -b feature
# ... faz alterações ...
git add .
git commit -m "Nova feature"
git checkout main
git merge feature
```

#### Desfazendo Alterações
```bash
# Desfazendo alterações não commitadas
git checkout -- arquivo.txt
git restore arquivo.txt

# Desfazendo último commit
git reset --soft HEAD~1
# ou
git revert HEAD
```

#### Trabalho Remoto
```bash
# Configurando remote
git remote add origin https://github.com/user/repo.git
git push -u origin main

# Atualizando local
git pull origin main
# ou
git fetch origin
git merge origin/main
```

#### Resolução de Conflitos
```bash
# Durante merge com conflito
git status # ver arquivos com conflito
# Resolver conflitos manualmente
git add . # marcar como resolvido
git commit # finalizar merge
```

<style>
:root {
    --bg-primary: #1E1E1E;
    --bg-secondary: #252526;
    --bg-tertiary: #2D2D2D;
    --text-primary: #D4D4D4;
    --text-accent: #569CD6;
    --keyword: #C586C0;
    --string: #CE9178;
    --comment: #6A9955;
    --operator: #D4D4D4;
    --border: #404040;
}

body {
    background-color: var(--bg-primary);
    color: var(--text-primary);
    font-family: 'Consolas', monospace;
    line-height: 1.6;
    margin: 20px;
    max-width: 1920px;
}

.container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(600px, 1fr));
    gap: 20px;
    margin: 0 auto;
}

.section {
    background: var(--bg-secondary);
    padding: 20px;
    border-radius: 8px;
    margin-bottom: 20px;
}

table {
    width: 100%;
    border-collapse: collapse;
    margin: 10px 0;
    background-color: var(--bg-tertiary);
    border-radius: 4px;
}

th, td {
    padding: 12px;
    text-align: left;
    border-bottom: 1px solid var(--border);
}

td:nth-child(3) {
    font-family: 'Consolas', monospace;
    color: var(--string);
}

td:nth-child(4) {
    color: var(--comment);
    font-style: italic;
}

code {
    color: var(--string);
    background-color: var(--bg-tertiary);
    padding: 2px 4px;
    border-radius: 3px;
}

h2 {
    color: var(--text-accent);
    border-bottom: 1px solid var(--text-accent);
    padding-bottom: 5px;
}

h3 {
    color: var(--keyword);
}

.example {
    background-color: var(--bg-tertiary);
    padding: 8px;
    border-radius: 4px;
    margin-top: 4px;
    font-size: 0.9em;
}
</style>

<script>
document.addEventListener('DOMContentLoaded', function() {
    // Toggle para seções expansíveis
    const sections = document.querySelectorAll('.section h2');
    sections.forEach(section => {
        section.addEventListener('click', () => {
            const parent = section.parentElement;
            parent.classList.toggle('expanded');
        });
    });
});
</script>
