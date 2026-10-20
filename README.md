# Classificazione-Wikipedia
Il progetto carica, classifica e confronta diversi modelli sul dataset Wikipedia

L'architettura del progetto si è articolata attraverso cinque punti nodali:

1- Data Ingestion e Feature Engineering: Il dataset, composto da testi etichettati, è stato affrontato fondendo sistematicamente la sezione introduttiva (summary) e il corpo principale (documents) di ogni articolo. Questa operazione ha massimizzato la densità semantica del testo in ingresso, fornendo al modello sia la sintesi concettuale che la profondità del contesto.

2- Pipeline di Preprocessing Distribuita: Il testo grezzo è stato sottoposto a una catena di montaggio sequenziale composta da pulizia tramite espressioni regolari (RegexTokenizer), rimozione di stop-words standard e personalizzate, vettorizzazione (HashingTF impostato a 10.000 feature) e pesatura statistica tramite IDF (Inverse Document Frequency).

3-Modellazione Avanzata e Deep Learning: È stato condotto uno studio comparativo architettando tre differenti approcci algoritmici. Al modello base (Logistic Regression) sviluppato con due approcci, è stata affiancata una rete neurale spark MLP (Multilayer Perceptron Classifier) a quattro livelli [10.000, 64, 32, 15], ottimizzata con mini-batch da 128 record su ambiente containerizzato/Colab.

3- Analisi delle Performance: Il modello selezionato ha raggiunto un'accuratezza macro complessiva del 93%. L'analisi critica condotta tramite classification report ha evidenziato le eccellenze del modello su categorie specifiche (esempio politics al 99%) e ha permesso di mappare i margini dell'MLP, legati alla naturale sovrapposizione semantica tra domini affini (per esempio il binomio medicine/research e finance/economics).

5- Industrializzazione: Il modello è stato congelato e serializzato su disco tramite il costrutto PipelineModel di Spark, garantendo la portabilità del modello e un caricamento istantaneo per future fasi di inferenza senza la necessità di riaddestramento.
