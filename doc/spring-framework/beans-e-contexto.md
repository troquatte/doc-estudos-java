# 📖 Beans e Contexto de Aplicação em Java (Spring Framework)

## Introdução

No ecossistema do Spring Framework, os **Beans** e o **Contexto de Aplicação** são pilares fundamentais para a construção de aplicações Java robustas, modulares e testáveis. Eles fazem parte do mecanismo de Injeção de Dependência, que promove o desacoplamento entre os componentes da aplicação.

## O que é um Bean?

Um **Bean** é um objeto gerenciado pelo container do Spring. Ele é instanciado, configurado e gerenciado automaticamente, conforme as definições feitas no código (via anotações) ou em arquivos de configuração.

### Como declarar um Bean?

Existem diversas formas de declarar um Bean em Spring:

#### ✅ Anotação `@Component`

```java
@Component
public class MeuServico {
    public void executar() {
        System.out.println("Executando MeuServico");
    }
}
```

#### ✅ Anotação `@Service`, `@Repository`, `@Controller`

Essas são especializações de `@Component`, usadas para indicar papéis específicos:

- `@Service`: lógica de negócio.
- `@Repository`: acesso a dados.
- `@Controller`: controle de requisições web.

#### ✅ Método com `@Bean` dentro de classe `@Configuration`

```java
@Configuration
public class ConfiguracaoApp {
    @Bean
    public MeuServico meuServico() {
        return new MeuServico();
    }
}
```

## Contexto de Aplicação (ApplicationContext)

O **ApplicationContext** é o container do Spring responsável por instanciar, configurar e montar os beans definidos na aplicação. Ele também gerencia o ciclo de vida dos beans e suas dependências.

### Principais responsabilidades:

- Instanciar Beans.
- Resolver dependências entre Beans.
- Gerenciar escopos (`singleton`, `prototype`, etc).
- Fornecer recursos como eventos e mensagens.

### Inicialização com `AnnotationConfigApplicationContext`

```java
ApplicationContext context = new AnnotationConfigApplicationContext(ConfiguracaoApp.class);
MeuServico servico = context.getBean(MeuServico.class);
servico.executar();
```

## Escopos de Beans

Por padrão, os Beans são **singleton** (uma única instância compartilhada). Outros escopos incluem:

| Escopo      | Descrição                                             |
| ----------- | ----------------------------------------------------- |
| `singleton` | Uma instância única para todo o contexto              |
| `prototype` | Nova instância cada vez que for solicitado            |
| `request`   | Uma instância por requisição HTTP (em aplicações web) |
| `session`   | Uma instância por sessão HTTP (em aplicações web)     |

### Exemplo de escopo:

```java
@Component
@Scope("prototype")
public class RecursoTemporario {
    // Novo objeto a cada requisição ao ApplicationContext
}
```

## Ciclo de Vida de um Bean

O Spring permite executar código no momento da **inicialização** e da **destruição** de um Bean:

```java
@Component
public class CicloBean {
    @PostConstruct
    public void iniciar() {
        System.out.println("Bean inicializado");
    }

    @PreDestroy
    public void destruir() {
        System.out.println("Bean destruído");
    }
}
```

## Injeção de Dependência com `@Autowired`

```java
@Component
public class Controlador {
    private final MeuServico servico;

    @Autowired
    public Controlador(MeuServico servico) {
        this.servico = servico;
    }
}
```

> Dica: Desde o Spring 4.3, a anotação `@Autowired` é opcional em construtores com apenas um parâmetro.

## 📚 Leitura Recomendada

- [Documentação Oficial do Spring - ApplicationContext](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#context-introduction)
- [Spring Beans and Dependency Injection](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-introduction)

---

Com o entendimento sobre Beans e o Contexto de Aplicação, você está pronto para explorar conceitos mais avançados como AOP, eventos do Spring e integrações com bancos de dados! 🚀
