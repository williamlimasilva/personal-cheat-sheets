# 📚 Template para Cheat Sheet de Programação

## 🎯 Estrutura do Documento

### 1️⃣ Cabeçalho
```markdown
# [EMOJI] Cheat Sheet - [Nome da Tecnologia] Commands.md

> 📝 Um guia completo sobre [Nome da Tecnologia]
> 📅 Última atualização: [DATA]
> 🔗 Versão da tecnologia: [VERSÃO]
```

### 2️⃣ Índice Padrão
```markdown
## 📑 Índice
1. [Conceitos Básicos](#conceitos-básicos)
2. [Sintaxe Fundamental](#sintaxe-fundamental)
3. [Estruturas Principais](#estruturas-principais)
4. [Recursos Avançados](#recursos-avançados)
5. [Melhores Práticas](#melhores-práticas)
6. [Ferramentas e Ambiente](#ferramentas-e-ambiente)
```

### 3️⃣ Formato das Seções

#### Tabelas de Referência
```markdown
| 🔍 Comando | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `comando`  | Explicação| `exemplo` | saída |
```

#### Blocos de Código
```markdown
<div class="example">
### 📝 Exemplo: [Nome do Exemplo]

\```bash
# Comentário explicativo
código_exemplo    # -----------------------> Resultado esperado
\```
</div>
```

#### Dicas e Observações
```markdown
<div class="tip">
💡 **Dica:** Texto da dica ou observação importante
</div>

<div class="warning">
⚠️ **Atenção:** Texto do aviso importante
</div>
```

### 4️⃣ Estilo e Formatação

#### CSS para Estilização
```html
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
    box-shadow: 0 2px 4px rgba(0,0,0,0.2);
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

td:nth-child(1) {
    width: 20%;
    color: var(--text-accent);
}

td:nth-child(2) {
    width: 30%;
}

td:nth-child(3) {
    width: 25%;
    font-family: 'Consolas', monospace;
    color: var(--string);
}

td:nth-child(4) {
    width: 25%;
    color: var(--comment);
    font-style: italic;
}

code {
    color: var(--string);
    background-color: var(--bg-tertiary);
    padding: 2px 4px;
    border-radius: 3px;
}

h1 {
    color: var(--text-primary);
    text-align: center;
    margin-bottom: 30px;
    font-size: 2.5em;
}

h2 {
    color: var(--text-accent);
    border-bottom: 1px solid var(--text-accent);
    padding-bottom: 5px;
    margin-top: 30px;
}

h3 {
    color: var(--keyword);
    margin-top: 20px;
}

.example {
    background-color: var(--bg-tertiary);
    padding: 12px;
    border-radius: 4px;
    margin: 10px 0;
    font-size: 0.9em;
    border-left: 3px solid var(--text-accent);
}

.tip {
    background-color: var(--bg-tertiary);
    padding: 12px;
    border-radius: 4px;
    margin: 10px 0;
    border-left: 3px solid var(--keyword);
}

.warning {
    background-color: var(--bg-tertiary);
    padding: 12px;
    border-radius: 4px;
    margin: 10px 0;
    border-left: 3px solid #d7ba7d;
}
</style>
```

#### JavaScript para Funcionalidades Interativas
```javascript
<script>
// Função para copiar código para a área de transferência
function copyToClipboard(element) {
    const code = element.parentElement.querySelector('code').textContent;
    navigator.clipboard.writeText(code).then(() => {
        const originalText = element.textContent;
        element.textContent = '✅ Copiado!';
        setTimeout(() => {
            element.textContent = originalText;
        }, 2000);
    });
}

// Função para adicionar botões de cópia a todos os blocos de código
document.addEventListener('DOMContentLoaded', () => {
    document.querySelectorAll('pre').forEach(block => {
        const button = document.createElement('button');
        button.className = 'copy-button';
        button.textContent = '📋 Copiar';
        button.onclick = () => copyToClipboard(button);
        block.style.position = 'relative';
        block.insertBefore(button, block.firstChild);
    });
});
</script>

## 📋 Instruções de Uso

### 1️⃣ Nome do Arquivo
- Use o formato: `[EMOJI] Cheat Sheet - [Nome].md`
- Exemplos de emojis:
  - 💻 Para linguagens de programação
  - 🔧 Para ferramentas
  - 📦 Para frameworks
  - 🗄️ Para bancos de dados
  - 📝 Para conceitos/metodologias

### 2️⃣ Estrutura de Conteúdo
1. Comece com conceitos básicos
2. Progrida para tópicos mais avançados
3. Inclua exemplos práticos
4. Adicione dicas e melhores práticas
5. Termine com recursos e referências

### 3️⃣ Formatação
- Use emojis para categorizar seções
- Mantenha consistência na formatação
- Use tabelas para referência rápida
- Inclua exemplos de código comentados
- Destaque informações importantes

### 4️⃣ Seções Recomendadas

#### Para Linguagens de Programação
- Sintaxe Básica
- Tipos de Dados
- Estruturas de Controle
- Funções e Métodos
- Classes e Objetos
- Bibliotecas Padrão
- Gerenciamento de Erros
- Recursos Avançados

#### Para Frameworks
- Instalação e Configuração
- Estrutura do Projeto
- Componentes Principais
- APIs e Integrações
- Segurança
- Performance
- Deploy
- Ferramentas de Desenvolvimento

#### Para Ferramentas
- Instalação
- Comandos Básicos
- Configuração
- Casos de Uso Comuns
- Integração com Outras Ferramentas
- Troubleshooting
- Melhores Práticas

### 5️⃣ Dicas para Manutenção
- Mantenha o documento atualizado
- Verifique links e referências
- Adicione novos recursos relevantes
- Corrija erros e imprecisões
- Aceite feedback e contribuições

## 🎨 Exemplos de Seções

### Tabela de Comandos/Sintaxe
```markdown
| 🔍 Comando | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `comando`  | Explicação| `exemplo` | saída |
```

### Bloco de Código com Explicação
```markdown
<div class="example">
### 📝 Exemplo: Nome do Exemplo

\```bash
# Comentário explicativo
código_exemplo    # -----------------------> Resultado esperado
\```
</div>
```

### Seção de Dicas
```markdown
<div class="tip">
💡 **Dica Pro:** Dica importante sobre o tópico
</div>

<div class="warning">
⚠️ **Atenção:** Aviso sobre possíveis problemas
</div>
```

### Referências e Links
```markdown
## 📚 Referências
- [📖 Documentação Oficial](url)
- [📝 Guia de Melhores Práticas](url)
- [🎓 Tutoriais Recomendados](url)
```
