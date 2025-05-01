# Projeto de Integração Contínua com Go e GitHub Actions

Este repositório demonstra a configuração de um pipeline de Integração Contínua (CI) utilizando [GitHub Actions](https://docs.github.com/actions) com um projeto escrito em [Go](https://golang.org/).

## 📦 Sobre o Projeto

O objetivo é automatizar o processo de build, testes e análise estática sempre que houver mudanças no código-fonte.

## 🚀 Funcionalidades da Pipeline

- ✅ Build automático do projeto Go
- ✅ Execução de testes automatizados com `go test`
- ✅ Análise de código com `golint` (opcional)
- ✅ Execução da pipeline em pull requests e push na branch `main`
