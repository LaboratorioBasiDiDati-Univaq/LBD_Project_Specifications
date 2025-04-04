# Corso di Laboratorio di Basi di Dati<br/>*Progetti A.A. 2024/2025* - Specifica 2

<section class="specifica">

## Progetto "Market"
> Versione 2

### Premessa

I progetti di fine corso si ispirano sempre ad esigenze
reali. La specifica informale del problema data nei paragrafi seguenti può
essere, come in ogni caso reale, incompleta e, in alcuni punti, ambigua o
contraddittoria. Lo studente dovrà quindi raffinare e disambiguare le
specifiche mediante l'interazione con il committente. In alcuni casi allo
studente sarà richiesto di valutare diverse possibili alternative, per poi
sceglierne una in maniera motivata. Le motivazioni di tutte le scelte
interpretative, progettuali e implementative andranno sempre chiaramente
documentate nel progetto e verranno discusse in sede di esame.

*Nota*: alcune delle funzionalità richieste dalla
specifica potrebbero non essere realizzabili con singole query, ma richiedere
l'uso di strumenti più avanzati messi a disposizione dal DBMS, come le
procedure. In ogni caso, tali procedure avrebbero una o più query come parte
principale. L'uso di queste caratteristiche avanzate aumenta notevolmente il
valore di un progetto. Tuttavia, nel caso si decida di non utilizzarle
nell'implementazione, è necessario comunque presentare lo pseudocodice
corrispondente, e realizzare *completamente* le relative query.

### Specifiche

<section class="descrizione">



Il database *Market* contiene le informazioni necessarie ad alimentare un sistema di acquisti online simile ai vari eCommerce che tutti ben conosciamo, ma *vincolato* e *guidato*, in quanto pensato per essere usato all'interno di un'organizzazione pubblica. 

Saranno previste due tipologie di utenza da modellare: *ordinanti* e *tecnici*. Nel sistema sarà previsto anche un *amministratore* col solo scopo di registrare altri utenti.

Il sistema funzionerà come segue. *Ricordate che non dovete realizzare questa procedura, ma solo comprenderla per modellare il database che ospiterà i dati necessari a supportarla!*

1. **Definizione della *richiesta di acquisto*.** L’ordinante dovrà selezionare una  *categoria* (ad esempio *PC Desktop*, *Notebook*, *Scrivania*,...) che identifichi la tipologia di prodotto da acquistare tra quelle note al sistema (*opzionalmente le categorie potranno avere una struttura ad albero, ad esempio Informatica > Computer > Notebook*). Ogni categoria di prodotto avrà associate una serie di *caratteristiche* specifiche (ad esempio quantità di RAM e tipo di CPU per un PC, ecc.), sempre definite nel sistema ed eventualmente aggiornabili. L'ordinante, per completare la propria *richiesta di acquisito*, dovrà quindi inserire i valori di tutte le caratteristiche desiderate relative alla categoria di prodotto selezionata (per ogni caratteristica sarà comunque sempre prevista l'opzione *indifferente*). Sarà presente anche uno spazio *note* per aggiungere ogni caratteristica peculiare non annoverata tra quelle standard. 

2. **Ricerca del prodotto da parte del personale tecnico.** Un membro del personale sarà associato alla *richiesta di acquisto* definita al punto 1, diventandone il *tecnico incaricato*. Il tecnico incaricato potrà visionare la categoria e le caratteristiche richieste dall'ordinante e cercherà (esternamente al sistema) un prodotto effettivo da ordinare (che chiameremo *prodotto candidato*), associandone poi la descrizione (che comprenderà almeno nome produttore, nome prodotto, codice prodotto, prezzo, URL di approfondimento e un campo note) alla richiesta.

3. **Revisione del prodotto candidato.** L'ordinante prenderà visione del prodotto candidato e potrà *approvarlo* o *respingerlo*, fornendo in questo caso una *motivazione*. In caso di richiesta respinta, il processo riprenderà dal passo 2, considerando che il tecnico incaricato sarà sempre lo stesso. La motivazione del rifiuto sarà mostrata assieme alle informazioni della richiesta, e il tecnico incaricato potrà modificare il prodotto candidato e inoltrarlo nuovamente all'ordinante.

4. **Esecuzione dell'ordine.** Nel caso in cui l'ordinante approvi la scelta del prodotto candidato al passo 3, il personale tecnico procederà all'acquisto (questa parte non sarà gestita dal nostro applicativo).

5. **Consegna e verifica del prodotto**. Quando il prodotto sarà consegnato (prima o poi!), l'ordinante dovrà *chiudere* la relativa richiesta di acquisto indicando se il prodotto ricevuto è stato *accettato*, *respinto perché non conforme* oppure *respinto perché non funzionante*.


</section>

Ci sono indubbiamente svariati vincoli che possono essere
applicati ai contenuti di questa base di dati. L'individuazione dei vincoli e
la loro implementazione (con vincoli sulle tabelle, trigger o quantomeno
definendo il codice e le query necessari ad effettuarne il controllo)
costituiscono un requisito importante per lo sviluppo di un progetto
realistico, e ne verrà tenuto conto durante la valutazione finale.  

### Operazioni da realizzare

Di seguito sono illustrate schematicamente le operazioni
previste sulla base di dati, ciascuna da realizzare tramite una query (o, se
necessario, tramite più query, *opzionalmente* racchiuse in una *stored
procedure*). Ovviamente, ogni ulteriore raffinamento o arricchimento di
queste specifiche aumenterà il valore del progetto.

<section class="operazioni">



1. inserimento di una richiesta di acquisto (comprensiva di categoria di prodotto, di tutte le caratteristiche richieste per quella categoria di prodotto e delle eventuali note)
2. associazione di una richiesta di acquisto a un tecnico incaricato  
3. approvazione del prodotto candidato relativo a una richiesta di acquisto 
4. eliminazione di una richiesta di acquisto dal sistema
5. estrazione lista delle richieste di acquisto *in corso* (non chiuse) di un determinato ordinante, aventi un prodotto candidato associato ma non ancora approvato o respinto
6. estrazione lista delle richieste di acquisto non ancora assegnate ad alcun tecnico
7. estrazione lista delle richieste di acquisto associate a un determinato tecnico con prodotto accettato ma non ancora ordinato
8. estrazione di tutti i dettagli di una richiesta di acquisto (richiesta iniziale, eventuale prodotto candidato, approvazione/rifiuto dell'ordinante con relativa motivazione)
9. conteggio richieste di acquisto gestite globalmente da un determinato tecnico
10. calcolo somma totale spesa da un determinato ordinante in un anno solare (*suggerimento*: si tratta dei prezzi dei prodotti candidati approvati, ordinati e con ordine chiuso con accettazione)
11. calcolo tempo medio di evasione di un ordine da parte dei tecnici (il tempo di evasione è dato dalla differenza tra il momento in cui viene inserita una richiesta di acquisto e quello in cui il prodotto viene ordinato. *suggerimento*: questo vuol dire che dovete prevedere alcuni *timestamp* nel database che saranno impostati nei momenti opportuni...)

</section>

È possibile inserire procedure di gestione addizionali che
si ritengano utili.

</section>

<section class="indicazioni break">

# Indicazioni per lo Sviluppo del Progetto

### Tecnologie da utilizzare

Il DBMS da utilizzare per la realizzazione del progetto è
MySQL. MariaDB è un'alternativa accettabile.

*Opzionalmente*, il database realizzato potrà essere dotato di
un'interfaccia scritta con un linguaggio di programmazione a scelta (Java o
PHP) tramite la quale invocare le query richieste (fornendone gli eventuali
parametri) e visualizzarne i risultati.  

### Svolgimento e Documentazione del Progetto

Le specifiche fornite potrebbero non risultare esaustive o
completamente definite. Ogni funzionalità aggiunta o raffinata, anche tramite
l'interazione con il committente, sarà adeguatamente valutata. Tutte le scelte
progettuali vanno comunque discusse e motivate.

Il progetto dovrà essere svolto secondo le seguenti fasi:

1. Formalizzazione ed analisi dei requisiti.

2. Progettazione concettuale tramite il modello Entità-Relazione.

3. Descrizione di tutti i vincoli non esprimibili nel modello ER.

4. Ristrutturazione ed ottimizzazione del modello ER.

5. Traduzione del modello ER nel corrispondente modello relazionale.

6. Implementazione effettiva del modello relazionale e di tutti i vincoli tramite SQL.

7. Implementazione delle query, procedure, funzioni, ecc. tramite SQL.

Tutte le fasi appena descritte dovranno essere corredate da
adeguata documentazione **in formato elettronico** che illustri quanto è stato
realizzato e le scelte intraprese. 

In particolare, dovranno essere
necessariamente inclusi nella documentazione gli schemi ER risultanti dai passi
(2) e (4), debitamente commentati, e il modello relazionale della base di dati
ottenuto al passo (5), in cui siano messe in evidenza le chiavi delle varie
tabelle e le relazioni tra queste ultime.

Il database finale, risultato dei passi (6) e (7), dovrà
essere consegnato nella forma di un *script SQL* contenente la struttura
del database (istruzioni CREATE, comprese eventuali procedure, funzioni e
viste) e il codice delle query necessarie a realizzare le funzionalità richieste. 
**Il codice di ciascuna query dovrà essere preceduto del suo numero identificativo e dal testo della
sua definizione**, come riportato nella presente specifica. 
*Opzionalmente*, lo script potrà comprendere anche dei dati di prova (istruzioni INSERT).    
*Suggerimento*: potete usare le funzioni di
esportazione presenti in tool come *phpMyAdmin*, *DBeaver* o *MySQL Workbench*, oppure direttamente il
comando *mysqldump*, per esportare un *dump* del database contenente sia la
struttura che i dati. Inoltre, per praticità, nella maggior parte dei casi
potrete incorporare anche la definizione delle query nel dump del database,
definendole come viste o stored procedures con nomi significativi come
"Query_1", ecc.

A puro titolo esemplificativo, all'interno del repository dei progetti 
del corso è presente un documento-base, strutturato seguendo le
indicazioni appena esposte, da cui è possibile derivare la propria documentazione.

Le parti della specifica marcate come *opzionali*, se
omesse, non renderanno il progetto insufficiente ma non gli permetteranno
comunque di raggiungere il massimo dei voti. Nel caso si decida di realizzarle,
non sarà necessario che siano perfette o complete, ma che dimostrino
chiaramente il vostro impegno nell'affrontare una tematica avanzata.

Nel caso di gruppi di lavoro composti da più componenti, *il
contributo effettivo offerto da ciascun componente* alla realizzazione
finale **deve** essere descritto nella documentazione (indicando, ad
esempio, chi si è dedicato prevalentemente alla modellazione concettuale, chi
ha realizzato il database con SQL, chi ha lavorato su ciascuna query, ecc.). In
sede di esame, i responsabili potranno essere chiamati a riferire sugli aspetti
loro delegati.  

### Consegna del Progetto

La *documentazione* e il *codice* del progetto descritti nella
sezione precedente andranno consegnati, anche per email, **almeno una
settimana prima** della data prevista per l'appello d'esame.   
*Non verranno in alcun caso concesse proroghe a questo termine*, perchè concedere 
anche un giorno in più a uno studente vorrebbe dire svantaggiare tutti gli altri che hanno 
consegnato per tempo o hanno organizzato i loro impegni per farlo, e che avrebbero 
anch'essi sicuramente beneficiato di un po' di tempo aggiuntivo, quantomeno per 
migliorare o rifinire il proprio lavoro.     
La consegna del progetto deve essere vista come un esame scritto: si svolge 
in un determinato giorno, poi viene corretto, e infine durante l'orale viene discusso. 
Il vantaggio del progetto è che può essere essere sviluppato nell'arco di molti mesi,
tuttavia il termine della consegna resta perentorio.

In sede di esame saranno discussi eventuali problemi
riscontrati nel progetto e potrà essere richiesta una dimostrazione del
funzionamento di alcune query e/o dell'eventuale interfaccia realizzata (è
quindi opportuno portare con sé un portatile con il progetto installato e
funzionante).

### Valutazione del Progetto


Nel valutare il progetto consegnato saranno prese in considerazione
le seguenti caratteristiche:

1. Rispetto delle specifiche e loro corretto raffinamento, ove necessario.

2. Correttezza e conformità alle specifiche dei modelli realizzati.

3. Correttezza tecnica dell'implementazione fisica del database (struttura, vincoli).

4. Correttezza tecnica delle query realizzate e loro aderenza alle funzionalità richieste.

5. Adeguatezza della documentazione.

A questa valutazione si aggiungerà quella generale derivata
dalla discussione del progetto in sede d'esame.  

### Ulteriori Informazioni

Questa specifica è disponibile nel repository del corso di Laboratorio di Basi di Dati, 
all'indirizzo https://github.com/LaboratorioBasiDiDati-Univaq/LBD_Project_Specifications. 
Ulteriori informazioni e chiarimenti sulle
specifiche possono essere richiesti direttamente via email all'indirizzo
giuseppe.dellapenna@univaq.it.

Si ricorda che i progetti vanno svolti in *piccoli*
gruppi (due/tre persone è il numero consigliato). Eccezioni a questa regola
andranno concordate direttamente col docente. 
</section>

