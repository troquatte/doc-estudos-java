# 📚 Collections Framework em Java

O **Collections Framework** do Java fornece um conjunto de interfaces e classes para manipular estruturas de dados como listas, conjuntos, mapas e filas. Ele melhora a eficiência e organização do código ao lidar com grandes volumes de dados.

---

## 🔹 1. List

A interface `List` representa uma coleção ordenada de elementos, permitindo duplicatas.

### 📌 Implementações principais:

- **ArrayList** - Baseado em array dinâmico, rápido para leitura, mas lento para inserções/remoções no meio da lista.

### ✨ Exemplo ArrayList

O ArrayList é uma implementação baseada em array dinâmico, que permite acesso rápido aos elementos por índice (O(1)), mas é lento para inserções e remoções no meio da lista (O(n)), pois exige deslocamento dos elementos. Ideal quando a operação principal é leitura.

```java
import java.util.*;

public class ListExample {
    public static void main(String[] args) {
        List<String> nomes = new ArrayList<>();
        // CREATE
        nomes.add("Ana");
        nomes.add("Carlos");
        nomes.add("Bruno");

        // READ
        System.out.println(nomes);

        // UPDATE
        nomes.set(1, "Marcos");

        // DELETE
        nomes.remove("Bruno");

        System.out.println(nomes);
    }
}
```

---

## 🔹 2. Set

A interface `Set` representa uma coleção de elementos únicos, ou seja, não permite elementos duplicados.

### 📌 Implementações principais:

- **HashSet** - Baseado em `HashMap`, não garante ordem dos elementos.
- **LinkedHashSet** - Mantém a ordem de inserção dos elementos.
- **TreeSet** - Ordenado automaticamente (baseado em `TreeMap`).

### ✨ Exemplo HashSet

O HashSet armazena elementos de forma não ordenada e não permite duplicatas. Ele usa um HashMap internamente, tornando as operações add, remove e contains muito rápidas (O(1) no melhor caso). Porém, a ordem dos elementos pode mudar ao longo da execução.

```java
import java.util.*;

public class SetExample {
    public static void main(String[] args) {
        Set<String> nomes = new HashSet<>();
        // CREATE
        nomes.add("Ana");
        nomes.add("Carlos");
        nomes.add("Bruno");

        // READ
        System.out.println(nomes);

        // DELETE
        nomes.remove("Bruno");

        System.out.println(nomes);
    }
}
```

### ✨ Exemplo LinkedHashSet

O LinkedHashSet funciona como um HashSet, mas mantém a ordem de inserção dos elementos. Ideal quando você precisa de desempenho similar ao HashSet, mas com a garantia de que os elementos serão iterados na ordem em que foram adicionados.

```java
import java.util.*;

public class LinkedHashSetExample {
    public static void main(String[] args) {
        // CREATE
        LinkedHashSet<String> nomes = new LinkedHashSet<>();
        nomes.add("Ana");
        nomes.add("Carlos");
        nomes.add("Bruno");

        System.out.println("Set inicial: " + nomes); // [Ana, Carlos, Bruno]

        // READ
        System.out.println("Contém Carlos? " + nomes.contains("Carlos")); // true

        // UPDATE (Não há atualização direta em Set, então removemos e adicionamos)
        nomes.remove("Carlos");
        nomes.add("João");
        System.out.println("Após update: " + nomes); // [Ana, Bruno, João]

    }
}

```

### ✨ Exemplo TreeSet

O TreeSet armazena elementos de forma ordenada (crescente por padrão), pois é baseado em um TreeMap. Todas as operações são O(log n) devido ao uso de uma árvore balanceada (Red-Black Tree). Ideal quando você precisa manter os elementos sempre ordenados.

```java
import java.util.*;

public class SetExample {
    public static void main(String[] args) {
        Set<String> nomes = new HashSet<>();
        // CREATE
        nomes.add("Ana");
        nomes.add("Carlos");
        nomes.add("Bruno");

        // READ
        System.out.println(nomes);

        // DELETE
        nomes.remove("Bruno");

        System.out.println(nomes);
    }
}
```

---

## 🔹 3. Map

A interface `Map` representa uma coleção de pares **chave-valor**, onde as **chaves são únicas**.

### 📌 Implementações principais:

- **HashMap** - Baseado em tabela de hash, não mantém a ordem das chaves.
- **LinkedHashMap** - Mantém a ordem de inserção.
- **TreeMap** - Ordena as chaves automaticamente.

### ✨ Exemplo HashMap

O HashMap armazena pares chave-valor sem garantir nenhuma ordem das chaves. É altamente eficiente para operações get() e put() (O(1) no melhor caso), mas sua ordem interna pode mudar. Ele permite uma chave null e múltiplos valores null.

```java
import java.util.*;

public class MapExample {
    public static void main(String[] args) {
        Map<Integer, String> usuarios = new HashMap<>();
        // CREATE
        usuarios.put(1, "Ana");
        usuarios.put(2, "Carlos");
        usuarios.put(3, "Bruno");

        // READ
        System.out.println(usuarios);

        // UPDATE
        usuarios.put(2, "Marcos");

        // DELETE
        usuarios.remove(3);

        System.out.println(usuarios);
    }
}
```

### ✨ Exemplo LinkedHashMap

O LinkedHashMap funciona como um HashMap, mas mantém a ordem de inserção das chaves. Útil quando a ordem das chaves precisa ser preservada ao longo do tempo, como em caches e dicionários ordenados.

```java
import java.util.*;

public class LinkedHashMapExample {
    public static void main(String[] args) {
        // CREATE
        LinkedHashMap<Integer, String> usuarios = new LinkedHashMap<>();
        usuarios.put(1, "Ana");
        usuarios.put(2, "Carlos");
        usuarios.put(3, "Bruno");

        System.out.println("Mapa inicial: " + usuarios); // {1=Ana, 2=Carlos, 3=Bruno}

        // READ
        System.out.println("Usuário com ID 2: " + usuarios.get(2)); // Carlos

        // UPDATE
        usuarios.put(2, "João"); // Substituindo Carlos por João
        System.out.println("Após update: " + usuarios); // {1=Ana, 2=João, 3=Bruno}

        // DELETE
        usuarios.remove(3);
        System.out.println("Após remoção: " + usuarios); // {1=Ana, 2=João}
    }
}

```

### ✨ Exemplo TreeMap

O TreeMap armazena os pares chave-valor de forma ordenada pelas chaves. Ele usa uma árvore balanceada (Red-Black Tree), garantindo que todas as operações (get, put, remove) sejam O(log n). Não permite null como chave.

```java
import java.util.*;

public class TreeMapExample {
    public static void main(String[] args) {
        // CREATE
        TreeMap<Integer, String> usuarios = new TreeMap<>();
        usuarios.put(3, "Ana");
        usuarios.put(1, "Carlos");
        usuarios.put(2, "Bruno");

        System.out.println("Mapa inicial: " + usuarios); // {1=Carlos, 2=Bruno, 3=Ana} (Ordenado por chave)

        // READ
        System.out.println("Usuário com menor ID: " + usuarios.firstEntry()); // 1=Carlos
        System.out.println("Usuário com maior ID: " + usuarios.lastEntry()); // 3=Ana

        // UPDATE
        usuarios.put(2, "João"); // Substituindo Bruno por João
        System.out.println("Após update: " + usuarios); // {1=Carlos, 2=João, 3=Ana}

        // DELETE
        usuarios.remove(3);
        System.out.println("Após remoção: " + usuarios); // {1=Carlos, 2=João}
    }
}


```

---

## 🔹 4. Queue

A interface `Queue` representa uma estrutura de **fila**, seguindo a ordem **FIFO** (First-In, First-Out).

### 📌 Implementações principais:

- **LinkedList** - Implementa `Queue`, permitindo operações de fila.
- **PriorityQueue** - Mantém os elementos em ordem de prioridade.

### ✨ Exemplo LinkedList

O LinkedList implementa tanto List quanto Queue, funcionando como lista encadeada. Ele é mais eficiente do que ArrayList para inserções e remoções no meio da lista (O(1) para operações na cabeça e cauda da lista), mas mais lento para acessos diretos aos elementos (O(n)).

```java
import java.util.*;

public class QueueExample {
    public static void main(String[] args) {
        Queue<String> fila = new LinkedList<>();
        // CREATE
        fila.add("Ana");
        fila.add("Carlos");
        fila.add("Bruno");

        // READ
        System.out.println(fila);

        // UPDATE (não é comum, mas pode remover e adicionar de novo)
        fila.remove("Carlos");
        fila.add("Marcos");

        // DELETE
        fila.poll();

        System.out.println(fila);
    }
}
```

### ✨ Exemplo PriorityQueue

O PriorityQueue é uma fila de prioridade onde os elementos são ordenados automaticamente com base em sua ordem natural (menor primeiro) ou por um Comparator personalizado. O elemento de maior prioridade sempre fica no topo, garantindo remoção eficiente (O(log n)). Ideal para algoritmos como Dijkstra e processamento por ordem de prioridade.

```java
import java.util.*;

public class PriorityQueueExample {
    public static void main(String[] args) {
        // CREATE
        PriorityQueue<Integer> filaPrioridade = new PriorityQueue<>();
        filaPrioridade.add(30);
        filaPrioridade.add(10);
        filaPrioridade.add(20);

        System.out.println("Fila inicial: " + filaPrioridade); // A ordem de exibição pode variar

        // READ
        System.out.println("Elemento de maior prioridade (menor número): " + filaPrioridade.peek()); // 10

        // UPDATE (Remover e adicionar um novo valor)
        filaPrioridade.poll(); // Remove o menor elemento (10)
        filaPrioridade.add(25);
        System.out.println("Após update: " + filaPrioridade); // Pode ser [20, 30, 25] (mantém a ordem mínima)

        // DELETE
        filaPrioridade.poll(); // Remove o próximo menor elemento (20)
        System.out.println("Após remoção: " + filaPrioridade); // Pode ser [25, 30]

        // ORDENAR (A `PriorityQueue` mantém a ordem mínima automaticamente)
        System.out.println("Fila ordenada automaticamente: " + filaPrioridade); // [25, 30]
    }
}
```

---

## 🎯 Exercícios Práticos

**1️⃣ Trabalhando com List**

- Crie uma `ArrayList` de inteiros e adicione números de 1 a 5.
- Remova o segundo elemento e exiba a lista.

**2️⃣ Manipulando Set**

- Crie um `HashSet` e adicione elementos repetidos.
- Exiba o resultado e perceba que os duplicados não são armazenados.

**3️⃣ Usando Map**

- Crie um `HashMap` para armazenar nomes e idades de pessoas.
- Exiba os dados e remova um elemento pelo ID.

**4️⃣ Simulando uma Fila**

- Use uma `LinkedList` para representar uma fila de atendimento.
- Adicione três nomes e remova-os na ordem de chegada.

---

## 📚 Leitura Recomendada

- [Livro: Effective Java - Joshua Bloch](https://amzn.to/3R3zZjs)

---

Este guia cobre os principais conceitos do **Collections Framework** e suas implementações em Java! 🚀
