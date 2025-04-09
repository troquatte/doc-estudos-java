# 🚀 Desenvolvimento Web com Spring Boot

## Introdução

O **Spring Boot** é um poderoso framework que facilita o desenvolvimento de aplicações Java baseadas no Spring. Ele oferece configuração automática, inicialização rápida e produção pronta com o mínimo de configuração manual. Nesta seção, vamos explorar os principais componentes e funcionalidades que fazem parte do desenvolvimento web com Spring Boot, desde a criação de um projeto até a documentação da API.

---

## 🛠️ Criando um Projeto Spring Boot

Você pode criar um projeto Spring Boot de várias formas, mas a maneira mais comum é usando o [Spring Initializr](https://start.spring.io/). Nele, você seleciona as dependências necessárias para seu projeto e faz o download de um pacote `.zip` já pronto para importar na sua IDE.

**Dependências comuns para uma API REST:**

- `Spring Web`: fornece suporte para aplicações web, incluindo RESTful.
- `Spring Boot DevTools`: reinicialização automática e outras ferramentas de desenvolvimento.
- `Spring Data JPA`: integração com bancos de dados usando ORM.
- `H2 Database`: banco de dados em memória para testes.
- `Validation`: para validação de dados com Bean Validation.
- `Springdoc OpenAPI` ou `Springfox Swagger`: documentação da API.

## ⚙️ Spring Boot Starter e AutoConfiguração

O Spring Boot utiliza **Starters**, que são pacotes de dependências prontos para facilitar o desenvolvimento. Por exemplo:

- `spring-boot-starter-web`: Inclui Spring MVC, Tomcat (como servidor embutido), Jackson (para JSON), entre outros.
- `spring-boot-starter-data-jpa`: Inclui JPA e Hibernate para persistência de dados.

**Autoconfiguração**: O Spring Boot detecta as dependências no classpath e configura automaticamente os beans e propriedades padrão, permitindo que você escreva menos configuração manual.

## 🧱 Arquitetura Spring MVC

O Spring MVC segue o padrão **Model-View-Controller**, mesmo para APIs REST. Os componentes principais são:

### 📍 Controllers

Classes anotadas com `@RestController` ou `@Controller` que recebem as requisições HTTP e retornam respostas (geralmente em JSON).

```java
@RestController
@RequestMapping("/usuarios")
public class UsuarioController {
    @GetMapping
    public List<Usuario> listar() {
        return usuarioService.listarTodos();
    }
}
```

### 🧠 Services

Contêm a lógica de negócio. São anotados com `@Service`.

```java
@Service
public class UsuarioService {
    public List<Usuario> listarTodos() {
        return repository.findAll();
    }
}
```

### 💾 Repositories

Interfaces que acessam o banco de dados usando `JpaRepository` ou `CrudRepository`. Anotadas com `@Repository`.

```java
@Repository
public interface UsuarioRepository extends JpaRepository<Usuario, Long> {}
```

## 🔄 Manipulação de Requisições e Respostas (JSON, XML)

Por padrão, o Spring Boot usa o **Jackson** para converter objetos Java para JSON e vice-versa. Você pode usar a anotação `@RequestBody` para ler dados do corpo da requisição, e `@ResponseBody` (ou apenas retornar o objeto) para enviar a resposta.

```java
@PostMapping
public Usuario criar(@RequestBody Usuario usuario) {
    return usuarioService.salvar(usuario);
}
```

Para suportar XML, adicione a dependência:

```xml
<dependency>
    <groupId>com.fasterxml.jackson.dataformat</groupId>
    <artifactId>jackson-dataformat-xml</artifactId>
</dependency>
```

## ✅ Validação de Dados com Bean Validation

Use a especificação **Bean Validation (JSR-380)** com anotações como `@NotNull`, `@Size`, `@Email`, etc., para validar objetos.

```java
public class Usuario {
    @NotBlank
    private String nome;

    @Email
    private String email;
}
```

Use `@Valid` no controller para ativar a validação:

```java
@PostMapping
public ResponseEntity<Usuario> salvar(@Valid @RequestBody Usuario usuario) {
    return ResponseEntity.ok(usuarioService.salvar(usuario));
}
```

## 🚨 Manipulação de Erros e Exceções Globais

Você pode usar `@ControllerAdvice` para interceptar exceções e padronizar as respostas de erro da API.

```java
@ControllerAdvice
public class GlobalExceptionHandler {
    @ExceptionHandler(MethodArgumentNotValidException.class)
    public ResponseEntity<?> handleValidationError(MethodArgumentNotValidException ex) {
        List<String> erros = ex.getBindingResult()
            .getFieldErrors()
            .stream()
            .map(FieldError::getDefaultMessage)
            .toList();

        return ResponseEntity.badRequest().body(erros);
    }
}
```

## 📚 Documentação de API com Swagger / OpenAPI

Documentar sua API facilita o uso e o entendimento por outros desenvolvedores. Você pode usar bibliotecas como:

### Springdoc OpenAPI 3

Adicione ao `pom.xml`:

```xml
<dependency>
    <groupId>org.springdoc</groupId>
    <artifactId>springdoc-openapi-ui</artifactId>
    <version>1.7.0</version>
</dependency>
```

Depois, acesse:

```
http://localhost:8080/swagger-ui.html
```

Você pode documentar endpoints com anotações como `@Operation`, `@Parameter`, `@Schema`, etc.

```java
@Operation(summary = "Lista todos os usuários")
@GetMapping
public List<Usuario> listarUsuarios() {
    return service.listarTodos();
}
```

---

Com esses fundamentos bem compreendidos, você estará preparado para criar APIs REST robustas, seguras e bem documentadas com Spring Boot. 🚀
