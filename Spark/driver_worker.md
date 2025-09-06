In un cluster abbiamo due componenti principali driver e worker

## Driver

Il driver si occupa di richiedere al cluster manager le risorse quando viene lanciata un applicazione spark e si occupa di assegnarle ai worker. inoltre richiede l'instanziazione di nuovi worker quando questi cadono.

Inoltre genera un piano di esecuzione denominato DAG.

## Worker

Il worker o nodo è l'entità che si occupa di eseguire le operazioni, è controllato da un driver. è composto da più esecutori uno per cpu