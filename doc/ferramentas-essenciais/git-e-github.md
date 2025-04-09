# 🧰 Uso de Git e GitHub para Versionamento de Código

## Introdução

Controlar versões de código é uma prática essencial no desenvolvimento de software moderno. Seja em projetos pessoais ou em grandes equipes, ferramentas como **Git** e **GitHub** são fundamentais para manter o histórico de alterações, colaborar com outros desenvolvedores e evitar perda de código.

Neste guia, você aprenderá o que são Git e GitHub, como utilizá-los na prática e quais os principais comandos e fluxos de trabalho utilizados no dia a dia do desenvolvedor Java.

---

## O que é Git?

**Git** é um sistema de controle de versão distribuído. Isso significa que cada desenvolvedor possui uma cópia completa do repositório, com todo o histórico de alterações, permitindo trabalhar de forma offline e integrar mudanças posteriormente.

### ✅ Benefícios do Git:

- Histórico completo de alterações
- Possibilidade de trabalhar em diferentes versões (branches)
- Integração com ferramentas de CI/CD
- Rápido, leve e gratuito

---

## O que é GitHub?

**GitHub** é uma plataforma baseada em Git que permite hospedar repositórios online. Com ele, é possível colaborar com outros desenvolvedores, abrir e revisar pull requests, controlar permissões e integrar com diversas ferramentas de automação.

> 💡 **Dica:** GitHub não é o Git. O Git é a ferramenta, o GitHub é o serviço online que a utiliza.

---

## 🔧 Principais Comandos do Git

| Comando               | Descrição                                              |
| --------------------- | ------------------------------------------------------ |
| `git init`            | Inicia um repositório Git local                        |
| `git clone <url>`     | Clona um repositório remoto                            |
| `git status`          | Mostra o status das alterações                         |
| `git add <arquivo>`   | Adiciona arquivos à área de preparação                 |
| `git commit -m ""`    | Salva um snapshot do código                            |
| `git push`            | Envia os commits para o repositório remoto             |
| `git pull`            | Atualiza o repositório local com as alterações remotas |
| `git branch`          | Lista ou cria ramificações (branches)                  |
| `git checkout <ramo>` | Alterna entre branches                                 |
| `git merge <ramo>`    | Mescla alterações de uma branch com a branch atual     |

---

## 🌀 Fluxo de Trabalho Básico com Git e GitHub

1. **Clonar um projeto existente:**

   ```bash
   git clone https://github.com/usuario/projeto.git
   ```
