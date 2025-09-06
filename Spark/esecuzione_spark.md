# Esecuzione di un job Spark

L’esecuzione di un job Spark segue un modello a fasi, che permette di ottimizzare il parallelismo e garantire l’efficienza del calcolo distribuito. Ecco una panoramica passo per passo:

## Sottomissione dell’applicazione
L’utente avvia un’applicazione Spark (ad esempio tramite SparkSession).
Questo rappresenta il punto di ingresso, dove vengono definite le trasformazioni e le azioni sui dati.

## Driver Program e creazione del piano di esecuzione

- Il Driver prende in carico il codice Spark dell’utente.
- Costruisce un DAG (Directed Acyclic Graph) che rappresenta la sequenza logica delle operazioni da eseguire.
- Il DAG viene ottimizzato e tradotto in un execution plan: una suddivisione in stages (fasi).

## Allocazione delle risorse da parte del Cluster Manager

- Il Driver comunica con il Cluster Manager (ad esempio YARN, Kubernetes, Databricks o Standalone).
- Il Cluster Manager assegna risorse computazionali e avvia i worker nodes, ciascuno con uno o più executor.

## Suddivisione in fasi (Stages)

- Il job viene diviso in stages in base alle dipendenze tra le trasformazioni.
- Ogni stage contiene più task, che sono le unità minime di lavoro e vengono eseguiti in parallelo sugli executor.

## Esecuzione dei task sugli Executor

- Gli executor ricevono i task dal Driver e li eseguono sui dati.
- Ogni executor ha memoria dedicata, che può essere usata per caching e per mantenere dataset intermedi in RAM.
- Questo riduce i ricalcoli e velocizza l’elaborazione.

## Shuffle e scambio di dati intermedi

- Tra una fase e l’altra, Spark può dover riorganizzare i dati (operazione detta shuffle).
- Lo shuffle distribuisce i dati tra i vari nodi in modo da rispettare le dipendenze del DAG (es. in operazioni come groupByKey, reduceByKey, join).

## Raccolta dei risultati

- Al termine, i risultati finali vengono:
    - inviati al Driver (se si tratta di un’azione come collect()), oppure
    - scritti su storage esterno (HDFS, Delta Lake, S3, ecc.).
- Una volta completata l’esecuzione, le risorse vengono rilasciate.