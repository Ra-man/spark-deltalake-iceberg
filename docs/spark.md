# Apache Spark (PySpark)

## O que e?

Apache Spark e um motor de processamento de dados distribuido, open-source, projetado para ser rapido e de uso geral. Ele processa grandes volumes de dados em memoria, sendo ate 100x mais rapido que o Hadoop MapReduce.

## Por que PySpark?

PySpark e a API Python do Spark, permitindo escrever pipelines de dados com Python, a linguagem mais usada em Engenharia de Dados.

## Criando uma SparkSession

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .appName("MeuApp") \
    .getOrCreate()
```

## Exemplo de leitura e transformacao

```python
df = spark.read.csv("dados.csv", header=True, inferSchema=True)
df.filter(df["status"] == "ativo").show()
```

## Integracao com formatos modernos

O Spark serve como motor de processamento tanto para **Delta Lake** quanto para **Apache Iceberg**, sendo o componente central desta arquitetura.

## Arquitetura

- **Driver**: coordena a execucao
- **Executors**: processam os dados em paralelo
- **SparkContext**: ponto de entrada da aplicacao
- **DataFrame API**: abstração principal para manipulacao de dados
