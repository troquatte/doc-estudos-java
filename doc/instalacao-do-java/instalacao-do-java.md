# Instalação do Java e Configuração do Ambiente

Antes de começar a programar em Java, é necessário instalar o JDK (Java Development Kit) e configurar o ambiente de desenvolvimento. O JDK contém tudo o que você precisa para compilar e executar aplicações Java.

### 1️⃣ Escolhendo a versão do JDK

A versão recomendada para novos projetos é o **JDK 17** ou superior, pois é uma versão LTS (Long-Term Support), garantindo suporte e atualizações por um longo período.

📌 Baixe o JDK diretamente do site da Oracle: [https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)

### 2️⃣ Instalando o JDK no Windows

1. Baixe o instalador do JDK 17 ou superior.
2. Execute o instalador e siga as instruções.
3. Configure a variável de ambiente `JAVA_HOME`:
   - No Windows, vá até **Configurações do Sistema > Variáveis de Ambiente**.
   - Adicione uma nova variável `JAVA_HOME` apontando para a pasta de instalação do JDK.
   - Adicione `JAVA_HOME\bin` à variável `Path` para permitir a execução do Java via terminal.
4. Verifique a instalação executando no terminal:
   ```sh
   java -version
   javac -version
   ```

### 3️⃣ Instalando o JDK no macOS

No macOS, recomenda-se utilizar o Homebrew:

```sh
brew install openjdk@17
```

Após a instalação, adicione o JDK ao PATH:

```sh
echo 'export PATH="/usr/local/opt/openjdk@17/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

Verifique a instalação:

```sh
java -version
javac -version
```

### 4️⃣ Instalando o JDK no Linux

Em distribuições baseadas em Debian (Ubuntu, Mint), use:

```sh
sudo apt update
sudo apt install openjdk-17-jdk
```

Para distribuições baseadas em RedHat (Fedora, CentOS):

```sh
sudo dnf install java-17-openjdk-devel
```

Verifique a instalação com:

```sh
java -version
javac -version
```

### 5️⃣ Escolhendo uma IDE

Para programar em Java, é recomendável utilizar uma IDE (Ambiente de Desenvolvimento Integrado). As mais populares são:

- **IntelliJ IDEA** (Recomendada): [https://www.jetbrains.com/idea/](https://www.jetbrains.com/idea/)
- **Eclipse**: [https://www.eclipse.org/downloads/](https://www.eclipse.org/downloads/)
- **Visual Studio Code** (com extensão Java): [https://code.visualstudio.com/](https://code.visualstudio.com/)

### 6️⃣ Configuração inicial da IDE

Após instalar a IDE de sua escolha, siga estes passos:

- Configure o **JDK 17** nas preferências do projeto.
- Instale plugins necessários (caso esteja usando VS Code, adicione a extensão **Java Extension Pack**).
- Teste sua configuração criando um programa Java simples:
  ```java
  public class Main {
      public static void main(String[] args) {
          System.out.println("Olá, Java!");
      }
  }
  ```
- Compile e execute o programa para verificar se está tudo funcionando.

### Conclusão

Após a instalação e configuração do ambiente, você estará pronto para começar sua jornada no desenvolvimento Java! O próximo passo é aprender sobre a **sintaxe básica do Java**, explorando variáveis, tipos de dados e estruturas de controle. 🚀
