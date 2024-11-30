# 📝 Cheat Sheet - Java Annotations

> 📚 Um guia completo sobre Annotations (Anotações) em Java

## 📑 Índice
1. [Conceitos Básicos](#conceitos-básicos)
2. [Anotações Internas do Java](#anotações-internas-do-java)
3. [Meta-Anotações](#meta-anotações)
4. [Criando Anotações Customizadas](#criando-anotações-customizadas)
5. [Processamento de Anotações](#processamento-de-anotações)
6. [Casos de Uso Comuns](#casos-de-uso-comuns)

## Conceitos Básicos

### O que são Annotations?

| Conceito | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@interface` | Define uma anotação | `public @interface MinhaAnotacao {}` | Declaração de anotação |
| `@Anotacao` | Uso de anotação | `@Override` | Aplicação em elemento |
| `Elemento` | Atributo da anotação | `value()` | Define valor da anotação |

### Sintaxe Básica
```java
// Anotação simples
@NomeAnotacao

// Anotação com elemento
@NomeAnotacao(elemento = "valor")

// Anotação com valor default
@NomeAnotacao("valor")    // Equivalente a @NomeAnotacao(value = "valor")
```

## Anotações Internas do Java

### Anotações Fundamentais
| Anotação | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@Override` | Indica sobrescrita de método | `@Override void metodo()` | Validação em tempo de compilação |
| `@Deprecated` | Marca elemento como obsoleto | `@Deprecated class Antiga` | Aviso de uso desencorajado |
| `@SuppressWarnings` | Suprime avisos do compilador | `@SuppressWarnings("unchecked")` | Ignora warnings específicos |
| `@FunctionalInterface` | Marca interface funcional | `@FunctionalInterface interface Runnable` | Validação de interface funcional |
| `@SafeVarargs` | Suprime warnings de varargs | `@SafeVarargs final <T> void metodo(T... args)` | Segurança com varargs genéricos |

### Anotações de Documentação
| Anotação | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@author` | Especifica autor | `@author João Silva` | Documentação JavaDoc |
| `@version` | Versão do elemento | `@version 1.0` | Controle de versão |
| `@since` | Desde qual versão existe | `@since 1.8` | Compatibilidade |
| `@see` | Referência a outro elemento | `@see OutraClasse` | Referência cruzada |
| `@param` | Documenta parâmetro | `@param nome descrição` | Documentação de parâmetro |
| `@return` | Documenta retorno | `@return descrição` | Documentação de retorno |
| `@throws` | Documenta exceção | `@throws Exception descrição` | Documentação de exceção |

## Meta-Anotações

### @Target
| Valor | Descrição | Exemplo | Uso |
|-------|-----------|---------|-----|
| `ElementType.TYPE` | Classes, interfaces, enums | `@Target(ElementType.TYPE)` | Anotação em tipos |
| `ElementType.FIELD` | Campos | `@Target(ElementType.FIELD)` | Anotação em campos |
| `ElementType.METHOD` | Métodos | `@Target(ElementType.METHOD)` | Anotação em métodos |
| `ElementType.PARAMETER` | Parâmetros | `@Target(ElementType.PARAMETER)` | Anotação em parâmetros |
| `ElementType.CONSTRUCTOR` | Construtores | `@Target(ElementType.CONSTRUCTOR)` | Anotação em construtores |
| `ElementType.LOCAL_VARIABLE` | Variáveis locais | `@Target(ElementType.LOCAL_VARIABLE)` | Anotação em variáveis |
| `ElementType.ANNOTATION_TYPE` | Anotações | `@Target(ElementType.ANNOTATION_TYPE)` | Meta-anotação |
| `ElementType.PACKAGE` | Pacotes | `@Target(ElementType.PACKAGE)` | Anotação em pacotes |
| `ElementType.TYPE_PARAMETER` | Parâmetros de tipo | `@Target(ElementType.TYPE_PARAMETER)` | Anotação em genéricos |
| `ElementType.TYPE_USE` | Uso de tipos | `@Target(ElementType.TYPE_USE)` | Anotação em qualquer tipo |

### @Retention
| Valor | Descrição | Exemplo | Uso |
|-------|-----------|---------|-----|
| `RetentionPolicy.SOURCE` | Apenas no código fonte | `@Retention(RetentionPolicy.SOURCE)` | Descartada na compilação |
| `RetentionPolicy.CLASS` | Mantida no bytecode | `@Retention(RetentionPolicy.CLASS)` | Disponível no .class |
| `RetentionPolicy.RUNTIME` | Disponível em runtime | `@Retention(RetentionPolicy.RUNTIME)` | Acessível via Reflection |

### Outras Meta-Anotações
| Anotação | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@Documented` | Inclui na documentação | `@Documented @interface Minha` | JavaDoc |
| `@Inherited` | Permite herança | `@Inherited @interface Pai` | Herança de anotações |
| `@Repeatable` | Permite repetição | `@Repeatable(Valores.class)` | Múltiplas ocorrências |

## Criando Anotações Customizadas

### Anotação Simples
```java
@Target(ElementType.METHOD)
@Retention(RetentionPolicy.RUNTIME)
public @interface Logger {
    String value() default "";
}
```

### Anotação com Elementos
```java
@Target({ElementType.TYPE, ElementType.METHOD})
@Retention(RetentionPolicy.RUNTIME)
@Documented
public @interface ApiEndpoint {
    String path();
    String method() default "GET";
    boolean deprecated() default false;
    String[] consumes() default {};
    String[] produces() default {};
}
```

### Anotação Repetível
```java
// Container
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
public @interface Roles {
    Role[] value();
}

// Anotação repetível
@Repeatable(Roles.class)
public @interface Role {
    String value();
    boolean admin() default false;
}

// Uso
@Role("USER")
@Role(value = "ADMIN", admin = true)
public class Usuario { }
```

## Processamento de Anotações

### Reflection API
```java
public class AnnotationProcessor {
    public static void processClass(Class<?> clazz) {
        // Obtendo anotações da classe
        Annotation[] annotations = clazz.getAnnotations();
        
        // Verificando anotação específica
        if (clazz.isAnnotationPresent(ApiEndpoint.class)) {
            ApiEndpoint api = clazz.getAnnotation(ApiEndpoint.class);
            System.out.println("Path: " + api.path());
        }
        
        // Processando métodos anotados
        for (Method method : clazz.getDeclaredMethods()) {
            if (method.isAnnotationPresent(Logger.class)) {
                Logger logger = method.getAnnotation(Logger.class);
                System.out.println("Logger: " + logger.value());
            }
        }
    }
}
```

### Annotation Processor
```java
@SupportedAnnotationTypes("com.exemplo.MinhaAnotacao")
@SupportedSourceVersion(SourceVersion.RELEASE_11)
public class MeuProcessor extends AbstractProcessor {
    @Override
    public boolean process(Set<? extends TypeElement> annotations, 
                         RoundEnvironment roundEnv) {
        for (TypeElement annotation : annotations) {
            Set<? extends Element> elementos = 
                roundEnv.getElementsAnnotatedWith(annotation);
            
            for (Element elemento : elementos) {
                // Processamento em tempo de compilação
                processar(elemento);
            }
        }
        return true;
    }
    
    private void processar(Element elemento) {
        // Lógica de processamento
    }
}
```

## Casos de Uso Comuns

### Validação
```java
@Target(ElementType.FIELD)
@Retention(RetentionPolicy.RUNTIME)
public @interface NotNull {
    String message() default "Campo não pode ser nulo";
}

@Target(ElementType.FIELD)
@Retention(RetentionPolicy.RUNTIME)
public @interface Length {
    int min() default 0;
    int max() default Integer.MAX_VALUE;
    String message() default "Tamanho inválido";
}
```

### Injeção de Dependências
```java
@Target(ElementType.FIELD)
@Retention(RetentionPolicy.RUNTIME)
public @interface Autowired {
    boolean required() default true;
}

@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
public @interface Component {
    String value() default "";
}
```

### Mapeamento ORM
```java
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
public @interface Entity {
    String table() default "";
}

@Target(ElementType.FIELD)
@Retention(RetentionPolicy.RUNTIME)
public @interface Column {
    String name() default "";
    boolean nullable() default true;
    int length() default 255;
}

@Target(ElementType.FIELD)
@Retention(RetentionPolicy.RUNTIME)
public @interface Id {
    String generator() default "auto";
}
```

### Testes
```java
@Target(ElementType.METHOD)
@Retention(RetentionPolicy.RUNTIME)
public @interface Test {
    Class<? extends Throwable> expected() default None.class;
    long timeout() default 0L;
}

@Target(ElementType.METHOD)
@Retention(RetentionPolicy.RUNTIME)
public @interface Before {
}

@Target(ElementType.METHOD)
@Retention(RetentionPolicy.RUNTIME)
public @interface After {
}
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
