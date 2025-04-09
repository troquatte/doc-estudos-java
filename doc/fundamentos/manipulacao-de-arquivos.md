# 📂 Manipulação de Arquivos em Java

## 1️⃣ Introdução

A manipulação de arquivos é uma funcionalidade essencial em Java, permitindo a leitura, escrita e manipulação de dados persistentes em arquivos no sistema.

### Principais Classes para Manipulação de Arquivos

- **`File`**: Representa um arquivo ou diretório no sistema.
- **`FileReader` e `BufferedReader`**: Usados para leitura de arquivos de texto.
- **`FileWriter` e `BufferedWriter`**: Usados para escrita em arquivos de texto.
- **`Files`**: Oferece métodos utilitários para manipulação de arquivos e diretórios.
- **`RandomAccessFile`**: Permite a leitura e escrita em arquivos de forma aleatória.

## 2️⃣ Criando e Verificando Arquivos

Para criar e verificar a existência de um arquivo, utilizamos a classe `File`.

```java
import java.io.File;
import java.io.IOException;

public class CriarArquivo {
    public static void main(String[] args) {
        try {
            File arquivo = new File("meuarquivo.txt");
            if (arquivo.createNewFile()) {
                System.out.println("Arquivo criado com sucesso!");
            } else {
                System.out.println("O arquivo já existe.");
            }
        } catch (IOException e) {
            System.out.println("Erro ao criar o arquivo: " + e.getMessage());
        }
    }
}
```

## 3️⃣ Escrevendo em Arquivos

Podemos utilizar `FileWriter` e `BufferedWriter` para escrever em arquivos de forma eficiente.

```java
import java.io.FileWriter;
import java.io.BufferedWriter;
import java.io.IOException;

public class EscreverArquivo {
    public static void main(String[] args) {
        try (BufferedWriter escritor = new BufferedWriter(new FileWriter("meuarquivo.txt", true))) {
            escritor.write("Hello, Java!\n");
            escritor.newLine();
            System.out.println("Texto escrito com sucesso!");
        } catch (IOException e) {
            System.out.println("Erro ao escrever no arquivo: " + e.getMessage());
        }
    }
}
```

## 4️⃣ Lendo Arquivos

A leitura pode ser feita utilizando `BufferedReader` para maior eficiência.

```java
import java.io.FileReader;
import java.io.BufferedReader;
import java.io.IOException;

public class LerArquivo {
    public static void main(String[] args) {
        try (BufferedReader leitor = new BufferedReader(new FileReader("meuarquivo.txt"))) {
            String linha;
            while ((linha = leitor.readLine()) != null) {
                System.out.println(linha);
            }
        } catch (IOException e) {
            System.out.println("Erro ao ler o arquivo: " + e.getMessage());
        }
    }
}
```

## 5️⃣ Excluindo Arquivos

Podemos excluir um arquivo utilizando o método `delete()` da classe `File`.

```java
import java.io.File;

public class ExcluirArquivo {
    public static void main(String[] args) {
        File arquivo = new File("meuarquivo.txt");
        if (arquivo.delete()) {
            System.out.println("Arquivo deletado com sucesso!");
        } else {
            System.out.println("Erro ao deletar o arquivo.");
        }
    }
}
```

## 🎯 Exercícios Práticos

**1 - Criando e Escrevendo em um Arquivo**

- Crie um programa que solicite ao usuário uma frase e grave-a em um arquivo.

**2 - Lendo um Arquivo**

- Modifique o programa anterior para exibir o conteúdo do arquivo após a gravação.

**3 - Manipulação Avançada**

- Crie um programa que copie o conteúdo de um arquivo para outro.

## 📚 Leitura Recomendada

- [Documentação Oficial da Oracle - File I/O](https://docs.oracle.com/javase/tutorial/essential/io/index.html)
- [Livro: Java: The Complete Reference - Herbert Schildt](https://amzn.to/3R3zZjs)

---

Com esse conhecimento, você estará pronto para trabalhar com arquivos em Java de forma eficiente! 🚀
