# 🏎️ Banco de Dados - Grande Prêmio do Brasil (GP Brasil)

![Licença](https://img.shields.io/badge/license-MIT-green)
![Tecnologia](https://img.shields.io/badge/SQL-MySQL%20%7C%20PostgreSQL%20%7C%20SQL%20Server-blue)
![Status](https://img.shields.io/badge/status-Conclu%C3%ADdo-brightgreen)

## 📌 Visão Geral
Este projeto consiste na modelagem e implementação de um banco de dados relacional para o gerenciamento de corridas, pilotos, equipes e participantes do **Grande Prêmio do Brasil**. 

A solução abrange a criação da estrutura do banco (DDL), a inserção de dados fictícios para testes (DML), a alteração de tabelas para novas regras de negócio e a execução de consultas analíticas (DQL).

---

## 🛠️ Tecnologias Utilizadas
- **Linguagem:** SQL (DDL, DML, DQL)
- **SGBD Compatível:** MySQL, PostgreSQL, Microsoft SQL Server ou SQLite
- **Ferramentas de Execução:** DBeaver, MySQL Workbench ou VS Code (com extensão SQL)

---

## 🗂️ Estrutura do Banco de Dados
O banco de dados é composto por 5 tabelas interligadas por chaves estrangeiras (`FOREIGN KEY`):

- **`Pais`**: Armazena os países de origem das equipes, pilotos e corridas.
- **`Corrida`**: Registra as etapas do GP com informações de voltas e tamanho da pista.
- **`Equipe`**: Cadastro das equipes participantes.
- **`Piloto`**: Registra os pilotos, associação de equipes, país de origem e salário.
- **`Participantes`**: Tabela associativa (N:M) que relaciona pilotos às corridas e registra a posição de largada.

---

## 🚀 Como Executar o Projeto

### Pré-requisitos
Ter um Gerenciador de Banco de Dados (SGBD) instalado (ex.: **MySQL Workbench** ou **DBeaver**).

### Passo a Passo
1. Clone este repositório para a sua máquina:
   ```bash
   git clone https://github.com/seu-usuario/nome-do-seu-repositorio.git
   ```
2. Abra seu ambiente de banco de dados SQL.
3. Importe ou copie o código do arquivo de script (ex.: `script_gp_brasil.sql`).
4. Execute o script em ordem:
   - **Criação do Banco e Tabelas** (`CREATE DATABASE` e `CREATE TABLE`)
   - **Inserção dos Dados** (`INSERT INTO`)
   - **Atualização da Tabela Piloto** (`ALTER TABLE` e `UPDATE`)
   - **Consultas e Relatórios** (`SELECT`)

---

## 🔍 Exemplos de Consultas Realizadas
O projeto inclui queries para análise de dados, como:
- Filtro de pilotos com faixas salariais específicas (`BETWEEN`).
- Cálculo de média salarial dos pilotos agrupados por país de origem (`AVG` e `ROUND`).
- Busca de países por padrão de texto (`LIKE`).

---

## 📷 Demonstração
![Execução do Script SQL](./preview.png)

---

## 📄 Licença
Este projeto está sob a licença MIT. Consulte o arquivo [LICENSE](LICENSE) para mais detalhes.
