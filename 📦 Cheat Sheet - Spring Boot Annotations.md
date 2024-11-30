# 📦 Cheat Sheet - Spring Boot Annotations

> 📚 Um guia completo sobre as Annotations do Spring Boot

## 📑 Índice
1. [Anotações de Configuração](#anotações-de-configuração)
2. [Anotações de Componentes](#anotações-de-componentes)
3. [Anotações Web](#anotações-web)
4. [Anotações de Dados](#anotações-de-dados)
5. [Anotações de Segurança](#anotações-de-segurança)
6. [Anotações de Teste](#anotações-de-teste)

## Anotações de Configuração

### Configuração Principal
| Anotação | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@SpringBootApplication` | Combina @Configuration, @EnableAutoConfiguration e @ComponentScan | `@SpringBootApplication public class App` | Classe principal |
| `@Configuration` | Define classe de configuração | `@Configuration public class Config` | Configurações |
| `@EnableAutoConfiguration` | Habilita auto-configuração | `@EnableAutoConfiguration` | Auto-config |
| `@ComponentScan` | Define pacotes para scan | `@ComponentScan("com.app")` | Scan de componentes |

### Propriedades e Perfis
| Anotação | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@ConfigurationProperties` | Liga propriedades a classe | `@ConfigurationProperties(prefix = "app")` | Config externa |
| `@Value` | Injeta valor de propriedade | `@Value("${app.name}")` | Valor específico |
| `@Profile` | Define perfil específico | `@Profile("dev")` | Ambiente específico |
| `@PropertySource` | Carrega arquivo properties | `@PropertySource("classpath:custom.properties")` | Config adicional |

## Anotações de Componentes

### Componentes Básicos
| Anotação | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@Component` | Marca classe como componente | `@Component class Service` | Componente genérico |
| `@Service` | Marca classe como serviço | `@Service class UserService` | Camada de serviço |
| `@Repository` | Marca classe como repositório | `@Repository class UserRepo` | Acesso a dados |
| `@Controller` | Marca classe como controller | `@Controller class UserCtrl` | Controller MVC |
| `@RestController` | Controller REST | `@RestController class ApiCtrl` | API REST |

### Injeção de Dependências
| Anotação | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@Autowired` | Injeta dependência | `@Autowired UserService service` | Injeção automática |
| `@Qualifier` | Especifica qual bean injetar | `@Qualifier("userServiceImpl")` | Bean específico |
| `@Primary` | Define bean primário | `@Primary @Service class MainService` | Bean preferencial |
| `@DependsOn` | Define dependências de bean | `@DependsOn("otherBean")` | Ordem de criação |
| `@Lazy` | Inicialização preguiçosa | `@Lazy @Service class HeavyService` | Carregamento tardio |

## Anotações Web

### Mapeamento de Requisições
| Anotação | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@RequestMapping` | Mapeia requisições | `@RequestMapping("/api")` | Mapeamento geral |
| `@GetMapping` | Mapeia GET | `@GetMapping("/users")` | Buscar dados |
| `@PostMapping` | Mapeia POST | `@PostMapping("/users")` | Criar dados |
| `@PutMapping` | Mapeia PUT | `@PutMapping("/users/{id}")` | Atualizar dados |
| `@DeleteMapping` | Mapeia DELETE | `@DeleteMapping("/users/{id}")` | Deletar dados |
| `@PatchMapping` | Mapeia PATCH | `@PatchMapping("/users/{id}")` | Atualização parcial |

### Parâmetros de Requisição
| Anotação | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@PathVariable` | Variável de caminho | `@PathVariable Long id` | Parâmetro na URL |
| `@RequestParam` | Parâmetro de query | `@RequestParam String name` | Query string |
| `@RequestBody` | Corpo da requisição | `@RequestBody User user` | Dados JSON/XML |
| `@RequestHeader` | Header da requisição | `@RequestHeader String token` | Header HTTP |
| `@CookieValue` | Valor de cookie | `@CookieValue String sessionId` | Cookie |

### Respostas e Validação
| Anotação | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@ResponseBody` | Corpo da resposta | `@ResponseBody User getUser()` | Resposta direta |
| `@ResponseStatus` | Status HTTP | `@ResponseStatus(HttpStatus.CREATED)` | Status específico |
| `@Valid` | Validação de objeto | `@Valid @RequestBody User user` | Validação |
| `@ExceptionHandler` | Trata exceções | `@ExceptionHandler(Exception.class)` | Tratamento de erro |
| `@ControllerAdvice` | Controlador global | `@ControllerAdvice class ErrorHandler` | Tratamento global |

## Anotações de Dados

### JPA e Persistência
| Anotação | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@Entity` | Define entidade JPA | `@Entity class User` | Mapeamento ORM |
| `@Table` | Define tabela | `@Table(name = "users")` | Nome da tabela |
| `@Id` | Define chave primária | `@Id Long id` | Identificador |
| `@GeneratedValue` | Geração de ID | `@GeneratedValue(strategy = AUTO)` | Auto incremento |
| `@Column` | Define coluna | `@Column(name = "user_name")` | Coluna específica |

### Spring Data
| Anotação | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@Transactional` | Define transação | `@Transactional void save()` | Controle transacional |
| `@Query` | Query personalizada | `@Query("SELECT u FROM User u")` | JPQL/SQL |
| `@Modifying` | Permite modificação | `@Modifying @Query` | Update/Delete |
| `@NoRepositoryBean` | Repositório abstrato | `@NoRepositoryBean interface Base` | Repo base |
| `@Param` | Nomeia parâmetro | `@Param("name") String name` | Parâmetro em query |

## Anotações de Segurança

### Configuração de Segurança
| Anotação | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@EnableWebSecurity` | Habilita segurança web | `@EnableWebSecurity class Config` | Config segurança |
| `@EnableGlobalMethodSecurity` | Segurança em métodos | `@EnableGlobalMethodSecurity(prePostEnabled = true)` | Segurança métodos |
| `@Secured` | Define roles permitidas | `@Secured("ROLE_ADMIN")` | Restrição de acesso |
| `@PreAuthorize` | Autorização prévia | `@PreAuthorize("hasRole('ADMIN')")` | Autorização SpEL |
| `@PostAuthorize` | Autorização posterior | `@PostAuthorize("returnObject.owner == principal.username")` | Verificação pós |

### Autenticação
| Anotação | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@AuthenticationPrincipal` | Principal atual | `@AuthenticationPrincipal User user` | Usuário logado |
| `@CurrentUser` | Usuário atual | `@CurrentUser CustomUser user` | Usuário customizado |
| `@Async` | Método assíncrono | `@Async void process()` | Processamento async |
| `@EnableAsync` | Habilita async | `@EnableAsync class Config` | Config async |

## Anotações de Teste

### Configuração de Testes
| Anotação | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@SpringBootTest` | Teste de integração | `@SpringBootTest class TestClass` | Teste completo |
| `@WebMvcTest` | Teste de MVC | `@WebMvcTest(UserController.class)` | Teste controller |
| `@DataJpaTest` | Teste de JPA | `@DataJpaTest class RepoTest` | Teste repositório |
| `@MockBean` | Mock de bean | `@MockBean UserService service` | Mock de componente |
| `@SpyBean` | Spy de bean | `@SpyBean UserService service` | Spy de componente |

### Execução de Testes
| Anotação | Descrição | Exemplo | Uso |
|----------|-----------|---------|-----|
| `@Test` | Define método de teste | `@Test void testMethod()` | Método de teste |
| `@BeforeEach` | Antes de cada teste | `@BeforeEach void setup()` | Setup de teste |
| `@AfterEach` | Após cada teste | `@AfterEach void cleanup()` | Limpeza de teste |
| `@DirtiesContext` | Reseta contexto | `@DirtiesContext` | Reset de contexto |
| `@ActiveProfiles` | Define perfil ativo | `@ActiveProfiles("test")` | Perfil de teste |

### Exemplos Práticos

#### Configuração Básica
```java
@SpringBootApplication
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

#### Controller REST
```java
@RestController
@RequestMapping("/api/users")
public class UserController {
    @Autowired
    private UserService userService;
    
    @GetMapping("/{id}")
    public ResponseEntity<User> getUser(@PathVariable Long id) {
        return ResponseEntity.ok(userService.findById(id));
    }
    
    @PostMapping
    @ResponseStatus(HttpStatus.CREATED)
    public User createUser(@Valid @RequestBody User user) {
        return userService.save(user);
    }
}
```

#### Serviço Transacional
```java
@Service
@Transactional
public class UserService {
    @Autowired
    private UserRepository repository;
    
    @PreAuthorize("hasRole('ADMIN')")
    public User save(User user) {
        return repository.save(user);
    }
}
```

#### Entidade JPA
```java
@Entity
@Table(name = "users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    @Column(nullable = false)
    private String username;
    
    @OneToMany(mappedBy = "user", cascade = CascadeType.ALL)
    private List<Order> orders;
}
```

#### Teste de Integração
```java
@SpringBootTest
@AutoConfigureMockMvc
class UserControllerTest {
    @Autowired
    private MockMvc mockMvc;
    
    @MockBean
    private UserService userService;
    
    @Test
    void shouldCreateUser() throws Exception {
        // given
        User user = new User("test");
        when(userService.save(any())).thenReturn(user);
        
        // when/then
        mockMvc.perform(post("/api/users")
                .contentType(MediaType.APPLICATION_JSON)
                .content("{\"username\":\"test\"}"))
                .andExpect(status().isCreated());
    }
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
