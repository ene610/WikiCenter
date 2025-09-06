# Shuffle

Una shuffle in Spark è il processo in cui i dati vengono ridistribuiti tra i nodi del cluster per soddisfare dipendenze tra operazioni.

Avviene quando un’operazione richiede di raggruppare o riordinare i dati per chiave (es. groupByKey, reduceByKey, join, distinct).

I dati vengono scritti su disco e spediti in rete tra executor → operazione costosa.

Segna il confine tra due stage in un job Spark.