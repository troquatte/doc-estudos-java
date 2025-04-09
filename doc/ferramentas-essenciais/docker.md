# 🐳 Fundamentos do Docker

## Introdução

Docker é uma plataforma que permite criar, empacotar e executar aplicações em contêiners. Ele resolve problemas de compatibilidade entre ambientes e facilita a distribuição de software com todas as suas dependências.

Com Docker, você pode garantir que seu aplicativo funcione da mesma forma em desenvolvimento, teste e produção.

---

## Conceitos Principais

### 📦 Imagem (Image)

Uma imagem é um pacote somente leitura com tudo o que a aplicação precisa para rodar: código, bibliotecas, dependências e configurações. Imagens são usadas como base para criar contêineres.

### 🧱 Contêiner (Container)

Contêiner é uma instância em execução de uma imagem. Ele é isolado do sistema hospedeiro, mas pode interagir com ele.

### 🏗️ Dockerfile

Arquivo de texto com instruções para criar uma imagem personalizada. Exemplo:

```Dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm", "start"]
```

### 📚 Docker Hub

Repositório público (ou privado) de imagens Docker. Similar ao GitHub, mas para imagens.

---

## Principais Comandos Docker

| Comando                        | Descrição                                 |
| ------------------------------ | ----------------------------------------- |
| `docker build -t nome .`       | Cria uma imagem a partir do Dockerfile    |
| `docker run nome`              | Executa um contêiner da imagem            |
| `docker run -p 3000:3000 nome` | Executa contêiner com mapeamento de porta |
| `docker ps`                    | Lista contêineres em execução             |
| `docker ps -a`                 | Lista todos os contêineres                |
| `docker stop id`               | Encerra um contêiner                      |
| `docker rm id`                 | Remove um contêiner parado                |
| `docker rmi imagem`            | Remove uma imagem                         |

---

## 🧪 Exercícios Práticos

**1. Criando sua primeira imagem**

- Crie um arquivo `Dockerfile` com instruções básicas (ex: uma aplicação Node ou Python)
- Rode `docker build -t minha-app .`
- Depois execute com `docker run minha-app`

**2. Testando isolamento**

- Execute dois contêineres em paralelo e veja como eles não compartilham arquivos entre si

**3. Mapeando portas**

- Rode uma aplicação web e acesse-a via navegador usando `localhost:porta`

**4. Listando e limpando recursos**

- Use os comandos `ps`, `stop`, `rm`, `rmi` para gerenciar seus contêineres e imagens

---

## 🛠️ Dicas e Boas Práticas

- Sempre defina um `.dockerignore` para evitar copiar arquivos desnecessários.
- Use `multi-stage builds` para reduzir o tamanho das imagens.
- Prefira imagens oficiais e com tags estáveis.
- Não rode aplicações como root dentro do contêiner.

---

## 📚 Leitura Recomendada

- [Documentação Oficial do Docker](https://docs.docker.com/)
- [Dockerfile Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- [Docker Hub](https://hub.docker.com/)

---

Com esses conceitos e práticas, você já pode começar a utilizar Docker no seu fluxo de desenvolvimento e dar os primeiros passos rumo à conteinerização de aplicações! 🚀
