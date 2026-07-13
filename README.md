# Desafio DevSecOps — Gerenciador de Tarefas

## Sobre o Projeto

Este projeto faz parte do desafio prático de DevSecOps da ADA Tech.

O objetivo foi implementar uma pipeline de segurança automatizada para verificar o código antes do deploy, identificando possíveis problemas de segurança e impedindo que uma aplicação vulnerável fosse publicada.


## Como funciona a Pipeline

A pipeline é executada automaticamente a cada alteração enviada para a branch main.

Ela possui as seguintes etapas:

## 1. Checkout do código
A primeira etapa realiza o download do código do repositório para que os testes possam ser executados.

## 2. Build
É feita uma validação inicial dos arquivos do projeto para confirmar que a aplicação está pronta para passar pelas etapas de segurança.

## 3. Secrets Scanning - Gitleaks
O Gitleaks verifica se existem informações sensíveis expostas no código ou no histórico de commits, como:
- Senhas;
- Tokens;
- Chaves de API.

Caso seja encontrado algum segredo, a pipeline é interrompida para evitar que informações sensíveis sejam publicadas.

## 4. SAST - Semgrep
O Semgrep realiza uma análise do código-fonte procurando padrões inseguros.

Durante a análise inicial foi encontrada uma utilização insegura da função eval(), que foi removida para melhorar a segurança da aplicação.

## 5. SCA - Grype
O Grype verifica as dependências utilizadas pelo projeto em busca de vulnerabilidades conhecidas.

Foram atualizadas dependências que apresentavam vulnerabilidades para versões mais seguras.

## 6. Deploy
Após todas as verificações de segurança serem aprovadas, a aplicação é publicada automaticamente utilizando GitHub Pages.

## Resultado final

Após as correções:

✅ Pipeline executando com sucesso no GitHub Actions
✅ Gitleaks validando exposição de segredos
✅ Semgrep analisando segurança do código
✅ Grype verificando vulnerabilidades das dependências
✅ Aplicação publicada no GitHub

## URL de Produção

A aplicação está disponível em:

https://daniellarf.github.io/projeto-devsecop-desafio/

## Ferramentas utilizadas
GitHub Actions
Gitleaks
Semgrep
Grype
GitHub Pages
Docker
