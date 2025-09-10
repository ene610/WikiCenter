
# Tipi di cluster

In Databricks ci sono diversi tipi di cluster, che variano in base a come vengono creati, gestiti e utilizzati. Ecco i principali:

## All-Purpose Cluster

Un primo tipo è l’all-purpose cluster, che viene usato soprattutto in fase di sviluppo, analisi esplorativa o attività di data science. Si tratta di un cluster multiutente, che rimane attivo finché non viene spento manualmente o tramite l’opzione di auto-terminate. È la scelta tipica quando si lavora in modo interattivo con i notebook e si ha bisogno di eseguire query ad hoc o provare diverse trasformazioni sui dati.

- Multiutente (più notebook e job possono usarlo in parallelo).

- Adatto a query ad-hoc e sperimentazione.

- Rimane acceso finché non viene terminato manualmente (o tramite auto-terminate).

## Job Cluster

Questi cluster non vengono creati manualmente ma nascono automaticamente all’avvio di un job pianificato, per poi terminarsi da soli quando il job è completato. Questo comportamento assicura che ogni job venga eseguito in un ambiente isolato e dedicato, evitando conflitti tra processi e garantendo un miglior controllo dei costi
Caratteristiche:

- Creato automaticamente all’avvio di un job e terminato al termine.

- Isolamento: ogni job ha il suo cluster dedicato.

- Più efficiente in termini di costi se i job non sono continui.

## High Concurrency Cluster

pensati per scenari in cui molti utenti o applicazioni devono eseguire query contemporaneamente, come quando si integrano strumenti di business intelligence tipo Tableau o Power BI. Questi cluster sono ottimizzati per gestire un elevato numero di richieste parallele e offrono livelli di sicurezza più elevati, in quanto ogni utente lavora in sessioni isolate.

- Ottimizzati per gestire più query contemporaneamente.

- Supportano l’uso di Databricks SQL.

- Maggiore sicurezza e isolamento delle sessioni utente.

## Serverless Compute (dove disponibile)

In questo caso l’utente non deve occuparsi della creazione o gestione dei cluster, perché l’infrastruttura viene gestita interamente dalla piattaforma. Il provisioning delle risorse è immediato, lo scaling è automatico e si paga solo per il tempo di effettivo utilizzo. È particolarmente comodo per query SQL interattive o per analisi che richiedono elasticità senza la complessità di configurare manualmente un cluster.

- Gestito interamente da Databricks.

- Auto-scaling veloce e provisioning istantaneo.

- Si paga solo per l’uso effettivo.

- Tipicamente usato con Databricks SQL o notebook interattivi in ambienti cloud.