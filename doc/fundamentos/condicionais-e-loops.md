# 📌 Estruturas Condicionais e Loops em Java

As **estruturas condicionais e loops** são fundamentais para o controle de fluxo em Java. Elas permitem que o programa tome decisões e repita ações com base em condições específicas.

---

## 🔹 1. Estruturas Condicionais

### 🔸 `if`, `else if`, `else`

O comando `if` avalia uma expressão booleana e executa um bloco de código se a condição for verdadeira.

```java
int idade = 18;

if (idade >= 18) {
    System.out.println("Você é maior de idade.");
} else {
    System.out.println("Você é menor de idade.");
}
```

Se houver mais de uma condição, usamos `else if`.

```java
int nota = 85;

if (nota >= 90) {
    System.out.println("Aprovado com excelência!");
} else if (nota >= 70) {
    System.out.println("Aprovado.");
} else {
    System.out.println("Reprovado.");
}
```

---

### 🔸 `switch`

O `switch` é útil quando há várias condições para um mesmo valor.

```java
int diaSemana = 3;

switch (diaSemana) {
    case 1:
        System.out.println("Domingo");
        break;
    case 2:
        System.out.println("Segunda-feira");
        break;
    case 3:
        System.out.println("Terça-feira");
        break;
    default:
        System.out.println("Dia inválido");
}
```

O `break` impede que os blocos seguintes sejam executados.

---

## 🔹 2. Estruturas de Repetição (Loops)

### 🔸 `while`

O `while` executa um bloco de código **enquanto** a condição for verdadeira.

```java
int contador = 1;
while (contador <= 5) {
    System.out.println("Contagem: " + contador);
    contador++;
}
```

> ⚠️ **Cuidado!** Certifique-se de que a condição será falsa em algum momento para evitar loops infinitos.

---

### 🔸 `do-while`

O `do-while` executa o bloco **ao menos uma vez** antes de verificar a condição.

```java
int num = 1;
do {
    System.out.println("Número: " + num);
    num++;
} while (num <= 3);
```

> ⚠️ Mesmo que a condição seja falsa logo na primeira verificação, o código dentro de `do` será executado ao menos uma vez.

---

### 🔸 `for`

O `for` é ideal quando sabemos o número exato de repetições.

```java
for (int i = 1; i <= 5; i++) {
    System.out.println("Iteração: " + i);
}
```

> ⚠️ A estrutura do `for` inclui **inicialização, condição e incremento**.

---

### 🔸 `foreach` (Enhanced for)

Usado para percorrer arrays e coleções de maneira simplificada.

```java
int[] numeros = {10, 20, 30, 40};
for (int num : numeros) {
    System.out.println(num);
}
```

---

## 🔹 3. Controle de Fluxo dentro de Loops

### 🔸 `break`

O `break` interrompe o loop imediatamente.

```java
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        break;
    }
    System.out.println(i);
}
```

### 🔸 `continue`

O `continue` pula para a próxima iteração do loop.

```java
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        continue;
    }
    System.out.println(i);
}
```

---

## 🎯 Exercícios Práticos

**1️⃣ Estruturas Condicionais**

- Crie um programa que verifica se um número é positivo, negativo ou zero.
- Escreva um `switch` que identifica se um mês tem 28, 30 ou 31 dias.

**2️⃣ Loops**

- Imprima os números de 1 a 10 usando um `while`.
- Some os números de 1 a 100 com um `for`.
- Percorra um array de nomes com um `foreach` e imprima cada nome.

---

Este guia cobre as **estruturas condicionais e loops** em Java! 🚀
