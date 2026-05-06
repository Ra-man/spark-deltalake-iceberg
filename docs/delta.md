# Delta Lake

## O que e?

Delta Lake e uma camada de armazenamento open-source que adiciona confiabilidade ao Data Lake. Desenvolvido pela Databricks, traz **transacoes ACID** para o Spark.

## Principais recursos

| Recurso | Descricao |
|---|---|
| ACID Transactions | Garante consistencia dos dados |
| Time Travel | Consulta versoes anteriores da tabela |
| Schema Evolution | Alteracao de schema sem recriar tabela |
| Upsert (MERGE) | Inserir ou atualizar em uma unica operacao |

## Criando uma tabela Delta

```sql
CREATE TABLE pedidos (
  id_pedido INT,
  status STRING,
  valor_total DOUBLE
) USING DELTA LOCATION "/tmp/delta/pedidos"
```

## INSERT

```sql
INSERT INTO pedidos VALUES (1, "pendente", 3500.00)
```

## UPDATE

```sql
UPDATE pedidos SET status = "entregue" WHERE id_pedido = 1
```

## DELETE

```sql
DELETE FROM pedidos WHERE id_pedido = 1
```

## Time Travel

```python
from delta.tables import DeltaTable

dt = DeltaTable.forPath(spark, "/tmp/delta/pedidos")
dt.history().show()

spark.read.format("delta").option("versionAsOf", 0).load("/tmp/delta/pedidos").show()
```
