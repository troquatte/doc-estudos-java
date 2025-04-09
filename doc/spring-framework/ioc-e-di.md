# ⚖️ Inversão de Controle (IoC) e Injeção de Dependência (DI) em Java

## Introdução

A Inversão de Controle (IoC) e a Injeção de Dependência (DI) são padrões fundamentais para o desenvolvimento de aplicações flexíveis, testáveis e desacopladas em Java. Esses conceitos são amplamente utilizados em frameworks como Spring.

## O que é Inversão de Controle (IoC)?

A IoC é um princípio onde o controle do fluxo de execução e da instanciação de objetos é transferido para um contêiner ou framework, em vez de ser feito manualmente pelo desenvolvedor.

### Exemplo tradicional (sem IoC):

```java
class Motor {
    public void ligar() {
        System.out.println("Motor ligado");
    }
}

class Carro {
    private Motor motor;

    public Carro() {
        this.motor = new Motor(); // Acoplamento forte
    }

    public void ligar() {
        motor.ligar();
    }
}
```

### Com IoC (usando DI):

```java
class Carro {
    private Motor motor;

    // Injeção via construtor
    public Carro(Motor motor) {
        this.motor = motor;
    }

    public void ligar() {
        motor.ligar();
    }
}
```

## O que é Injeção de Dependência (DI)?

DI é uma forma de implementar IoC. Em vez da própria classe criar suas dependências, elas são fornecidas de fora.

### Tipos de Injeção:

| Tipo            | Descrição                                        |
| --------------- | ------------------------------------------------ |
| Construtor      | Dependências são passadas pelo construtor.       |
| Setter (método) | Dependências são passadas via métodos `set`.     |
| Interface       | Define uma interface para injeção (menos comum). |

## Benefícios do uso de IoC e DI

- Redução do acoplamento entre classes
- Facilita testes unitários (mock de dependências)
- Aumenta a manutenção e reutilização de código
- Melhor organização do sistema

## IoC Container

Um IoC container é um framework que gerencia o ciclo de vida e as dependências de objetos automaticamente.

### Exemplo com Spring:

```java
@Component
class Motor {
    public void ligar() {
        System.out.println("Motor ligado com Spring");
    }
}

@Component
class Carro {
    private final Motor motor;

    @Autowired
    public Carro(Motor motor) {
        this.motor = motor;
    }

    public void ligar() {
        motor.ligar();
    }
}
```

### Configuração do contexto:

```java
ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);
Carro carro = context.getBean(Carro.class);
carro.ligar();
```

## Desvantagens e Cuidados

- Maior curva de aprendizado (principalmente com frameworks)
- Pode ocultar a complexidade do código
- Mau uso pode levar a problemas de performance

## 🎯 Exercícios Práticos

**1 - Implementação manual de DI**

- Crie uma classe `Computador` que depende de `Processador` e `MemoriaRAM`.
- Injete essas dependências via construtor.

**2 - Testes com IoC**

- Crie um projeto Spring e use `@Component` e `@Autowired` para montar uma aplicação simples de `Loja` e `Produto`.

## 📚 Leitura Recomendada

- [Documentação Oficial Spring](https://spring.io/projects/spring-framework)

---

Compreender e aplicar IoC e DI em Java é um passo essencial para escrever código limpo, escalável e testável. Com a prática, esses conceitos se tornam naturais no dia a dia de um desenvolvedor Java profissional. ✨
