# 🐘 Cheat Sheet - PostgreSQL

> 📝 Um guia completo sobre PostgreSQL - O SGBD relacional mais avançado de código aberto

## 📑 Índice
1. [Conceitos Básicos](#conceitos-básicos)
2. [Sintaxe Fundamental](#sintaxe-fundamental)
3. [Estruturas Principais](#estruturas-principais)
4. [Recursos Avançados](#recursos-avançados)
5. [Melhores Práticas](#melhores-práticas)
6. [Ferramentas e Ambiente](#ferramentas-e-ambiente)

## 📘 Conceitos Básicos

### 🔑 Tipos de Dados
| Tipo | Descrição | Exemplo | Resultado |
|------|-----------|---------|-----------|
| `INTEGER` | Número inteiro | `idade INTEGER` | Armazena números inteiros |
| `NUMERIC` | Número decimal exato | `preco NUMERIC(10,2)` | Armazena valores monetários |
| `VARCHAR` | Texto variável | `nome VARCHAR(100)` | Armazena texto com limite |
| `TEXT` | Texto ilimitado | `descricao TEXT` | Armazena texto sem limite |
| `TIMESTAMP` | Data e hora | `created_at TIMESTAMP` | Armazena data/hora |
| `BOOLEAN` | Verdadeiro/Falso | `ativo BOOLEAN` | Armazena true/false |
| `UUID` | Identificador único | `id UUID` | Gera ID único universal |
| `JSONB` | JSON binário | `dados JSONB` | Armazena JSON otimizado |
| `ARRAY` | Matriz de valores | `tags TEXT[]` | Armazena lista de valores |

### 📝 Exemplo Prático: Criação de Tabela
```sql
-- Criar uma tabela com diferentes tipos de dados
CREATE TABLE produtos (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(), # -----> ID único universal
    nome VARCHAR(100) NOT NULL,                    # -----> Nome do produto
    descricao TEXT,                                # -----> Descrição longa
    preco NUMERIC(10,2) NOT NULL,                  # -----> Preço com 2 decimais
    categorias TEXT[],                             # -----> Array de categorias
    metadata JSONB,                                # -----> Dados extras em JSON
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP  # -----> Data de criação
);
```

> 💡 **Dica:** Use JSONB em vez de JSON para melhor performance e funcionalidades adicionais

## 🔧 Sintaxe Fundamental

### 🎯 Operadores e Funções
| Operador | Descrição | Exemplo | Resultado |
|----------|-----------|---------|-----------|
| `->` | Acesso JSON | `dados->'nome'` | Retorna valor JSON como texto |
| `->>`| Acesso JSON texto | `dados->>'nome'` | Retorna valor como texto |
| `@>` | Contém | `dados @> '{"status":"ativo"}'` | Verifica se contém JSON |
| `<@` | Está contido | `ARRAY[1] <@ numeros` | Verifica se array contém |
| `&&` | Sobrepõe | `ARRAY[1,2] && ARRAY[2,3]` | Verifica interseção |
| `||` | Concatenação | `'Olá ' || nome` | Concatena strings |

### 📝 Exemplo Prático: Consultas Avançadas
```sql
-- Consulta com JSON, array e funções
SELECT 
    nome,
    metadata->>'categoria' as categoria,     # -----> Extrai valor JSON
    array_length(categorias, 1) as total,    # -----> Conta elementos array
    created_at::DATE as data_criacao        # -----> Conversão de tipo
FROM 
    produtos
WHERE 
    categorias && ARRAY['eletrônicos']      # -----> Verifica array
    AND metadata @> '{"status": "ativo"}'   # -----> Verifica JSON
ORDER BY 
    created_at DESC;
```

## 🔄 Estruturas Principais

### 🎯 Extensões
| Extensão | Descrição | Comando | Resultado |
|----------|-----------|---------|-----------|
| `postgis` | Dados geoespaciais | `CREATE EXTENSION postgis` | Habilita funções GIS |
| `pgcrypto` | Criptografia | `CREATE EXTENSION pgcrypto` | Funções de hash/crypto |
| `uuid-ossp` | UUIDs | `CREATE EXTENSION uuid-ossp` | Geração de UUIDs |
| `pg_stat_statements` | Monitoramento | `CREATE EXTENSION pg_stat_statements` | Análise de queries |
| `pg_trgm` | Busca textual | `CREATE EXTENSION pg_trgm` | Busca por similaridade |

### 📝 Exemplo Prático: Usando Extensões
```sql
-- Habilitar extensões necessárias
CREATE EXTENSION IF NOT EXISTS postgis;     # -----> Habilita PostGIS
CREATE EXTENSION IF NOT EXISTS pgcrypto;    # -----> Habilita pgcrypto

-- Criar tabela com recursos das extensões
CREATE TABLE locais (
    id UUID DEFAULT gen_random_uuid(),      # -----> UUID automático
    nome VARCHAR(100),
    localizacao GEOGRAPHY(POINT),           # -----> Ponto geográfico
    senha_hash TEXT,                        # -----> Senha criptografada
    PRIMARY KEY (id)
);

-- Inserir dados usando funções das extensões
INSERT INTO locais (nome, localizacao, senha_hash) 
VALUES (
    'Escritório',
    ST_SetSRID(ST_MakePoint(-46.633308, -23.550520), 4326),  # -----> Cria ponto
    crypt('senha123', gen_salt('bf'))                         # -----> Criptografa
);
```

## 🚀 Recursos Avançados

### 🎯 Funções Window
| Função | Descrição | Exemplo | Resultado |
|--------|-----------|---------|-----------|
| `ROW_NUMBER()` | Número da linha | `ROW_NUMBER() OVER (ORDER BY data)` | Enumera resultados |
| `LAG()` | Valor anterior | `LAG(valor) OVER (ORDER BY data)` | Acessa linha anterior |
| `LEAD()` | Próximo valor | `LEAD(valor) OVER (ORDER BY data)` | Acessa próxima linha |
| `FIRST_VALUE()` | Primeiro valor | `FIRST_VALUE(valor) OVER (...)` | Primeiro da partição |
| `LAST_VALUE()` | Último valor | `LAST_VALUE(valor) OVER (...)` | Último da partição |

### 📝 Exemplo Prático: Análise de Dados
```sql
-- Análise de vendas com funções window
SELECT 
    data,
    valor,
    ROW_NUMBER() OVER w as seq,            # -----> Número sequencial
    LAG(valor) OVER w as valor_anterior,   # -----> Valor da venda anterior
    LEAD(valor) OVER w as proxima_valor,   # -----> Valor da próxima venda
    AVG(valor) OVER w as media_movel       # -----> Média móvel
FROM vendas
WINDOW w AS (ORDER BY data)                # -----> Define janela
ORDER BY data;
```

## ⚡ Melhores Práticas

### 🎯 Otimização
| Prática | Descrição | Exemplo | Benefício |
|---------|-----------|---------|-----------|
| `Índices` | Criar índices | `CREATE INDEX idx_nome ON tabela(nome)` | Acelera buscas |
| `VACUUM` | Limpar espaço | `VACUUM ANALYZE tabela` | Otimiza storage |
| `EXPLAIN` | Analisar query | `EXPLAIN ANALYZE SELECT ...` | Identifica gargalos |
| `Particionamento` | Dividir tabelas | `CREATE TABLE PARTITION OF ...` | Melhora performance |

### 📝 Exemplo Prático: Otimização
```sql
-- Criar índices eficientes
CREATE INDEX idx_produtos_categoria        # -----> Índice para categoria
ON produtos USING GIN(categorias);         # -----> Índice GIN para array

CREATE INDEX idx_produtos_metadata         # -----> Índice para JSON
ON produtos USING GIN(metadata);           # -----> Índice GIN para JSONB

-- Analisar performance
EXPLAIN ANALYZE                           # -----> Analisa execução
SELECT * FROM produtos                    # -----> Query a ser analisada
WHERE categorias && ARRAY['eletrônicos']  # -----> Condição de filtro
AND metadata @> '{"status": "ativo"}';    # -----> Condição JSON
```

## 🛠️ Ferramentas e Ambiente

### 🔧 Ferramentas de Administração
| Ferramenta | Descrição | Comando | Uso |
|------------|-----------|---------|-----|
| `psql` | Cliente CLI | `psql -U postgres` | Acesso via terminal |
| `pg_dump` | Backup | `pg_dump dbname > backup.sql` | Backup do banco |
| `pg_restore` | Restauração | `pg_restore -d dbname backup.sql` | Restaura backup |
| `pgAdmin` | GUI | Interface gráfica | Administração visual |

### 📝 Exemplo Prático: Manutenção
```sql
-- Backup do banco
pg_dump -U postgres -F c -b -v -f backup.backup dbname  # -----> Backup completo

-- Monitoramento de processos
SELECT pid, query, state
FROM pg_stat_activity                     # -----> Visualiza processos
WHERE state != 'idle'                     # -----> Apenas ativos
ORDER BY query_start DESC;                # -----> Ordenado por início

-- Matar query problemática
SELECT pg_terminate_backend(pid)          # -----> Mata processo
FROM pg_stat_activity                     # -----> Da tabela de processos
WHERE query_start < now() - interval '5 minutes';  # -----> Rodando há 5+ min
```

## 📚 Links Úteis
- [📖 Documentação Oficial PostgreSQL](https://www.postgresql.org/docs/current/)
- [📝 Wiki PostgreSQL](https://wiki.postgresql.org/wiki/Main_Page)
- [🎓 PostgreSQL Tutorial](https://www.postgresqltutorial.com/)
- [🔧 PostgreSQL Exercises](https://pgexercises.com/)

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
