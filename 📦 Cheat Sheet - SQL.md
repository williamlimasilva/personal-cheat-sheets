# 🗄️ Cheat Sheet - SQL

> 📝 Um guia completo sobre SQL (Structured Query Language) - A linguagem padrão para manipulação de bancos de dados relacionais

## 📑 Índice
1. [Conceitos Básicos](#conceitos-básicos)
2. [Sintaxe Fundamental](#sintaxe-fundamental)
3. [Estruturas Principais](#estruturas-principais)
4. [Recursos Avançados](#recursos-avançados)
5. [Comandos de Visualização](#comandos-de-visualização)
6. [Melhores Práticas](#melhores-práticas)
7. [Exemplos Práticos](#exemplos-práticos)
8. [Links Úteis](#links-úteis)

## 📘 Conceitos Básicos

### 🔑 Tipos de Comandos SQL
| Tipo | Descrição | Uso | Comandos Principais |
|------|-----------|-----|-------------------|
| `DDL` | Data Definition Language | Definição da estrutura | `CREATE`, `ALTER`, `DROP`, `TRUNCATE`, `RENAME` |
| `DML` | Data Manipulation Language | Manipulação de dados | `INSERT`, `UPDATE`, `DELETE`, `MERGE` |
| `DQL` | Data Query Language | Consulta de dados | `SELECT` |
| `DCL` | Data Control Language | Controle de acesso | `GRANT`, `REVOKE` |
| `TCL` | Transaction Control Language | Controle de transações | `COMMIT`, `ROLLBACK`, `SAVEPOINT` |

### 📝 Comandos DDL (Data Definition Language)
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `CREATE` | Cria objetos | `CREATE TABLE usuarios (id INT)` | Nova tabela criada |
| `ALTER` | Modifica objetos | `ALTER TABLE usuarios ADD email VARCHAR(100)` | Coluna adicionada |
| `DROP` | Remove objetos | `DROP TABLE usuarios` | Tabela removida |
| `TRUNCATE` | Limpa dados | `TRUNCATE TABLE logs` | Dados removidos |
| `RENAME` | Renomeia objetos | `RENAME TABLE users TO usuarios` | Tabela renomeada |
| `COMMENT` | Adiciona comentários | `COMMENT ON TABLE usuarios IS 'Tabela de usuários'` | Comentário adicionado |

### 📝 Comandos DML (Data Manipulation Language)
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `INSERT` | Insere dados | `INSERT INTO usuarios (nome) VALUES ('João')` | Registro inserido |
| `UPDATE` | Atualiza dados | `UPDATE usuarios SET status = 'ativo'` | Registros atualizados |
| `DELETE` | Remove dados | `DELETE FROM usuarios WHERE inativo = true` | Registros removidos |
| `MERGE` | Mescla dados | `MERGE INTO target USING source ON (id)` | Dados mesclados |
| `CALL` | Chama procedure | `CALL calcular_total(1, @resultado)` | Procedure executada |
| `EXPLAIN` | Plano de execução | `EXPLAIN SELECT * FROM usuarios` | Plano exibido |

### 📝 Comandos DQL (Data Query Language)
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `SELECT` | Consulta básica | `SELECT * FROM usuarios` | Retorna registros |
| `FROM` | Origem dos dados | `FROM usuarios u` | Define tabela fonte |
| `WHERE` | Filtra registros | `WHERE idade >= 18` | Filtra resultados |
| `GROUP BY` | Agrupa registros | `GROUP BY departamento` | Agrupa dados |
| `HAVING` | Filtra grupos | `HAVING COUNT(*) > 5` | Filtra grupos |
| `ORDER BY` | Ordena resultados | `ORDER BY nome ASC` | Ordena dados |
| `DISTINCT` | Remove duplicados | `SELECT DISTINCT cidade FROM usuarios` | Valores únicos |

### 📝 Comandos DCL (Data Control Language)
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `GRANT` | Concede permissões | `GRANT SELECT ON usuarios TO user1` | Permissão concedida |
| `REVOKE` | Remove permissões | `REVOKE INSERT ON produtos FROM user1` | Permissão removida |
| `DENY` | Nega permissões | `DENY DELETE ON logs TO user1` | Permissão negada |
| `CREATE USER` | Cria usuário | `CREATE USER user1 WITH PASSWORD '123'` | Usuário criado |
| `ALTER USER` | Modifica usuário | `ALTER USER user1 WITH PASSWORD '456'` | Usuário modificado |
| `DROP USER` | Remove usuário | `DROP USER user1` | Usuário removido |

### 📝 Comandos TCL (Transaction Control Language)
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `BEGIN` | Inicia transação | `BEGIN TRANSACTION` | Transação iniciada |
| `COMMIT` | Confirma alterações | `COMMIT` | Alterações salvas |
| `ROLLBACK` | Desfaz alterações | `ROLLBACK` | Alterações desfeitas |
| `SAVEPOINT` | Ponto de restauração | `SAVEPOINT ponto1` | Savepoint criado |
| `SET TRANSACTION` | Define transação | `SET TRANSACTION ISOLATION LEVEL READ COMMITTED` | Isolamento definido |

## 🔧 Sintaxe Fundamental

### 🎯 Operações Básicas (CRUD)
| Operação | Comando | Exemplo | Resultado |
|----------|---------|---------|-----------|
| `CREATE` | INSERT | `INSERT INTO usuarios (nome) VALUES ('João')` | Insere novo registro |
| `READ` | SELECT | `SELECT * FROM usuarios WHERE id = 1` | Lê dados existentes |
| `UPDATE` | UPDATE | `UPDATE usuarios SET nome = 'João Silva' WHERE id = 1` | Atualiza registro |
| `DELETE` | DELETE | `DELETE FROM usuarios WHERE id = 1` | Remove registro |

### 📝 Exemplo Prático: Consulta Básica
```sql
SELECT 
    nome,           # -----------------------> Campo a ser retornado
    idade          # -----------------------> Outro campo
FROM 
    usuarios       # -----------------------> Tabela fonte
WHERE 
    idade > 18     # -----------------------> Condição de filtro
ORDER BY 
    nome ASC;      # -----------------------> Ordenação
```

## 🔄 Estruturas Principais

### 🔗 JOINs e Relacionamentos
| Tipo | Descrição | Exemplo | Resultado |
|------|-----------|---------|-----------|
| `INNER JOIN` | Intersecção | `SELECT * FROM A INNER JOIN B ON A.id = B.id` | Registros comuns |
| `LEFT JOIN` | Todos de A | `SELECT * FROM A LEFT JOIN B ON A.id = B.id` | Todos de A + comuns |
| `RIGHT JOIN` | Todos de B | `SELECT * FROM A RIGHT JOIN B ON A.id = B.id` | Todos de B + comuns |
| `FULL JOIN` | União | `SELECT * FROM A FULL JOIN B ON A.id = B.id` | Todos os registros |

### 📝 Exemplo Prático: JOIN Múltiplo
```sql
SELECT 
    u.nome,         # -----------------------> Campo da tabela usuarios
    p.produto       # -----------------------> Campo da tabela pedidos
FROM 
    usuarios u      # -----------------------> Alias para usuarios
    INNER JOIN 
    pedidos p      # -----------------------> Join com tabela pedidos
    ON u.id = p.usuario_id;
```

## 🚀 Recursos Avançados

### 📊 Funções de Agregação
| Função | Descrição | Exemplo | Resultado |
|--------|-----------|---------|-----------|
| `COUNT()` | Conta registros | `SELECT COUNT(*) FROM users` | Total de registros |
| `SUM()` | Soma valores | `SELECT SUM(valor) FROM vendas` | Soma total |
| `AVG()` | Média | `SELECT AVG(idade) FROM usuarios` | Média de idade |
| `MAX()` | Valor máximo | `SELECT MAX(preco) FROM produtos` | Maior preço |
| `MIN()` | Valor mínimo | `SELECT MIN(data) FROM eventos` | Data mais antiga |

### 📝 Exemplo Prático: Subquery
```sql
SELECT 
    nome,
    (SELECT COUNT(*) 
     FROM pedidos 
     WHERE pedidos.usuario_id = usuarios.id
    ) as total_pedidos    # -----------------------> Subquery correlacionada
FROM usuarios;
```

## 🔒 Constraints (Restrições)
| Constraint | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `PRIMARY KEY` | Identifica unicamente cada registro | `id INT PRIMARY KEY` | Chave primária definida |
| `FOREIGN KEY` | Estabelece relacionamento entre tabelas | `FOREIGN KEY (dept_id) REFERENCES departamentos(id)` | Chave estrangeira definida |
| `UNIQUE` | Garante valores únicos | `email VARCHAR(100) UNIQUE` | Não permite duplicatas |
| `NOT NULL` | Não permite valores nulos | `nome VARCHAR(100) NOT NULL` | Valor obrigatório |
| `CHECK` | Valida valor conforme condição | `CHECK (idade >= 18)` | Valida dados na inserção |
| `DEFAULT` | Define valor padrão | `status VARCHAR(20) DEFAULT 'ativo'` | Valor padrão definido |

### 📝 Exemplo Prático: Uso de Constraints
```sql
-- Criar banco de dados para sistema escolar
CREATE DATABASE escola;
USE escola;

-- Tabela de cursos com várias constraints
CREATE TABLE cursos (
    id INT PRIMARY KEY AUTO_INCREMENT,  # -----------------------> Chave primária
    codigo VARCHAR(10) UNIQUE NOT NULL, # -----------------------> Único e obrigatório
    nome VARCHAR(100) NOT NULL,         # -----------------------> Obrigatório
    carga_horaria INT NOT NULL,         # -----------------------> Obrigatório
    preco DECIMAL(10,2) NOT NULL,       # -----------------------> Obrigatório
    nivel VARCHAR(20) DEFAULT 'Básico', # -----------------------> Valor padrão
    status VARCHAR(20) DEFAULT 'Ativo', # -----------------------> Valor padrão
    data_criacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP, # ---------> Timestamp automático
    CHECK (carga_horaria >= 20),        # -----------------------> Validação de valor mínimo
    CHECK (preco >= 0),                 # -----------------------> Validação de valor não negativo
    CHECK (nivel IN ('Básico', 'Intermediário', 'Avançado')), # -> Validação de valores permitidos
    CONSTRAINT uk_codigo UNIQUE (codigo) # -----------------------> Constraint nomeada
);

-- Tabela de professores com constraints
CREATE TABLE professores (
    id INT PRIMARY KEY AUTO_INCREMENT,
    matricula VARCHAR(10) UNIQUE NOT NULL,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    data_contratacao DATE DEFAULT CURRENT_DATE,
    salario DECIMAL(10,2) NOT NULL,
    CHECK (salario > 0)
);

-- Tabela de turmas com múltiplas foreign keys e checks
CREATE TABLE turmas (
    id INT PRIMARY KEY AUTO_INCREMENT,
    codigo VARCHAR(10) UNIQUE NOT NULL,
    curso_id INT NOT NULL,
    professor_id INT NOT NULL,
    data_inicio DATE NOT NULL,
    data_fim DATE NOT NULL,
    vagas INT NOT NULL,
    vagas_ocupadas INT DEFAULT 0,
    
    -- Foreign Keys
    CONSTRAINT fk_curso FOREIGN KEY (curso_id)
        REFERENCES cursos(id)
        ON DELETE RESTRICT          # -----------------------> Impede deleção se houver referências
        ON UPDATE CASCADE,          # -----------------------> Atualiza referências automaticamente
    
    CONSTRAINT fk_professor FOREIGN KEY (professor_id)
        REFERENCES professores(id)
        ON DELETE RESTRICT
        ON UPDATE CASCADE,
    
    -- Checks
    CONSTRAINT chk_datas CHECK (data_fim > data_inicio), # ----> Valida período
    CONSTRAINT chk_vagas CHECK (vagas >= vagas_ocupadas), # ---> Valida quantidade de vagas
    CONSTRAINT chk_vagas_min CHECK (vagas >= 5),         # ----> Mínimo de vagas
    CONSTRAINT chk_vagas_max CHECK (vagas <= 50)         # ----> Máximo de vagas
);

-- Adicionar constraint após criação da tabela
ALTER TABLE turmas
    ADD CONSTRAINT chk_codigo_formato 
    CHECK (codigo REGEXP '^[A-Z]{2}[0-9]{4}$'); # ---------> Formato específico para código

-- Remover constraint
ALTER TABLE turmas
    DROP CONSTRAINT chk_codigo_formato;

-- Exemplo de inserção respeitando constraints
INSERT INTO cursos (codigo, nome, carga_horaria, preco, nivel) 
VALUES ('SQL001', 'SQL Básico', 40, 199.99, 'Básico');

INSERT INTO professores (matricula, nome, email, salario)
VALUES ('PROF001', 'Ana Silva', 'ana@escola.com', 5000.00);

INSERT INTO turmas (codigo, curso_id, professor_id, data_inicio, data_fim, vagas)
VALUES ('TB202401', 1, 1, '2024-02-01', '2024-03-30', 30);
```

> 💡 **Dica:** Use constraints nomeadas (CONSTRAINT nome_constraint) para facilitar sua manutenção posterior

## 📋 Comandos de Visualização
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `SHOW DATABASES` | Lista todos os bancos | `SHOW DATABASES` | Lista de bancos disponíveis |
| `SHOW TABLES` | Lista tabelas do banco atual | `SHOW TABLES` | Lista de tabelas |
| `SHOW COLUMNS` | Lista colunas da tabela | `SHOW COLUMNS FROM usuarios` | Estrutura da tabela |
| `DESC` ou `DESCRIBE` | Descreve estrutura da tabela | `DESC usuarios` | Detalhes das colunas |
| `SHOW CREATE TABLE` | Mostra comando de criação | `SHOW CREATE TABLE usuarios` | DDL da tabela |
| `SHOW INDEX` | Mostra índices da tabela | `SHOW INDEX FROM usuarios` | Lista de índices |
| `SHOW PROCESSLIST` | Lista processos ativos | `SHOW PROCESSLIST` | Processos em execução |
| `SHOW VARIABLES` | Lista variáveis do sistema | `SHOW VARIABLES LIKE '%timeout%'` | Configurações do sistema |
| `SHOW STATUS` | Mostra status do servidor | `SHOW STATUS` | Estado do servidor |
| `SHOW GRANTS` | Mostra permissões | `SHOW GRANTS FOR 'user'@'localhost'` | Permissões do usuário |

### 📝 Exemplo Prático: Análise de Estrutura
```sql
-- Listar todos os bancos de dados
SHOW DATABASES;                 # -----------------------> Lista bancos disponíveis

-- Selecionar banco de dados
USE meu_banco;                  # -----------------------> Seleciona banco atual

-- Listar todas as tabelas
SHOW TABLES;                    # -----------------------> Lista tabelas do banco

-- Ver estrutura detalhada
DESC usuarios;                  # -----------------------> Mostra estrutura da tabela
/* Resultado exemplo:
+----------+--------------+------+-----+---------+----------------+
| Field    | Type         | Null | Key | Default | Extra          |
+----------+--------------+------+-----+---------+----------------+
| id       | int(11)      | NO   | PRI | NULL    | auto_increment |
| nome     | varchar(100) | NO   |     | NULL    |                |
| email    | varchar(100) | YES  | UNI | NULL    |                |
+----------+--------------+------+-----+---------+----------------+
*/

-- Ver informações de índices
SHOW INDEX FROM usuarios;       # -----------------------> Lista índices da tabela

-- Ver DDL da tabela
SHOW CREATE TABLE usuarios\G    # -----------------------> Mostra comando de criação
```

> 💡 **Dica:** Use `\G` ao invés de `;` para visualizar resultados em formato vertical, especialmente útil para resultados longos

## ⚡ Melhores Práticas
| Prática | Descrição | Exemplo | Benefício |
|---------|-----------|---------|-----------|
| `Índices` | Criar índices | `CREATE INDEX idx_nome ON usuarios(nome)` | Acelera buscas |
| `EXPLAIN` | Analisar query | `EXPLAIN SELECT * FROM usuarios` | Identifica problemas |
| `Limit` | Limitar resultados | `SELECT * FROM logs LIMIT 1000` | Melhora performance |

> 💡 **Dica:** Use EXPLAIN antes de executar queries complexas em produção

## 📝 Exemplos Práticos

### Criação Completa de Banco de Dados
```sql
-- Criar novo banco de dados
CREATE DATABASE empresa         # -----------------------> Cria banco de dados
    DEFAULT CHARACTER SET utf8  # -----------------------> Define charset
    DEFAULT COLLATE utf8_general_ci; # -----------------> Define collation

-- Selecionar o banco de dados
USE empresa;                    # -----------------------> Seleciona o banco

-- Criar tabela de departamentos
CREATE TABLE departamentos (    # -----------------------> Cria tabela base
    id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
    localizacao VARCHAR(100)
);

-- Criar tabela de funcionários com foreign key
CREATE TABLE funcionarios (     # -----------------------> Cria tabela com relacionamento
    id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    salario DECIMAL(10,2),
    data_contratacao DATE DEFAULT CURRENT_DATE,
    departamento_id INT,
    FOREIGN KEY (departamento_id)      # -----------------------> Define chave estrangeira
        REFERENCES departamentos(id)    # -----------------------> Referencia tabela pai
        ON DELETE SET NULL             # -----------------------> Ação quando registro pai é deletado
        ON UPDATE CASCADE              # -----------------------> Ação quando registro pai é atualizado
);

-- Criar índices para otimização
CREATE INDEX idx_func_nome ON funcionarios(nome);  # ----> Índice para busca por nome
CREATE INDEX idx_func_dept ON funcionarios(departamento_id); # -> Índice para join

-- Inserir dados iniciais
INSERT INTO departamentos (nome, localizacao) VALUES 
    ('TI', 'Sala 101'),
    ('RH', 'Sala 102'),
    ('Vendas', 'Sala 103');

INSERT INTO funcionarios 
    (nome, email, salario, departamento_id) 
VALUES 
    ('João Silva', 'joao@empresa.com', 5000.00, 1),
    ('Maria Santos', 'maria@empresa.com', 6000.00, 1),
    ('Pedro Costa', 'pedro@empresa.com', 4500.00, 2);

-- Criar view para relatório
CREATE VIEW vw_funcionarios_dept AS  # -----------------------> Cria view
SELECT 
    f.nome as funcionario,
    f.salario,
    d.nome as departamento
FROM 
    funcionarios f
    INNER JOIN departamentos d ON d.id = f.departamento_id;
```

> 💡 **Dica:** Sempre planeje a estrutura do banco antes de criar as tabelas, considerando relacionamentos e índices necessários

### Comandos por SGBD
{{ ... seção de comandos por SGBD existente ... }}

## 📚 Links Úteis
- [📖 Documentação MySQL](https://dev.mysql.com/doc/)
- [📖 Documentação PostgreSQL](https://www.postgresql.org/docs/)
- [📝 W3Schools SQL Tutorial](https://www.w3schools.com/sql/)
- [🎓 SQL Zoo](https://sqlzoo.net/)
- [📘 Mode SQL Tutorial](https://mode.com/sql-tutorial/)
- [🔍 PostgreSQL Exercises](https://pgexercises.com/)
- [📊 SQLBolt](https://sqlbolt.com/)
- [🎯 HackerRank SQL](https://www.hackerrank.com/domains/sql)

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

```
