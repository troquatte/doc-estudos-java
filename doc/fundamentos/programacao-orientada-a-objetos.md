# 🏛️ Programação Orientada a Objetos (POO) Básico em Java

## 1️⃣ Introdução à POO

A Programação Orientada a Objetos (POO) é um paradigma de programação baseado no conceito de **objetos**, que representam entidades do mundo real. Em Java, a POO é fundamental e se baseia em quatro pilares:

- **Encapsulamento**
- **Herança**
- **Polimorfismo**
- **Abstração**

## 2️⃣ Classes e Objetos

### O que são Classes?

Uma **classe** é um modelo para criar objetos. Ela define atributos (variáveis) e comportamentos (métodos).

```java
class Carro {
    String marca;
    int ano;

    void acelerar() {
        System.out.println("O carro está acelerando...");
    }
}
```

### O que são Objetos?

Um **objeto** é uma instância de uma classe.

```java
public class Main {
    public static void main(String[] args) {
        Carro meuCarro = new Carro(); // Criando um objeto
        meuCarro.marca = "Toyota";
        meuCarro.ano = 2022;
        meuCarro.acelerar();
    }
}
```

## 3️⃣ Encapsulamento

O **encapsulamento** protege os dados dentro de uma classe e controla o acesso a eles.

### Modificadores de Acesso

| Modificador       | Descrição                                            |
| ----------------- | ---------------------------------------------------- |
| `public`          | Acesso livre a partir de qualquer classe             |
| `private`         | Acesso permitido apenas dentro da própria classe     |
| `protected`       | Acesso permitido dentro do mesmo pacote e subclasses |
| (sem modificador) | Acesso permitido apenas dentro do mesmo pacote       |

### Exemplo de Encapsulamento

```java
class Pessoa {
    private String nome;

    public void setNome(String nome) {
        this.nome = nome;
    }

    public String getNome() {
        return nome;
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        Pessoa p = new Pessoa();
        p.setNome("João");
        System.out.println(p.getNome());
    }
}
```

## 4️⃣ Herança

A **herança** permite que uma classe herde atributos e métodos de outra.

```java
class Animal {
    void comer() {
        System.out.println("Comendo...");
    }
}

class Cachorro extends Animal {
    void latir() {
        System.out.println("Au au!");
    }
}
```

### Criando e Usando um Objeto Herdado

```java
public class Main {
    public static void main(String[] args) {
        Cachorro dog = new Cachorro();
        dog.comer(); // Herdado da classe Animal
        dog.latir(); // Método próprio da classe Cachorro
    }
}
```

## 5️⃣ Polimorfismo

O **polimorfismo** permite que métodos tenham diferentes comportamentos dependendo do contexto.

### Exemplo de Polimorfismo com Sobrescrita de Método

```java
class Animal {
    void fazerSom() {
        System.out.println("Som genérico de animal");
    }
}

class Gato extends Animal {
    @Override
    void fazerSom() {
        System.out.println("Miau");
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        Animal meuAnimal = new Gato();
        meuAnimal.fazerSom(); // Saída: Miau
    }
}
```

## 6️⃣ Interfaces e Abstração

### Abstração

A **abstração** oculta detalhes internos e expõe apenas o necessário.

```java
abstract class Veiculo {
    abstract void mover(); // Método abstrato (sem implementação)
}

class Carro extends Veiculo {
    @Override
    void mover() {
        System.out.println("O carro está em movimento");
    }
}
```

### Interfaces

Uma **interface** define um contrato que as classes devem seguir.

```java
interface Animal {
    void fazerSom();
}

class Gato implements Animal {
    public void fazerSom() {
        System.out.println("Miau");
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        Animal meuGato = new Gato();
        meuGato.fazerSom(); // Saída: Miau
    }
}
```

## 🎯 Exercícios Práticos

**1 - Aplicando Encapsulamento**

- Crie uma classe `Funcionario` com os atributos privados `nome` e `salario`.
- Implemente métodos `set` e `get` para acessar e modificar os atributos.
- No `main()`, instancie um funcionário, defina seus valores e exiba-os na tela.

**2 - Demonstrando Herança**

- Crie uma classe `Veiculo` com um método `mover()`.
- Crie as classes `Carro` e `Moto` que herdam de `Veiculo` e sobrescrevem `mover()`.
- No `main()`, instancie `Carro` e `Moto`, chamando `mover()` para cada um.

**3 - Implementando uma Interface**

- Crie uma interface `Pagamento` com um método `processarPagamento()`.
- Implemente `Pagamento` nas classes `CartaoCredito` e `Boleto`, cada uma com sua lógica.
- No `main()`, instancie um `CartaoCredito` e um `Boleto`, chamando `processarPagamento()`.

## 📚 Leitura Recomendada

- [Documentação Oficial da Oracle - POO](https://docs.oracle.com/javase/tutorial/java/concepts/index.html)
- [Livro: Effective Java - Joshua Bloch](https://amzn.to/3R3zZjs)

---

Com esse conhecimento, você estará pronto para desenvolver aplicações orientadas a objetos de maneira eficiente! 🚀
