# 🚀 Pipeline de Integração Contínua (CI) com Go e GitHub Actions

[![CI Pipeline](https://img.shields.io/github/actions/workflow/status/JBorges-QA/CI-com-GitHubActions/deploy_ec2.yml)](https://github.com/JBorges-QA/CI-com-GitHubActions/actions/workflows/ci.yml)
[![Go Version](https://img.shields.io/badge/Go-1.21+-00ADD8?style=flat&logo=go)](https://go.dev/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Docker](https://img.shields.io/badge/Docker-Supported-2496ED?style=flat&logo=docker)](https://www.docker.com/)

> **Projeto Portfólio DevOps**  
> Implementação de uma esteira de Integração Contínua completa, automatizando build, teste, análise estática e notificações para uma aplicação web escrita em Go.

---

## 📌 Visão Geral do Projeto

Este repositório foi desenvolvido como um **caso prático de DevOps**, demonstrando a criação de uma pipeline de CI moderna utilizando **GitHub Actions**. O projeto vai além de um simples `go build`, incorporando práticas de qualidade de código, automação de testes e comunicação assíncrona de status via Webhooks.

A aplicação alvo é uma estrutura web em Go (possivelmente um CRUD ou API renderizada server-side, baseado na estrutura de `controllers`, `models` e `templates`).

**Principais Diferenciais Técnicos:**
- **Environments Strategy:** Uso de `environments` no GitHub Actions (`ci` e `prod`) para simular segregação de ambientes e controle de aprovação (visível no histórico de commits).
- **Automação com Makefile:** Abstração de comandos complexos para padronização da execução local e remota.
- **Containerização:** `docker-compose.yml` pronto para execução do ambiente de desenvolvimento/teste.

---

## 🛠️ Arquitetura da Pipeline CI/CD

O fluxo definido em `.github/workflows/ci.yml` executa as seguintes etapas de forma sequencial e condicional:

```mermaid
graph LR
    A[Push / PR para Main] --> B{Checkout & Setup Go};
    B --> C[Etapa de Build];
    C --> D[Execução de Testes Unitários];
    D --> E[Análise Estática - golint];
    E --> F[Notificação Discord];
    
    subgraph GitHub Actions
        C
        D
        E
    end
    
    subgraph Comunicação
        F -- Webhook --> G[Discord Channel]
    end
