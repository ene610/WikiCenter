# Differenza tra Job, Stage e Task in Spark

## Job

Creato ogni volta che viene invocata un’azione (collect, count, save, ecc.).

Rappresenta l’intero lavoro necessario per ottenere il risultato richiesto.

## Stage

Ogni job viene suddiviso in più stages, in base alle dipendenze tra le trasformazioni.

Uno stage è una sequenza di operazioni che possono essere eseguite senza shuffle.

Il confine tra due stage è segnato da uno shuffle (es. groupBy, join).

## Task

È l’unità minima di esecuzione.

Ogni stage viene diviso in più task, uno per ciascuna partizione dei dati.

I task vengono eseguiti in parallelo sugli executor distribuiti nei worker.