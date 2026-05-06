# Apache Spark com Delta Lake e Apache Iceberg

> Trabalho de Pesquisa — Arquitetura de Dados | SATC

## Participantes

- Nathan Frassetto
- Rafael Pagnan
- Ryan Candeu

## Sobre o Projeto

Este projeto demonstra na pratica o uso do **Apache Spark (PySpark)** integrado com dois formatos de tabela open-source para Data Lakehouse:

- **Delta Lake** — formato da Databricks com suporte a ACID transactions e Time Travel
- **Apache Iceberg** — formato da Netflix com suporte avancado a schema evolution e Time Travel

O cenario utilizado simula uma base de dados de **e-commerce** com tabelas de clientes, produtos e pedidos.

## Estrutura do Projeto

```
spark-deltalake-iceberg/
├── notebooks/
│   ├── delta_lake.ipynb        # Demonstracao completa com Delta Lake
│   └── iceberg.ipynb           # Demonstracao completa com Apache Iceberg
├── docs/                       # Documentacao MkDocs
│   ├── index.md
│   ├── spark.md
│   ├── delta.md
│   └── iceberg.md
├── mkdocs.yml
├── pyproject.toml
└── README.md
```

## Pre-requisitos

### Java 17

**Linux/Ubuntu (WSL):**
```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
echo "export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64" >> ~/.bashrc
echo "export PATH=$JAVA_HOME/bin:$PATH" >> ~/.bashrc
source ~/.bashrc
java -version
```

### Python 3.11

```bash
sudo apt install software-properties-common -y
sudo add-apt-repository ppa:deadsnakes/ppa -y
sudo apt update
sudo apt install python3.11 python3.11-venv python3-pip -y
python3.11 --version
```

### Poetry

```bash
curl -sSL https://install.python-poetry.org | python3.11 -
echo "export PATH=$HOME/.local/bin:$PATH" >> ~/.bashrc
source ~/.bashrc
poetry --version
```

## Como Rodar

### 1. Clone o repositorio

```bash
git clone https://github.com/Ra-man/spark-deltalake-iceberg.git
cd spark-deltalake-iceberg
```

### 2. Instale as dependencias

```bash
poetry install
```

### 3. Ative o ambiente virtual

```bash
eval $(poetry env activate)
```

### 4. Inicie o Jupyter Lab

```bash
jupyter lab --no-browser
```

Acesse no navegador: http://localhost:8888

### 5. Execute os notebooks

Abra e execute celula por celula:
- delta_lake.ipynb
- iceberg.ipynb

## Dependencias

| Pacote | Versao | Descricao |
|---|---|---|
| pyspark | 3.5.1 | Motor de processamento distribuido |
| delta-spark | 3.2.0 | Integracao Delta Lake com Spark |
| jupyterlab | 4.x | Interface de notebooks |
| mkdocs | 1.5.x | Gerador de documentacao |
| mkdocs-material | 9.x | Tema Material para MkDocs |

## Modelo de Dados

```
CLIENTES (id_cliente, nome, email, cidade)
    |
    +--< PEDIDOS (id_pedido, id_cliente, id_produto, quantidade, valor_total, status, data_pedido)
                    |
PRODUTOS (id_produto, nome, categoria, preco) >--+
```

## Documentacao

Acesse a documentacao completa em: https://Ra-man.github.io/spark-deltalake-iceberg/

## Referencias

- https://spark.apache.org/docs/latest/
- https://docs.delta.io/
- https://iceberg.apache.org/docs/latest/
- https://github.com/jlsilva01/spark-delta
- https://github.com/jlsilva01/spark-iceberg
