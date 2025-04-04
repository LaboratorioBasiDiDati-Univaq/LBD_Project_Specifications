# Corso di Laboratorio di Basi di Dati<br/>*Progetti A.A. 2024/2025* - Specifica 1

<section class="specifica">

## Progetto "Soccorso"
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



Il database *Soccorso* rappresenta una generica base di dati per la ricezione e la gestione di *richieste di soccorso*. La tipologia di soccorso offerto non ci interessa: ci concentreremo solo sul modo generale di realizzare questo tipo di database. 

Il database conterrà per prima cosa le informazioni su due categorie di utenza: gli *amministratori* (che configureranno il sistema, smisteranno le richieste e le monitoreranno) e gli *operatori* (a cui verranno inviate le richieste e che le gestiranno in prima persona). Gli amministratori potranno creare account per nuovi amministratori ed operatori. Per entrambe le categorie di utenza, oltre ai dati anagrafici, dovrà essere possibile inserire delle informazioni extra quali le *patenti* possedute (A, B, C, nautica,...) e una lista (generica) di *abilità* (ad esempio un operatore potrebbe avere un diploma infermieristico, un altro potrebbe essere un elettricista, ecc.) utili per deciderne l'assegnazione alle missioni. 

Per effettuare le operazioni di soccorso, gli operatori avranno a disposizione dei *mezzi* (auto, ambulanze, autopompe... dipende dal tipo di emergenza che verrà gestita effettivamente dal sito) e dei *materiali* (kit medici, scale, estintori,...). Tali elementi saranno censiti nel database (sempre per essere molto generici, essi avranno solo un nome e una descrizione), e gli amministratori potranno aggiungerli, modificarli o eliminarli.

Le *richieste* di soccorso immagazzinate nel database dovranno essere necessariamente accompagnate da una breve descrizione, dall'indicazione della posizione (indirizzo, coordinate, ecc.), dal nome e dell'indirizzo email del *segnalante*, e potranno essere opzionalmente corredate da una foto. Inoltre, per evitare spam e attacchi vari, il sistema dovrà tenere traccia quantomeno dell'indirizzo IP di origine delle richieste. Infine, ogni richiesta *inviata*, prima di diventare *attiva*, dovrà essere *convalidata*. A questo scopo, alla richiesta verrà associata una stringa lunga e casuale che sarà poi usata per costruire un link inviato per email al segnalante. Cliccando tale link, la richiesta verrà marcata come attiva nel database.

Le richieste, in base al loro stato di gestione, potranno essere in stato attivo (inviate e convalidate), in corso (gestite) e chiuso (concluse). 
Le richieste attive potranno essere ignorate (annullate) o gestite creando una *missione*. Tale missione avrà associati la richiesta scatenante, un obiettivo, una posizione, una *squadra* (composta da almeno un operatore *caposquadra* e da zero o più altri operatori), zero o più mezzi, zero o più materiali, oltre che ovviamente un timestamp di inizio.   

Gli amministratori potranno in ogni momento inserire degli *aggiornamenti* (blocchi di testo descrittivo) in una missione, ciascuno associato con il timestamp di immissione).

Infine, gli amministratori (a seguito di un’opportuna comunicazione da parte degli operatori) potranno marcare una missione come conclusa (chiusa), inserendo data/ora di fine, un generico *livello si successo* (anche questo dipendente dal tipo di soccorso, possiamo genericamente usare un numero che va da 0=fallimento a 5=successo pieno) e dei commenti opzionali relativi all’intervento eseguito. 

Ogni elemento coinvolto nelle missioni (operatori, mezzi, materiali) dovrà essere dotato anche di un proprio storico delle missioni in cui è stato coinvolto.


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



1. Inserimento di una richiesta di soccorso.
2. Creazione di una missione connessa a una richiesta di soccorso attiva.
3. Chiusura di una missione.
4. Estrazione della lista degli operatori non coinvolti in missioni in corso.
5. Calcolo del numero di missioni svolte da un operatore.
6. Calcolo del tempo medio di svolgimento delle missioni (*dalla creazione alla chiusura*) in un anno specifico o per ciascun caposquadra.
7. Calcolo del numero di richieste provenienti da un certo soggetto segnalante (identificato dall'indirizzo email) o da un certo indirizzo IP nelle ultime 36 ore.
8. Calcolo del tempo totale di impiego in missione di un certo operatore (*cioè somma delle durata delle missioni in cui è stato coinvolto*)
9. Estrazione delle missioni svoltesi negli ultimi tre anni nello stesso luogo di una missione data.
10. Estrazione della lista delle richieste di soccorso chiuse con risultato non totalmente positivo (livello di successo minore di 5).
11. Estrazione degli operatori maggiormente coinvolti nelle richieste di soccorso chiuse con risultato non totalmente positivo (*calcolate come alla query precedente*).
12. Estrazione dello storico delle missioni in cui è stato coinvolto un certo mezzo.
13. Calcolo delle ore d'uso di un certo materiale (*supponiamo che il tempo d'uso uso corrisponda alla durata totale della missione in cui è stato assegnato*).



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

