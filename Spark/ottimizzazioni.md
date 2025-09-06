# Ottimizzazioni tipiche in Apache Spark

## 1. Gestione delle trasformazioni

Evitare azioni inutili: ogni azione (collect, count, ecc.) scatena un job → meglio ridurle.

Usare trasformazioni strette (map, filter) al posto di quelle larghe quando possibile (groupByKey, reduceByKey).

Preferire mapPartitions a map quando si vuole ridurre l’overhead su molte partizioni.

## 2. Partizionamento e parallelismo

Repartition/Coalesce: adattare il numero di partizioni ai dati e al cluster.

Partitioning by key: per operazioni come join o groupByKey, usare un partitioner coerente (es. HashPartitioner).

Evita partizioni troppo piccole (overhead di scheduling) o troppo grandi (rischio di out-of-memory).

## 3. Caching e persistenza

Cache/ persist: memorizzare dataset ricalcolati più volte in RAM (.cache(), .persist()).

Uso strategico: evitare di cacheare dataset usati una sola volta.

## 4. Shuffle e join

Ridurre gli shuffle: sono costosi in termini di rete e disco.

Usare reduceByKey invece di groupByKey: riduce i dati prima dello shuffle.

Broadcast join (broadcast()) quando una tabella è piccola rispetto all’altra → evita shuffle pesanti.

## 5. Formati e storage

Usare formati colonnari come Parquet o ORC → compressione + predicate pushdown.

Evita CSV/JSON per grossi volumi → parsing pesante.

Partitioning e bucketing a livello di file system per migliorare i join e i filter.

## 6. Configurazioni del cluster

Esecutori ben dimensionati: memoria, core e numero di executor devono bilanciare parallelismo e overhead.

Dynamic allocation (se disponibile): per adattare automaticamente le risorse ai carichi.

Evita di saturare la memoria dell’executor → meglio più executor piccoli che pochi enormi.

## 7. Catalyst Optimizer & Tungsten

Spark SQL sfrutta Catalyst per ottimizzare i piani di query (pushdown, eliminazione di proiezioni inutili, ecc.).

Tungsten engine ottimizza la gestione della memoria e il code generation a runtime.