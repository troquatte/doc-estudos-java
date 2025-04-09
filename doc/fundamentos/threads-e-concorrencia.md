# 🚀 Threads e Concorrência em Java (Básico)

## 1️⃣ Introdução a Threads e Concorrência

Em Java, **Threads** permitem a execução de tarefas simultâneas dentro de um programa, tornando-o mais eficiente e responsivo. O suporte à concorrência em Java é baseado no pacote `java.util.concurrent`, que fornece ferramentas avançadas para manipulação de threads.

### Benefícios do Uso de Threads

- ✅ Melhor aproveitamento de CPUs multi-core.
- ✅ Maior responsividade para aplicações de interface gráfica.
- ✅ Execução simultânea de tarefas independentes.

## 2️⃣ Criando e Executando Threads

Existem duas maneiras principais de criar uma thread em Java:

### 1. Extendendo a Classe `Thread`

```java
class MinhaThread extends Thread {
    public void run() {
        System.out.println("Thread executando: " + Thread.currentThread().getName());
    }
}

public class TesteThread {
    public static void main(String[] args) {
        MinhaThread t1 = new MinhaThread();
        t1.start();
    }
}
```

### 2. Implementando a Interface `Runnable`

```java
class MinhaRunnable implements Runnable {
    public void run() {
        System.out.println("Thread executando: " + Thread.currentThread().getName());
    }
}

public class TesteRunnable {
    public static void main(String[] args) {
        Thread t1 = new Thread(new MinhaRunnable());
        t1.start();
    }
}
```

## 3️⃣ Sincronização de Threads

Quando múltiplas threads acessam um mesmo recurso compartilhado, pode ocorrer **condição de corrida**. Para evitar isso, usamos a palavra-chave `synchronized`.

### Exemplo de Sincronização

```java
class Contador {
    private int count = 0;

    public synchronized void incrementar() {
        count++;
    }

    public int getCount() {
        return count;
    }
}

public class TesteSincronizacao {
    public static void main(String[] args) {
        Contador contador = new Contador();

        Runnable tarefa = () -> {
            for (int i = 0; i < 1000; i++) {
                contador.incrementar();
            }
        };

        Thread t1 = new Thread(tarefa);
        Thread t2 = new Thread(tarefa);

        t1.start();
        t2.start();

        try {
            t1.join();
            t2.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println("Valor final: " + contador.getCount());
    }
}
```

## 4️⃣ Executors: Gerenciando Múltiplas Threads

O Java oferece a API `Executors` para facilitar o gerenciamento de threads.

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class TesteExecutor {
    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(3);

        Runnable tarefa = () -> System.out.println("Executando thread: " + Thread.currentThread().getName());

        for (int i = 0; i < 5; i++) {
            executor.execute(tarefa);
        }

        executor.shutdown();
    }
}
```

## 5️⃣ Quando e Onde Usar Threads e Concorrência?

### Quando Usar?

- **Aplicações com tarefas longas**: Se uma tarefa consome muito tempo (como processamento de imagens ou cálculos pesados), o uso de threads pode manter a aplicação responsiva.
- **Operações de I/O**: Leituras e gravações de arquivos, chamadas de API e consultas a bancos de dados podem ser executadas em threads separadas para não travar a aplicação principal.
- **Sistemas que precisam lidar com múltiplos usuários**: Aplicações como servidores web ou jogos multiplayer precisam lidar com múltiplas requisições simultâneas.

### Onde Evitar?

- **Tarefas curtas e simples**: Criar threads pode ter um custo de processamento maior do que a execução sequencial.
- **Código que já usa bibliotecas concorrentes**: Evite criar threads manualmente se você já está utilizando bibliotecas como `ForkJoinPool` ou `Executors`.
- **Ambientes de execução com restrições de recursos**: Em sistemas embarcados ou aplicações móveis, muitas threads podem causar consumo excessivo de CPU e bateria.

## 🎯 Exercícios Práticos

**1 - Criando Threads**

- Crie uma classe que estenda `Thread` e execute uma tarefa simples.
- Modifique a implementação para usar `Runnable`.

**2 - Sincronização**

- Implemente uma classe que compartilhe um recurso entre threads e use `synchronized` para evitar problemas de concorrência.

**3 - Executors**

- Utilize `Executors` para criar um pool de threads e execute múltiplas tarefas concorrentes.

## 📚 Leitura Recomendada

- [Documentação Oficial da Oracle - Threads](https://docs.oracle.com/javase/tutorial/essential/concurrency/)

---

Com esse conhecimento, você estará pronto para trabalhar com **threads** e **concorrência** de forma segura e eficiente! 🚀
