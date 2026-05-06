# Apache Spark + Delta Lake + Iceberg

## Contextualizacao

Este projeto explora a integracao do **Apache Spark** com dois dos principais formatos de tabela open-source para arquiteturas **Data Lakehouse**: o **Delta Lake** e o **Apache Iceberg**.

## Cenario

Utilizamos um modelo de **e-commerce** com tres entidades:

| Tabela | Descricao |
|---|---|
| clientes | Cadastro de clientes |
| produtos | Catalogo de produtos |
| pedidos | Transacoes de compra |

## Objetivo

Demonstrar operacoes DML (INSERT, UPDATE, DELETE) com suporte a ACID Transactions e Time Travel usando PySpark nos dois formatos de tabela.

## Tecnologias

| Tecnologia | Versao |
|---|---|
| Python | 3.11 |
| Apache Spark | 3.5.1 |
| Delta Lake | 3.2.0 |
| Apache Iceberg | 1.5.0 |
| Poetry | 2.x |
| JupyterLab | 4.x |
