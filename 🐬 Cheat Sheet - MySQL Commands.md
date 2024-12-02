# 🗄️ Cheat Sheet - MySQL Commands.md

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

> 📝 Guia específico de recursos e comandos exclusivos do MySQL
> 📅 Última atualização: 2024
> 🔗 Versão: MySQL 8.0

## 🚀 Recursos Exclusivos MySQL

<div class="container">
<div class="section">

### 🔄 Tipos de Dados Específicos
| 🔍 Comando | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `ENUM` | Lista de valores permitidos | `ENUM('small', 'medium', 'large')` | Restringe valores |
| `SET` | Múltiplos valores | `SET('tag1', 'tag2', 'tag3')` | Permite combinações |
| `TINYINT(1)` | Boolean otimizado | `TINYINT(1) DEFAULT 0` | Booleano eficiente |
| `MEDIUMTEXT` | Texto até 16MB | `MEDIUMTEXT` | Textos longos |
| `JSON` | Dados JSON nativos | `JSON` | Armazena JSON |

### 🔐 Engines de Armazenamento
| 🔍 Comando | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `InnoDB` | Engine padrão | `CREATE TABLE t (id INT) ENGINE=InnoDB;` | ACID, transações |
| `MEMORY` | Tabela em memória | `CREATE TABLE t (id INT) ENGINE=MEMORY;` | Performance |
| `MyISAM` | Engine legada | `CREATE TABLE t (id INT) ENGINE=MyISAM;` | Leitura rápida |
| `SHOW ENGINES` | Listar engines | `SHOW ENGINES;` | Engines disponíveis |

<div class="example">
### 📝 Exemplo: Criação com Engine Específica

```sql
CREATE TABLE orders (
    id INT PRIMARY KEY,
    data JSON,
    size ENUM('S', 'M', 'L', 'XL'),
    tags SET('promo', 'new', 'sale')
) ENGINE=InnoDB;
```
</div>

</div>
</div>

## 🛠️ Funcionalidades Avançadas

<div class="container">
<div class="section">

### 🎯 Particionamento
| 🔍 Comando | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `PARTITION BY RANGE` | Particionar por faixa | `PARTITION BY RANGE(year_col)` | Divide por faixas |
| `PARTITION BY LIST` | Particionar por lista | `PARTITION BY LIST(status)` | Divide por valores |
| `PARTITION BY HASH` | Particionar por hash | `PARTITION BY HASH(id)` | Divide uniformemente |
| `REORGANIZE PARTITION` | Reorganizar partições | `ALTER TABLE ... REORGANIZE PARTITION` | Otimiza partições |

### 🔍 Full-Text Search
| 🔍 Comando | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `FULLTEXT INDEX` | Índice de texto | `CREATE FULLTEXT INDEX idx ON table(col)` | Busca textual |
| `MATCH AGAINST` | Busca em texto | `MATCH(col) AGAINST('texto')` | Encontra texto |
| `IN BOOLEAN MODE` | Modo booleano | `MATCH(col) AGAINST('+req -exc' IN BOOLEAN MODE)` | Busca complexa |
| `WITH QUERY EXPANSION` | Expansão de busca | `MATCH(col) AGAINST('termo' WITH QUERY EXPANSION)` | Busca expandida |

</div>
</div>

## 🔄 Replicação e Clustering

<div class="container">
<div class="section">

### 📡 Replicação
| 🔍 Comando | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `SHOW MASTER STATUS` | Status master | `SHOW MASTER STATUS;` | Info replicação |
| `SHOW SLAVE STATUS` | Status slave | `SHOW SLAVE STATUS\G` | Status detalhado |
| `CHANGE MASTER TO` | Configurar slave | `CHANGE MASTER TO MASTER_HOST='host'` | Config replicação |
| `START/STOP SLAVE` | Controle slave | `START SLAVE;` | Inicia replicação |

### 🌐 Group Replication
| 🔍 Comando | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `group_replication_start` | Iniciar grupo | `SET GLOBAL group_replication_start=ON;` | Inicia grupo |
| `group_replication_bootstrap` | Bootstrap grupo | `SET GLOBAL group_replication_bootstrap=ON;` | Primeiro nó |
| `group_replication_status` | Status do grupo | `SELECT * FROM replication_group_members;` | Info do grupo |

</div>
</div>

## 🔒 Segurança Avançada

<div class="container">
<div class="section">

### 🛡️ Recursos de Segurança
| 🔍 Comando | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `CREATE ROLE` | Criar role | `CREATE ROLE 'app_read', 'app_write';` | Novas roles |
| `GRANT ROLE` | Atribuir role | `GRANT 'app_read' TO 'user'@'localhost';` | Atribui role |
| `SET DEFAULT ROLE` | Role padrão | `SET DEFAULT ROLE 'app_read' TO 'user'@'localhost';` | Define padrão |
| `SHOW GRANTS` | Ver permissões | `SHOW GRANTS FOR 'user'@'localhost';` | Lista grants |

### 🔐 Criptografia
| 🔍 Comando | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `CREATE ENCRYPTION KEY` | Criar chave | `ALTER INSTANCE ROTATE INNODB MASTER KEY;` | Nova chave |
| `ENCRYPT TABLE` | Criptografar tabela | `ALTER TABLE t ENCRYPTION='Y';` | Tabela segura |
| `SSL/TLS` | Configurar SSL | `REQUIRE SSL` | Conexão segura |

<div class="warning">
⚠️ **Atenção:** Sempre use SSL/TLS em produção e mantenha as chaves de criptografia seguras!
</div>

</div>
</div>

## 🔧 Otimização e Diagnóstico

<div class="container">
<div class="section">

### 📊 Performance Schema
| 🔍 Comando | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `performance_schema` | Monitoramento | `SELECT * FROM events_statements_summary_by_digest;` | Stats SQL |
| `sys schema` | Visões do sistema | `SELECT * FROM sys.host_summary;` | Info sistema |
| `EXPLAIN FORMAT=JSON` | Análise detalhada | `EXPLAIN FORMAT=JSON SELECT ...` | Plano detalhado |
| `OPTIMIZER_TRACE` | Debug otimizador | `SET optimizer_trace='enabled=on';` | Debug query |

### 🎯 Otimização InnoDB
| 🔍 Comando | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `innodb_buffer_pool` | Config buffer | `SET GLOBAL innodb_buffer_pool_size=` | Otimiza memória |
| `innodb_file_per_table` | Arquivo por tabela | `innodb_file_per_table=1` | Melhor gestão |
| `innodb_flush_method` | Método de flush | `innodb_flush_method=O_DIRECT` | I/O otimizado |

<div class="tip">
💡 **Dica:** Use Performance Schema e sys schema para identificar gargalos de performance
</div>

</div>
</div>

## 📚 Referências

- [📖 MySQL 8.0 Reference Manual](https://dev.mysql.com/doc/refman/8.0/en/)
- [🔧 MySQL Performance Blog](https://www.percona.com/blog/)
- [🛡️ MySQL Security Guide](https://dev.mysql.com/doc/refman/8.0/en/security.html)
- [📊 Performance Schema Tables](https://dev.mysql.com/doc/refman/8.0/en/performance-schema-table-descriptions.html)
