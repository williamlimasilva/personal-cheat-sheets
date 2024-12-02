# 🔷 Cheat Sheet - C# .NET Commands.md

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

> 📝 Guia completo de C# e .NET Core/.NET 6+
> 📅 Última atualização: 2024
> 🔗 Versão: C# 12 / .NET 8

## 🚀 Recursos Modernos C# 12

<div class="container">
<div class="section">

### 🆕 Novos Recursos da Linguagem
| 🔍 Recurso | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `Primary Constructor` | Construtor na declaração | `class Person(string name, int age);` | Sintaxe simplificada |
| `Collection Expressions` | Sintaxe simplificada | `int[] numbers = [1, 2, 3];` | Array literal |
| `Alias Any Type` | Alias para qualquer tipo | `using Json = System.Text.Json.JsonDocument;` | Simplifica referências |
| `Inline Arrays` | Arrays em stack | `internal inline int[4] Vector;` | Performance |

<div class="example">
### 📝 Exemplo: Primary Constructor

```csharp
public class Person(string name, int age)
{
    public string Name { get; } = name;
    public int Age { get; } = age;
    
    public string Greet() => $"Hi, I'm {Name}, {Age} years old";
}
```
</div>

</div>
</div>

## 🛠️ Recursos Essenciais

<div class="container">
<div class="section">

### 📦 Records
| 🔍 Recurso | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `Record Class` | Classe imutável | `record Person(string Name, int Age);` | Imutabilidade |
| `with` | Cópia com mudanças | `person with { Age = 30 }` | Nova instância |
| `Record Struct` | Struct imutável | `readonly record struct Point(int X, int Y);` | Value type |

### ⚡ Pattern Matching
| 🔍 Padrão | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `is` | Verificação de tipo | `if (obj is string str)` | Type pattern |
| `switch` | Pattern matching | `object result = x switch { > 0 => "Positive" }` | Switch expression |
| `Property` | Match propriedades | `{ Name: "John", Age: > 18 }` | Property pattern |

<div class="example">
### 📝 Exemplo: Pattern Matching Avançado

```csharp
var result = shape switch
{
    Circle { Radius: > 0 } c => Math.PI * c.Radius * c.Radius,
    Rectangle { Width: var w, Height: var h } => w * h,
    _ => throw new ArgumentException("Unknown shape")
};
```
</div>

</div>
</div>

## 🧵 Programação Assíncrona

<div class="container">
<div class="section">

### 🔄 Async/Await
| 🔍 Recurso | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `async/await` | Operações assíncronas | `async Task<T> GetDataAsync()` | Assíncrono |
| `ValueTask` | Task otimizada | `ValueTask<int> GetValueAsync()` | Menos alocações |
| `IAsyncEnumerable` | Stream assíncrono | `await foreach (var item in GetItems())` | Streaming |

### ⚡ Parallel Programming
| 🔍 Recurso | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `Parallel.ForEach` | Loop paralelo | `Parallel.ForEach(items, item => Process(item))` | Paralelismo |
| `Task.WhenAll` | Múltiplas tasks | `await Task.WhenAll(tasks)` | Concorrência |
| `CancellationToken` | Cancelamento | `async Task Method(CancellationToken ct)` | Cancelável |

<div class="tip">
💡 **Dica:** Use ValueTask quando o resultado frequentemente estiver disponível de forma síncrona
</div>

</div>
</div>

## 🎯 LINQ e Coleções

<div class="container">
<div class="section">

### 📊 LINQ Moderno
| 🔍 Operador | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `=>` | Query sintax | `list.Where(x => x > 0)` | Filtragem |
| `MaxBy/MinBy` | Máximo/Mínimo | `people.MaxBy(p => p.Age)` | Elemento |
| `Chunk` | Dividir coleção | `list.Chunk(size: 3)` | Sub-arrays |
| `Index/Range` | Fatiamento | `list[^1]`, `list[1..4]` | Elementos |

### 🔄 Coleções Especializadas
| 🔍 Tipo | Descrição | Exemplo | Uso |
|------------|-----------|---------|-----------|
| `Span<T>` | Memória contígua | `Span<byte> buffer = stackalloc byte[100]` | Performance |
| `Memory<T>` | Memória gerenciada | `Memory<char> chars = text.AsMemory()` | Async ops |
| `ImmutableArray<T>` | Array imutável | `ImmutableArray.Create(1, 2, 3)` | Thread-safe |

</div>
</div>

## 🌐 ASP.NET Core

<div class="container">
<div class="section">

### 🔄 Minimal APIs
| 🔍 Recurso | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `MapGet` | Endpoint GET | `app.MapGet("/api/users", GetUsers)` | Rota GET |
| `Results` | Respostas HTTP | `Results.Ok(data)` | HTTP 200 |
| `Filters` | Middleware | `app.UseExceptionHandler()` | Error handling |

### 🚀 Endpoints Tipados
| 🔍 Recurso | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `IResult` | Retorno tipado | `Task<IResult> GetUser(int id)` | Tipo seguro |
| `FromRoute` | Binding route | `[FromRoute] int id` | Parâmetro |
| `FromBody` | Binding body | `[FromBody] UserDto user` | Request body |

<div class="example">
### 📝 Exemplo: Minimal API

```csharp
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.MapGet("/users/{id}", async (int id, IUserService users) =>
    await users.GetUser(id) is User user
        ? Results.Ok(user)
        : Results.NotFound());
```
</div>

</div>
</div>

## 🔒 Recursos Avançados

<div class="container">
<div class="section">

### 🎯 Generics Avançados
| 🔍 Recurso | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `where T : struct` | Constraint value | `where T : struct` | Apenas value types |
| `where T : new()` | Constraint construtor | `where T : new()` | Requer construtor |
| `default` | Valor padrão | `default(T)` | Valor default |

### 🛠️ Reflection e Metaprogramação
| 🔍 Recurso | Descrição | Exemplo | Resultado |
|------------|-----------|---------|-----------|
| `Source Generators` | Geração código | `[Generator] class MyGenerator` | Compile-time |
| `Expression Trees` | Árvores expressão | `Expression<Func<T, bool>>` | Dynamic queries |
| `Dynamic` | Tipagem dinâmica | `dynamic obj = GetObject()` | Runtime binding |

<div class="warning">
⚠️ **Atenção:** Use reflection com moderação devido ao impacto na performance
</div>

</div>
</div>

## 📚 Referências

- [📖 C# Documentation](https://docs.microsoft.com/en-us/dotnet/csharp/)
- [🔧 .NET API Browser](https://docs.microsoft.com/en-us/dotnet/api/)
- [🚀 ASP.NET Core Documentation](https://docs.microsoft.com/en-us/aspnet/core/)
- [💡 C# Language Features](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/)
