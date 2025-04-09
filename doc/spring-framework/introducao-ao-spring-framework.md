# 📖 Introdução ao Spring Framework

## Introdução

O Spring Framework é um dos frameworks mais populares e poderosos do ecossistema Java. Ele oferece uma ampla gama de funcionalidades para desenvolver aplicações Java modernas, modulares e escaláveis, desde APIs REST até sistemas corporativos completos. Com foco em injeção de dependência e inversão de controle, o Spring torna o código mais limpo, testável e de fácil manutenção.

## Principais Características do Spring

O Spring Framework é composto por diversos módulos. Alguns dos principais são:

- **Core Container**: Fornece os recursos de Inversão de Controle (IoC) e Injeção de Dependência (DI).
- **Spring MVC**: Permite criar aplicações web baseadas em arquitetura MVC (Model-View-Controller).
- **Spring Data**: Facilita a integração com bancos de dados relacionais e NoSQL.
- **Spring Security**: Adiciona autenticação e autorização às aplicações.
- **Spring Boot**: Abstrai configurações complexas para iniciar projetos de forma rápida e eficiente.

## Inversão de Controle (IoC) e Injeção de Dependência (DI)

O coração do Spring é a inversão de controle. Em vez de o código criar dependências diretamente, o Spring as fornece automaticamente.

### Exemplo:

```java
@Component
public class MeuServico {
    public void executar() {
        System.out.println("Executando serviço...");
    }
}

@RestController
public class MeuController {
    private final MeuServico servico;

    public MeuController(MeuServico servico) {
        this.servico = servico;
    }

    @GetMapping("/executar")
    public String executar() {
        servico.executar();
        return "Serviço executado!";
    }
}
```

## Spring Boot

O Spring Boot é uma extensão do Spring que visa simplificar a criação de aplicações. Ele vem com:

- Autoconfiguração
- Servidor embutido (Tomcat, Jetty)
- Dependências agrupadas via **starters**

### Exemplo de Classe Principal:

```java
@SpringBootApplication
public class MinhaAplicacao {
    public static void main(String[] args) {
        SpringApplication.run(MinhaAplicacao.class, args);
    }
}
```

## Spring MVC

Com o Spring MVC é possível criar controladores que respondem a requisições HTTP, facilitando a criação de APIs RESTful.

### Exemplo de Controller REST:

```java
@RestController
@RequestMapping("/api")
public class ApiController {

    @GetMapping("/hello")
    public String hello() {
        return "Olá, Spring!";
    }
}
```

## Spring Data JPA

O Spring Data JPA facilita o acesso a dados usando repositórios baseados em interfaces.

### Exemplo:

```java
@Entity
public class Usuario {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String nome;
}

public interface UsuarioRepository extends JpaRepository<Usuario, Long> {
    List<Usuario> findByNome(String nome);
}
```

## Spring Security

Com Spring Security você pode proteger endpoints e definir regras de autenticação e autorização com facilidade.

### Exemplo:

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
                .anyRequest().authenticated()
                .and()
            .httpBasic();
    }
}
```

## 🎯 Exercícios Práticos

**1 - Criar uma aplicação Spring Boot simples**

- Use o Spring Initializr (https://start.spring.io) para gerar um projeto.
- Adicione uma rota REST que retorna uma mensagem simples.

**2 - Utilizar Injeção de Dependência**

- Crie uma classe de serviço anotada com `@Service`.
- Injetar essa classe em um controller usando o construtor.

**3 - Criar uma entidade e repositório JPA**

- Crie uma classe `Produto` com id, nome e preço.
- Use `JpaRepository` para gerenciar os produtos.

**4 - Adicionar segurança básica**

- Configure o Spring Security para proteger todas as rotas.
- Use autenticação HTTP básica com um usuário definido na configuração.

## 📚 Leitura Recomendada

- [Documentação Oficial do Spring](https://spring.io/projects/spring-framework)
- [Guia Rápido do Spring Boot](https://spring.io/quickstart)

---

Com esse conhecimento, você estará preparado para desenvolver aplicações modernas e robustas com o poder do Spring! 🚀
