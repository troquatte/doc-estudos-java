# 🚀 Criando um Projeto Spring Boot do Zero

## Introdução

Spring Boot é um framework baseado no Spring que visa facilitar a criação de aplicações Java modernas, reduzindo a quantidade de configurações necessárias. Ele permite criar APIs RESTful, microsserviços, aplicações web e muito mais de forma simples, produtiva e escalável.

Neste guia, vamos construir um projeto Spring Boot do zero, passo a passo, explicando a finalidade de cada parte.

---

## ✅ Requisitos para Começar

Antes de iniciar, certifique-se de ter:

- **Java JDK 17** ou superior instalado
- **IDE** (recomenda-se IntelliJ IDEA, Eclipse ou VS Code)
- **Maven** ou **Gradle** (usaremos Maven neste exemplo)
- **Spring Initializr** (https://start.spring.io/) para gerar o projeto

---

## 📦 Estrutura do Projeto

A estrutura de pastas gerada é semelhante a:

```
meu-projeto/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/meuapp/
│   │   │       ├── MeuAppApplication.java
│   │   │       └── controller/
│   │   │       └── service/
│   │   │       └── repository/
│   │   └── resources/
│   │       ├── application.properties
│   │       └── static/
│   │       └── templates/
│   └── test/ (códigos de teste)
└── pom.xml (dependências do projeto)
```

---

## ⚙️ Criando o Projeto com Spring Initializr

Acesse [start.spring.io](https://start.spring.io/) e preencha os campos:

- **Project**: Maven
- **Language**: Java
- **Spring Boot**: 3.1.0 ou superior
- **Group**: com.meuapp
- **Artifact**: meu-projeto
- **Name**: meu-projeto
- **Description**: Meu primeiro projeto Spring Boot
- **Packaging**: Jar
- **Java**: 17

### Dependências para adicionar:

- Spring Web
- Spring Boot DevTools
- Spring Data JPA
- H2 Database (ou PostgreSQL, caso deseje usar banco externo)
- Lombok

Clique em **Generate** para baixar o `.zip` do projeto.

---

## 🧱 Estrutura Mínima da Aplicação

### 1️⃣ Classe Principal

```java
@SpringBootApplication
public class MeuAppApplication {
    public static void main(String[] args) {
        SpringApplication.run(MeuAppApplication.class, args);
    }
}
```

### 2️⃣ Controller (Camada de entrada)

```java
@RestController
@RequestMapping("/api")
public class HelloController {
    @GetMapping("/hello")
    public String hello() {
        return "Hello, Spring Boot!";
    }
}
```

### 3️⃣ Service (Regra de negócio)

```java
@Service
public class HelloService {
    public String gerarSaudacao() {
        return "Bem-vindo ao Spring Boot!";
    }
}
```

### 4️⃣ Repository (Persistência de dados)

```java
@Repository
public interface UsuarioRepository extends JpaRepository<Usuario, Long> {
    Optional<Usuario> findByEmail(String email);
}
```

### 5️⃣ Entity (Modelo de dados)

```java
@Entity
@Data
@NoArgsConstructor
@AllArgsConstructor
public class Usuario {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String nome;

    private String email;
}
```

---

## 🛠 Configurando o application.properties

```properties
# Porta da aplicação
server.port=8080

# Configurações do H2
spring.h2.console.enabled=true
spring.h2.console.path=/h2

# Configuração JPA
spring.jpa.hibernate.ddl-auto=update
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
```

---

## 🧪 Testando sua aplicação

Inicie a aplicação com o botão **Run** da sua IDE ou via terminal:

```bash
./mvnw spring-boot:run
```

Acesse:

- [http://localhost:8080/api/hello](http://localhost:8080/api/hello) → Rota de teste
- [http://localhost:8080/h2](http://localhost:8080/h2) → Console H2 (login: `sa`, sem senha)

---

## 🧩 Como funcionam as dependências (Maven)

No arquivo `pom.xml`, estão listadas as dependências do projeto. Por exemplo:

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

Esses _starters_ são coleções de dependências agrupadas para facilitar a configuração.

### Principais starters:

- `spring-boot-starter-web`: suporte a API REST e Spring MVC
- `spring-boot-starter-data-jpa`: integração com banco de dados usando JPA/Hibernate
- `spring-boot-starter-test`: dependências para testes
- `spring-boot-devtools`: recarregamento automático em dev
- `lombok`: gera getters/setters automaticamente

---

## 🧠 Dicas Adicionais

- Use o `@Slf4j` do Lombok para logging
- Separe bem as camadas: controller, service, repository
- Evite lógica de negócio em controllers
- Configure `DTOs` para entrada e saída de dados
- Utilize o `ModelMapper` para conversão entre entidades e DTOs

---

## 📚 Leitura Recomendada

- [Documentação Oficial Spring Boot](https://spring.io/projects/spring-boot)
- [Baeldung - Spring Boot Guide](https://www.baeldung.com/spring-boot-start)

---

Com esse guia você tem uma base sólida para começar seu primeiro projeto com Spring Boot. Agora é só codar! ✨
