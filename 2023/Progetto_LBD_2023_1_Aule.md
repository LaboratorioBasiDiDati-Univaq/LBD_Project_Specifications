# Corso di Laboratorio di Basi di Dati<br/>*Progetti A.A. 2023/2024* - Specifica 1

<section class="specifica">

## Progetto "Aule"
> Versione 1.0

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



Il database *Aule* rappresenta la struttura dati del sistema di gestione aule del nostro Ateneo (https://aule.univaq.it).

Ogni *aula* gestita dal sistema avrà associati un *nome*, una *posizione* (luogo, edificio, piano), una *capienza* (numero posti), l’email del *responsabile*, il numero di *prese* elettriche e di rete presenti, delle generiche *note* e la lista delle *attrezzature* disponibili (ad esempio proiettore, schermo motorizzato, schermo manuale, impianto audio, PC fisso, microfono a filo, microfono senza filo, lavagna luminosa, wifi). Le attrezzature associabili alle aule dovranno essere liberamente configurabili nel database.

Le aule saranno suddivise in *gruppi* (che potranno rappresentare dipartimenti, poli, ecc.), anch'essi liberamente configurabili. Ogni gruppo avrà un *nome* e una *descrizione*.

Sarà possibile allocare le aule assegnandovi degli *eventi*. Per semplicità, assumeremo che un evento non possa essere a cavallo di due o più giorni: in altre parole ogni evento si svolgerà in una singola giornata (di cui dovrà essere specificata la *data*), con una determinata *ora* di inizio e di fine. L’evento avrà associate anche una *descrizione*, il nome e l’email del *responsabile* dell’evento, una *tipologia* (lezione, esame, seminario, parziale, riunione, lauree, altro) e, per le tipologie lezione, esame e parziale, anche il nome di un *corso*. I corsi disponibili e i dati dei responsabili saranno anch'essi contenuti nel database.

Un evento potrà essere dichiarato come *ricorrente*, e in tal caso si dovrà specificare il tipo di ricorrenza (giornaliera, settimanale o mensile) e fino a che data ripeterlo. *Suggerimento: un evento ricorrente corrisponde a tutti gli effetti a un evento copiato nello stesso slot orario per tutti i giorni determinati dal tipo di ricorrenza, fino al termine specificato. Al momento della definizione di un evento ricorrente, quindi, potreste semplicemente creare tutta la serie di eventi singoli corrispondenti. Tali eventi avranno, però, un "ID master" in comune, in modo che li si possa mettere sempre in relazione (per poter, ad esempio, cancellare un intero evento ricorrente e non una singola ricorrenza). Ovviamente questa è un’idea, potete trovare anche altre soluzioni ugualmente o maggiormente valide.*


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



1. inserimento di una nuova aula
2. inserimento di un evento singolo e di un evento ricorrente
3. modifica di un evento ricorrente
4. eliminazione di un evento ricorrente
5. associazione di un'attrezzatura a un'aula
6. estrazione lista degli eventi associati a una specifica aula in una determinata settimana
7. estrazione lista degli eventi degli eventi delle prossime tre ore (cioè che inizieranno nell'arco delle prossime tre ore)
8. calcolo del numero di lezioni relative a un corso svoltesi in un determinato anno accademico e del corrispondente numero complessivo di ore di didattica (*si assuma che, dato un anno, l'anno accademico corrispondente vada da ottobre di quell'anno a giugno del successivo*)
9. estrazione di tutti gli eventi previsti nella giornata odierna nelle aule di un determinato gruppo
10. calcolo della percentuale d'uso di un'aula in un determinato giorno (cioè del rapporto tra il tempo totale per cui è allocata da eventi e la durata complessiva della giornata)
11. estrazione delle aule la cui percentuale media  giornaliera d'uso, calcolata in un mese specificato, è minore del 70% (*suggerimento*: partite dal risultato della query precedente, calcolatelo per tutti i giorni di un mese, fatene la media... potete provarci con una singola query o usando del codice)

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

### Valutazione del Progetto

La documentazione e il codice del progetto descritti nella
sezione precedente andranno consegnati, anche per email, almeno **una
settimana prima** della data prevista per l'appello d'esame. Eventuali
eccezioni a questa regola potranno essere concordate col docente.

In sede di esame saranno discussi eventuali problemi
riscontrati nel progetto e potrà essere richiesta una dimostrazione del
funzionamento di alcune query e/o dell'eventuale interfaccia realizzata (è
quindi opportuno portare con sé un portatile con il progetto installato e
funzionante).

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

