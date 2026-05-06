# Apache Iceberg

## O que e?

Apache Iceberg e um formato de tabela open-source de alto desempenho para analise em larga escala. Criado pela Netflix, resolve problemas de escalabilidade que o formato Hive nao conseguia lidar.

## Diferenciais em relacao ao Delta Lake

| Caracteristica | Delta Lake | Apache Iceberg |
|---|---|---|
| Criador | Databricks | Netflix / Apache |
| Multi-engine | Parcial | Total (Spark, Flink, Trino...) |
| Schema Evolution | Sim | Sim (mais avancado) |
| Partition Evolution | Nao | Sim |
| Row-level deletes | Sim | Sim |

## Configurando o Spark com Iceberg

```python
spark = SparkSession.builder \
    .config("spark.jars.packages", "org.apache.iceberg:iceberg-spark-runtime-3.5_2.12:1.5.0") \
    .config("spark.sql.extensions", "org.apache.iceberg.spark.extensions.IcebergSparkSessionExtensions") \
    .config("spark.sql.catalog.local", "org.apache.iceberg.spark.SparkCatalog") \
    .config("spark.sql.catalog.local.type", "hadoop") \
    .config("spark.sql.catalog.local.warehouse", "/tmp/iceberg/warehouse") \
    .getOrCreate()
```

## INSERT

```sql
INSERT INTO local.ecommerce.pedidos VALUES (1, 1, 1, 1, 3500.00, "pendente", DATE "2024-01-10")
```

## UPDATE

```sql
UPDATE local.ecommerce.pedidos SET status = "entregue" WHERE id_pedido = 1
```

## DELETE

```sql
DELETE FROM local.ecommerce.pedidos WHERE id_pedido = 2
```

## Time Travel com Snapshots

```sql
SELECT * FROM local.ecommerce.pedidos.snapshots;
```

```python
spark.read.option("snapshot-id", 123456789).table("local.ecommerce.pedidos").show()
```
