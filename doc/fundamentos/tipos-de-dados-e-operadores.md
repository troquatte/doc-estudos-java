# 📖 Tipos de Dados e Operadores em Java

## Introdução

Em Java, os tipos de dados e operadores são fundamentais para a manipulação de variáveis e a execução de operações matemáticas e lógicas. Compreender esses conceitos é essencial para escrever código eficiente e confiável.

## Tipos de Dados em Java

Java é uma linguagem fortemente tipada, o que significa que toda variável deve ser declarada com um tipo específico. Os tipos de dados são classificados em **primitivos** e **referência**.

### Tipos Primitivos

Os tipos primitivos são os tipos de dados básicos em Java e representam valores simples.

| Tipo      | Tamanho | Valor Padrão | Faixa de Valores      |
| --------- | ------- | ------------ | --------------------- |
| `byte`    | 8 bits  | `0`          | -128 a 127            |
| `short`   | 16 bits | `0`          | -32.768 a 32.767      |
| `int`     | 32 bits | `0`          | -2³¹ a 2³¹-1          |
| `long`    | 64 bits | `0L`         | -2⁶³ a 2⁶³-1          |
| `float`   | 32 bits | `0.0f`       | ±3.4e−038 a ±3.4e+038 |
| `double`  | 64 bits | `0.0d`       | ±1.7e−308 a ±1.7e+308 |
| `char`    | 16 bits | `'\u0000'`   | Caracteres Unicode    |
| `boolean` | 1 bit   | `false`      | `true` ou `false`     |

### Tipos de Referência

Os tipos de referência armazenam endereços de memória de objetos e arrays. Exemplos incluem:

- **Strings** (`String`): Representam cadeias de caracteres.
- **Arrays** (`int[]`, `double[]`, etc.): Coleções de elementos do mesmo tipo.
- **Objetos** (instâncias de classes criadas pelo usuário).

## Operadores em Java

Os operadores são usados para manipular variáveis e realizar cálculos e comparações.

### 1️⃣ Operadores Aritméticos

Usados para realizar operações matemáticas.

| Operador | Descrição                 | Exemplo |
| -------- | ------------------------- | ------- |
| `+`      | Adição                    | `a + b` |
| `-`      | Subtração                 | `a - b` |
| `*`      | Multiplicação             | `a * b` |
| `/`      | Divisão                   | `a / b` |
| `%`      | Módulo (resto da divisão) | `a % b` |

### 2️⃣ Operadores de Atribuição

Atribuem valores às variáveis.

| Operador | Exemplo  | Equivalente a  |
| -------- | -------- | -------------- |
| `=`      | `a = b`  | `a` recebe `b` |
| `+=`     | `a += b` | `a = a + b`    |
| `-=`     | `a -= b` | `a = a - b`    |
| `*=`     | `a *= b` | `a = a * b`    |
| `/=`     | `a /= b` | `a = a / b`    |
| `%=`     | `a %= b` | `a = a % b`    |

## 3️⃣ Tipos de Dados Primitivos em Java

Java possui oito tipos de dados primitivos, que são usados para armazenar valores simples na memória. Abaixo está uma tabela detalhada com explicações mais claras sobre a faixa de valores de cada tipo.

| Tipo      | Tamanho | Valor Padrão | Faixa de Valores                                                        |
| --------- | ------- | ------------ | ----------------------------------------------------------------------- |
| `byte`    | 8 bits  | `0`          | -128 a 127 (2^7 a -2^7-1)                                               |
| `short`   | 16 bits | `0`          | -32.768 a 32.767 (2^15 a -2^15-1)                                       |
| `int`     | 32 bits | `0`          | -2.147.483.648 a 2.147.483.647 (2^31 a -2^31-1)                         |
| `long`    | 64 bits | `0L`         | -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807 (2^63 a -2^63-1) |
| `float`   | 32 bits | `0.0f`       | Aproximadamente ±1.4E-45 a ±3.4E+38                                     |
| `double`  | 64 bits | `0.0d`       | Aproximadamente ±4.9E-324 a ±1.7E+308                                   |
| `char`    | 16 bits | `'\u0000'`   | Qualquer caractere Unicode (0 a 65.535)                                 |
| `boolean` | 1 bit   | `false`      | Apenas `true` ou `false`                                                |

Os tipos numéricos (`byte`, `short`, `int`, `long`, `float`, `double`) podem armazenar valores positivos e negativos, exceto `char`, que representa um caractere Unicode. O tipo `boolean` é utilizado para representar valores lógicos.

### 4️⃣ Operadores Lógicos

Usados para avaliar expressões booleanas.

| Operador | Descrição        | Exemplo            |
| -------- | ---------------- | ------------------ |
| `&&`     | E lógico (AND)   | `a > 0 && b > 0`   |
| `\|\|`   | OU lógico (OR)   | `a > 0 \|\| b > 0` |
| `!`      | NÃO lógico (NOT) | `!a`               |

### 5️⃣ Operadores de Incremento e Decremento

Usados para aumentar ou diminuir valores em 1 unidade.

| Operador | Descrição  | Exemplo        |
| -------- | ---------- | -------------- |
| `++`     | Incremento | `a++` ou `++a` |
| `--`     | Decremento | `a--` ou `--a` |

### 6️⃣ Operadores Bitwise

Manipulam bits diretamente.

| Operador | Descrição               | Exemplo  |
| -------- | ----------------------- | -------- |
| `&`      | AND bit a bit           | `a & b`  |
| `\|`     | OR bit a bit            | `a \| b` |
| `^`      | XOR bit a bit           | `a ^ b`  |
| `~`      | Complemento bit a bit   | `~a`     |
| `<<`     | Deslocamento à esquerda | `a << 2` |
| `>>`     | Deslocamento à direita  | `a >> 2` |

## 🎯 Exercícios Práticos

**1 - Criando um programa básico**

- Declare uma variável para cada tipo de dado primitivo e atribua valores.
- Exiba os valores usando `System.out.println()`.

**2 - Operações matemáticas**

- Solicite dois números do usuário.
- Realize e exiba todas as operações aritméticas (`+`, `-`, `*`, `/`, `%`).

**3 - Explorando operadores lógicos**

- Crie expressões condicionais (`if`) que testem `&&`, `||` e `!`.
- Exiba mensagens indicando se as expressões retornam `true` ou `false`.

**4 - Manipulando operadores de atribuição**

- Declare uma variável `int` e modifique seu valor utilizando `+=`, `-=`, `*=`, `/=`, `%=`.
- Exiba os resultados a cada operação.

**5 - Testando operadores bitwise**

- Escolha dois números inteiros e aplique `&`, `|`, `^`, `~`, `<<` e `>>`.
- Exiba os valores em binário antes e depois das operações.

## 📚 Leitura Recomendada

- [Documentação Oficial da Oracle - Tipos de Dados](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)
- [Documentação Oficial da Oracle - Operadores](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/operators.html)
- [Livro: Effective Java - Joshua Bloch](https://amzn.to/3R3zZjs)

---

Com este conhecimento, você estará pronto para avançar para estruturas de controle e manipulação de fluxo em Java! 🚀
