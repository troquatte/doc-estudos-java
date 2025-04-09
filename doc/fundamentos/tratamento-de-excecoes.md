# ⚠️ Tratamento de Exceções em Java

## 1️⃣ Introdução ao Tratamento de Exceções

Em Java, uma **exceção** é um evento inesperado que ocorre durante a execução de um programa e pode interromper seu fluxo normal. O tratamento de exceções permite lidar com esses erros de maneira controlada.

### Tipos de Exceções

As exceções em Java podem ser classificadas em:

- **Checked Exceptions (Exceções Verificadas)**: Ocorrem em tempo de compilação e devem ser tratadas obrigatoriamente. Exemplo: `IOException`.
- **Unchecked Exceptions (Exceções Não Verificadas)**: Ocorrem em tempo de execução e derivam de `RuntimeException`. Exemplo: `NullPointerException`.
- **Errors**: Problemas graves que geralmente não podem ser tratados. Exemplo: `OutOfMemoryError`.

## 2️⃣ Blocos try-catch-finally

O tratamento de exceções é feito com o uso dos blocos `try`, `catch` e `finally`.

### Exemplo básico de `try-catch`

```java
public class ExcecaoExemplo {
    public static void main(String[] args) {
        try {
            int resultado = 10 / 0; // Isso causará uma exceção
        } catch (ArithmeticException e) {
            System.out.println("Erro: Divisão por zero!");
        }
    }
}
```

### Uso do bloco `finally`

O bloco `finally` sempre será executado, independentemente de uma exceção ocorrer ou não.

```java
public class ExemploFinally {
    public static void main(String[] args) {
        try {
            int[] numeros = {1, 2, 3};
            System.out.println(numeros[5]); // Causa exceção
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Erro: Índice fora dos limites do array!");
        } finally {
            System.out.println("Bloco finally executado.");
        }
    }
}
```

## 3️⃣ Lançando Exceções com `throw`

Podemos lançar exceções manualmente com a palavra-chave `throw`.

```java
public class ExemploThrow {
    static void verificarIdade(int idade) {
        if (idade < 18) {
            throw new IllegalArgumentException("Idade insuficiente!");
        }
        System.out.println("Acesso permitido.");
    }

    public static void main(String[] args) {
        verificarIdade(15); // Isso gerará uma exceção
    }
}
```

## 4️⃣ Propagando Exceções com `throws`

Quando um método pode gerar uma exceção, podemos indicar isso usando `throws` na assinatura do método.

```java
import java.io.*;

public class ExemploThrows {
    static void lerArquivo() throws IOException {
        FileReader arquivo = new FileReader("arquivo.txt");
    }

    public static void main(String[] args) {
        try {
            lerArquivo();
        } catch (IOException e) {
            System.out.println("Erro ao ler o arquivo: " + e.getMessage());
        }
    }
}
```

## 5️⃣ Criando Exceções Personalizadas

Podemos criar nossas próprias classes de exceção herdando de `Exception` ou `RuntimeException`.

```java
class MinhaExcecao extends Exception {
    public MinhaExcecao(String mensagem) {
        super(mensagem);
    }
}

public class TesteMinhaExcecao {
    static void validar(int numero) throws MinhaExcecao {
        if (numero < 0) {
            throw new MinhaExcecao("Número negativo não permitido!");
        }
        System.out.println("Número válido!");
    }

    public static void main(String[] args) {
        try {
            validar(-5);
        } catch (MinhaExcecao e) {
            System.out.println("Erro: " + e.getMessage());
        }
    }
}
```

## 🎯 Exercícios Práticos

**1 - Tratamento de exceções básico**

- Crie um programa que solicite ao usuário dois números e realize uma divisão.
- Utilize `try-catch` para tratar uma possível divisão por zero.

**2 - Propagação de Exceções**

- Crie um método que tente abrir um arquivo inexistente.
- Use `throws` para propagar a exceção e trate-a no `main()`.

**3 - Exceção Personalizada**

- Crie uma exceção `SaldoInsuficienteException`.
- Use essa exceção para verificar saques em um sistema bancário.

## 📚 Leitura Recomendada

- [Documentação Oficial da Oracle - Exceções](https://docs.oracle.com/javase/tutorial/essential/exceptions/index.html)
- [Livro: Effective Java - Joshua Bloch](https://amzn.to/3R3zZjs)

---

Com esse conhecimento, você estará pronto para lidar com erros de maneira eficiente! 🚀
