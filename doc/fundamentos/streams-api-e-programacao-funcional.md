# 🚀 Streams API e Programação Funcional em Java

## Introdução

Java oferece poderosas ferramentas para manipulação de coleções de dados de forma declarativa e eficiente. A **Streams API** permite o processamento de dados em pipelines, enquanto a **Programação Funcional** traz conceitos como imutabilidade e funções de alta ordem. Juntos, esses conceitos ajudam a escrever um código mais limpo, conciso e eficiente.

---

## 🔥 Streams API

A **Streams API**, introduzida no Java 8, permite o processamento de coleções de forma funcional e paralela, eliminando a necessidade de loops explícitos.

### 🎯 Características das Streams

- **Imutáveis**: A stream não modifica a coleção original.
- **Lazy Evaluation**: Operações são executadas apenas quando necessário.
- **Pipeline de operações**: Podem ser encadeadas para transformar dados.
- **Paralelismo**: Suporte a processamento paralelo para melhorar desempenho.

### 📌 Operações em Streams

As operações em **Streams API** são divididas em:

#### 1️⃣ **Intermediárias** (transformam a stream, retornando uma nova stream)

| Método     | Descrição                                  |
| ---------- | ------------------------------------------ |
| `filter`   | Filtra elementos com base em uma condição. |
| `map`      | Transforma cada elemento da stream.        |
| `sorted`   | Ordena os elementos.                       |
| `distinct` | Remove elementos duplicados.               |
| `limit`    | Limita o número de elementos.              |
| `skip`     | Ignora os primeiros elementos.             |

##### 📝 Exemplos

```java
import java.util.*;
import java.util.function.Function;
import java.util.stream.Collectors;

public class StreamsAPIExamples {
    public static void main(String[] args) {
        // Lista de exemplo
        List<String> nomes = Arrays.asList("Ana", "Pedro", "Mariana", "João", "Ana", "Carlos", "Amanda");

        // 1️⃣ FILTER - Filtrando nomes que começam com "A"
        List<String> filtrados = nomes.stream()
            .filter(nome -> nome.startsWith("A"))
            .collect(Collectors.toList());
        System.out.println("Nomes que começam com A: " + filtrados); // [Ana, Ana, Amanda]

        // 2️⃣ MAP - Convertendo todos os nomes para maiúsculas
        List<String> maiusculos = nomes.stream()
            .map(String::toUpperCase)
            .collect(Collectors.toList());
        System.out.println("Nomes em maiúsculas: " + maiusculos);

        // 3️⃣ SORTED - Ordenando alfabeticamente
        List<String> ordenados = nomes.stream()
            .sorted()
            .collect(Collectors.toList());
        System.out.println("Nomes ordenados: " + ordenados);

        // 4️⃣ DISTINCT - Removendo duplicatas
        List<String> distintos = nomes.stream()
            .distinct()
            .collect(Collectors.toList());
        System.out.println("Nomes distintos: " + distintos);

        // 5️⃣ LIMIT - Pegando apenas os 3 primeiros nomes
        List<String> limitados = nomes.stream()
            .limit(3)
            .collect(Collectors.toList());
        System.out.println("Apenas os 3 primeiros: " + limitados);

        // 6️⃣ SKIP - Pulando os 2 primeiros elementos
        List<String> ignorados = nomes.stream()
            .skip(2)
            .collect(Collectors.toList());
        System.out.println("Pulando os 2 primeiros: " + ignorados);

        // 7️⃣ COLLECT - Transformando a Stream em um Set (sem duplicatas)
        Set<String> setNomes = nomes.stream()
            .collect(Collectors.toSet());
        System.out.println("Set de nomes: " + setNomes);

        // 8️⃣ FOREACH - Imprimindo cada nome (sem coletar)
        System.out.println("Nomes com forEach:");
        nomes.stream().forEach(System.out::println);

        // 9️⃣ REDUCE - Concatenando todos os nomes
        String concatenado = nomes.stream()
            .reduce((a, b) -> a + ", " + b)
            .orElse("Lista vazia");
        System.out.println("Nomes concatenados: " + concatenado);

        // 🔟 COUNT - Contando quantos nomes começam com "A"
        long countA = nomes.stream()
            .filter(nome -> nome.startsWith("A"))
            .count();
        System.out.println("Quantidade de nomes que começam com A: " + countA);

        // 1️⃣1️⃣ MIN/MAX - Menor e maior nome (por tamanho)
        Optional<String> menorNome = nomes.stream()
            .min(Comparator.comparingInt(String::length));
        Optional<String> maiorNome = nomes.stream()
            .max(Comparator.comparingInt(String::length));

        System.out.println("Menor nome: " + menorNome.orElse("Nenhum"));
        System.out.println("Maior nome: " + maiorNome.orElse("Nenhum"));

        // 1️⃣2️⃣ ANYMATCH - Verifica se há pelo menos um nome que começa com "M"
        boolean existeM = nomes.stream()
            .anyMatch(nome -> nome.startsWith("M"));
        System.out.println("Existe algum nome que começa com M? " + existeM);
    }
}

```

##### Resumo das Operações Aplicadas

| Operação   | O que faz?                                          | Exemplo                                        |
| ---------- | --------------------------------------------------- | ---------------------------------------------- |
| `filter`   | Filtra elementos com base em uma condição.          | `filter(nome -> nome.startsWith("A"))`         |
| `map`      | Transforma os elementos da stream.                  | `map(String::toUpperCase)`                     |
| `sorted`   | Ordena os elementos.                                | `sorted()`                                     |
| `distinct` | Remove elementos duplicados.                        | `distinct()`                                   |
| `limit`    | Retorna apenas os primeiros elementos.              | `limit(3)`                                     |
| `skip`     | Ignora os primeiros elementos.                      | `skip(2)`                                      |
| `collect`  | Converte a stream em outra estrutura de dados.      | `collect(Collectors.toList())`                 |
| `forEach`  | Executa uma ação para cada elemento.                | `forEach(System.out::println)`                 |
| `reduce`   | Combina os elementos em um único valor.             | `reduce((a, b) -> a + ", " + b)`               |
| `count`    | Conta os elementos.                                 | `count()`                                      |
| `min/max`  | Retorna o menor/maior elemento.                     | `min(Comparator.comparingInt(String::length))` |
| `anyMatch` | Verifica se ao menos um elemento atende à condição. | `anyMatch(nome -> nome.startsWith("M"))`       |

#### 2️⃣ **Finais** (produzem um resultado e encerram a stream)

| Método     | Descrição                                     |
| ---------- | --------------------------------------------- |
| `collect`  | Coleta os elementos em uma lista, set, etc.   |
| `forEach`  | Executa uma ação para cada elemento.          |
| `reduce`   | Combina os elementos em um único valor.       |
| `count`    | Conta os elementos.                           |
| `min/max`  | Retorna o menor/maior elemento.               |
| `anyMatch` | Verifica se algum elemento atende à condição. |

##### 📝 Exemplos

```java
// Soma todos os números da lista
int soma = numeros.stream()
    .reduce(0, Integer::sum);
System.out.println(soma); // Saída: 35

// Conta quantos números existem na lista
long quantidade = numeros.stream().count();
System.out.println(quantidade); // Saída: 8

// Obtém o menor e o maior número
Optional<Integer> menor = numeros.stream().min(Integer::compareTo);
Optional<Integer> maior = numeros.stream().max(Integer::compareTo);
System.out.println(menor.get()); // Saída: 1
System.out.println(maior.get()); // Saída: 9

// Verifica se há algum número maior que 7
boolean existeMaiorQueSete = numeros.stream().anyMatch(n -> n > 7);
System.out.println(existeMaiorQueSete); // Saída: true

// Itera sobre a lista e imprime cada número
numeros.forEach(System.out::println);
```

---

## 🎯 Programação Funcional em Java

A **Programação Funcional** permite escrever código mais conciso e menos propenso a erros, utilizando funções como primeira classe e evitando estados mutáveis.

### 🔍 Princípios da Programação Funcional

1️⃣ **Imutabilidade**: Evita modificações de estado, tornando o código mais previsível.  
2️⃣ **Funções de alta ordem**: Permite passar funções como argumento e retorná-las como resultado.  
3️⃣ **Expressões Lambda**: Facilita a criação de funções anônimas.  
4️⃣ **Referências de Métodos**: Reuso de métodos existentes para melhorar legibilidade.

### 📌 Expressões Lambda

As **expressões lambda** eliminam a necessidade de classes anônimas ao definir funções.

#### 📝 Exemplo

```java
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);

List<Integer> dobrados = numeros.stream()
    .map(n -> n * 2)
    .collect(Collectors.toList());

System.out.println(dobrados); // Saída: [2, 4, 6, 8, 10]
```

### 🔥 Referências de Métodos

Permitem utilizar métodos existentes sem criar novas funções anônimas.

#### 📝 Exemplo

```java
List<String> nomes = Arrays.asList("Maria", "João", "Pedro");
nomes.forEach(System.out::println); // Imprime cada nome
```

### 🔄 Funções de Alta Ordem

São funções que aceitam outras funções como argumento ou retornam uma função.

#### 📝 Exemplo

```java
Function<Integer, Integer> dobrar = x -> x * 2;
System.out.println(dobrar.apply(5)); // Saída: 10
```

---

Com este conhecimento, você poderá escrever código mais eficiente, reutilizável e escalável! 🚀

---

## 🎯 Exercícios Práticos

1️⃣ **Filtrando e transformando dados:**

- Dada uma lista de números, retorne apenas os números pares e multiplicados por 3.

2️⃣ **Usando `reduce()`:**

- Some todos os elementos de uma lista utilizando `reduce()`.

3️⃣ **Criando sua própria função de alta ordem:**

- Escreva uma função que recebe outra função como argumento e a aplica a uma lista de números.

---

## 📚 Leitura Recomendada

- [Documentação Oficial do Java - Streams API](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/stream/package-summary.html)
- [Livro: Effective Java - Joshua Bloch](https://amzn.to/3R3zZjs)

---

Com este conhecimento, você poderá escrever código mais eficiente, reutilizável e escalável! 🚀
