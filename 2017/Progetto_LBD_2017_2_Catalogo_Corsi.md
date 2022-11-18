# Corso di Laboratorio di Basi di Dati
*Progetti A.A. 2017/2018* - Specifica 2

## Progetto "Catalogo Corsi"

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

*Nota* : alcune delle funzionalità richieste dalla
specifica potrebbero non essere realizzabili con singole query, ma richiedere
l'uso di strumenti più avanzati messi a disposizione dal DBMS, come le
procedure. In ogni caso, tali procedure avrebbero una o più query come parte
principale. L'uso di queste caratteristiche avanzate aumenta notevolmente il
valore di un progetto. Tuttavia, nel caso si decida di non utilizzarle
nell'implementazione, è necessario comunque presentare lo pseudocodice
corrispondente, e realizzare *completamente* le query relative.

### Specifiche

Il *Catalogo Corsi* rappresenta un catalogo di corsi universitari online, semplificato ma rispondente ai principali requisiti di trasparenza e completezza necessari per questo tipo di sistema.

Per prima cosa, il sistema dovrà supportare la **pubblicazione bilingue** (italiano e inglese) di tutti i contenuti, requisito necessario per l'internazionalizzazione. Dovrete quindi avere due versioni, una per ciascuna lingua, per quasi tutte le informazioni elencate di seguito.

Inoltre poter creare una "guida virtuale" sarà necessario che **il sistema raccolga tutte queste informazioni anno per anno** . Ciò significa che dovrete **predisporre un sistema col quale i dati relativi a uno specifico corso di seguito esposti siano associati a un anno accademico**, e che ne possano quindi esistere diverse copie, per differenti anni accademici.

Ciascun corso dovrà essere necessariamente associato alle informazioni che seguono. Qualunque altro extra, derivante dalla vostra esperienza diretta, sarà apprezzato e magari di ispirazione per il futuro.

* Dati di base: nome, codice, settore scientifico-disciplinare (SSD, ad esempio INF/01), lingua, semestre
* Lista docenti titolari
* Descrizione del corso: prerequisiti, obiettivi di apprendimento, modalità d'esame, modalità di insegnamento, sillabo/programma analitico (suddiviso per punti, in generale un punto per ciascun credito)
* Libri di testo (autore, titolo, volume, anno, editore, link web se disponibile)
* Relazioni con altri insegnamenti: corsi propedeutici, corsi mutuati, moduli (nel caso di corsi integrati)
* Collegamenti esterni (link): homepage del corso, risorse esterne, forum/eLearning
* Note (ogni dettaglio per il quale non è prevista una voce specifica)
* Informazioni sull'erogazione: lista dei corsi di laurea/curriculum per il quale il corso è fruibile, con indicazione del relativo anno di corso, del suo valore in crediti (CFU) e della rispettiva tipologia (A, B, C, D, F)

Gli *obiettivi di apprendimento* citati nella lista dovranno essere strutturati secondo i cosiddetti *descrittori di Dublino* , richiesti dai processi di standardizzazione europei. I descrittori richiedono che gli obiettivi del corso siano descritti sulla base dei risultati raggiunti in cinque aree: *Knowledge* (quali conoscenze sono acquisite con il corso?), *Application* (come e dove sono applicabili le conoscenze derivanti dal corso?), *Evaluation* (se e in che modo le conoscenze acquisite possono aiutare nel valutare, giudicare, comparare...?), *Communication* (se e in che modo gli studenti possono trasmettere la conoscenza acquisita?), *Lifelong learning skills* (il corso fornisce strumenti per continuare ad apprendere determinati argomenti?).

Ogni corso sarà infine associato a una lista di aggiornamenti svolti sui suoi dati. Ogni record di tale lista farà riferimento al corso oggetto della modifica e al docente che l'ha effettuata, e conterrà un *timestamp* e una descrizione testuale del tipo "l'utente ha modificato le informazioni del corso".

Ci sono indubbiamente molti vincoli che possono essere applicati ai contenuti di questa base di dati. Ad esempio, *alcune delle informazioni relative a un corso, come gli obiettivi, non possono mai essere nulle o vuote* , e *un corso non può essere erogato nello stesso anno accademico, corso di laurea e curriculum in anni differenti ma con numero di crediti diverso*. L'individuazione dei vincoli e la loro implementazione (con vincoli sulle tabelle, trigger o quantomeno definendo il codice e le query necessari a effettuarne il controllo) costituiscono un requisito importante per lo sviluppo di un progetto realistico, e ne verrà tenuto conto durante la valutazione finale.

Ci sono indubbiamente svariati vincoli che possono essere
applicati ai contenuti di questa base di dati. L'individuazione dei vincoli e
la loro implementazione (con vincoli sulle tabelle, trigger o quantomeno
definendo il codice e le query necessari a effettuarne il controllo)
costituiscono un requisito importante per lo sviluppo di un progetto
realistico, e ne verrà tenuto conto durante la valutazione finale.

### Operazioni da realizzare

Di seguito sono illustrate schematicamente le operazioni
previste sulla base di dati, ciascuna da realizzare tramite una query (o, se
necessario, tramite più query, *opzionalmente* racchiuse in una *stored
procedure*). Ovviamente, ogni ulteriore raffinamento o arricchimento di
queste specifiche aumenterà il valore del progetto.
1. Estrazione della lista completa dei corsi, eventualmente filtrata per nome (anche parziale), codice, SSD, semestre, docente, lingua. (realizzate una query-tipo che mostri come combinare questi parametri di filtro);
2. Creazione di un corso;
3. Inserimento/aggiornamento dei titolari di un corso;
4. Inserimento delle informazioni su un corso relative a uno specifico anno accademico;
5. Visualizzazione della lista delle modifiche relative a un determinato corso;
6. Visualizzazione dell'attività di un determinato utente (operazioni svolte) negli ultimi trenta giorni;
7. Estrazione delle informazioni base di un corso relative a un determinato anno accademico;
8. Estrazione delle informazioni base *più recenti* relative a un corso;
9. Elenco degli anni accademici per i quali esistono informazioni per un determinato corso;
10. Storico (lista ordinata per anno accademico) dei titolari di un corso;
11. Elenco dei corsi erogati per uno specifico corso di laurea/curriculum in un determinato anno accademico;
12. Data una lista di codici, verificare a quanti crediti assommano i relativi corsi in uno specifico anno accademico e corso di laurea/curriculum;
13. Lista di tutti gli insegnamenti erogati al primo semestre di uno specifico anno accademico;
14. Calcolo del numero di crediti erogati al secondo anno di uno specifico corso di laurea/curriculum in un determinato anno accademico;
15. Calcolo del numero di crediti assegnati a ciascun docente (cioè la somma dei crediti dei corsi di cui risulta titolare) in un determinato anno accademico;
16. Estrazione della lista dei corsi mutuati da un determinato corso;
17. Estrazione della lista dei corsi tenuti in inglese nel corrente anno academico;
18. Estrazione della lista dei curriculum per ciascun corso di laurea che erogano almeno trenta crediti.

È possibile inserire procedure di gestione addizionali che
si ritengano utili.

# Indicazioni per lo Sviluppo del Progetto

### Tecnologie da utilizzare

Il DBMS da utilizzare per la realizzazione del progetto è MySQL. MariaDB è un'alternativa accettabile.

Opzionalmente, il database realizzato potrà essere dotato di un'interfaccia scritta con un linguaggio di programmazione a scelta (Java o PHP) tramite la quale invocare le query richieste (fornendone gli eventuali parametri) e visualizzarne i risultati.

### Svolgimento e Documentazione del Progetto

Le specifiche fornite potrebbero non risultare esaustive o completamente definite. Ogni funzionalità aggiunta o raffinata, anche tramite l'interazione con il committente, sarà adeguatamente valutata. Tutte le scelte progettuali vanno comunque discusse e motivate.

Il progetto dovrà essere svolto secondo le seguenti fasi:

1. Formalizzazione ed analisi dei requisiti.
2. Progettazione concettuale tramite il modello Entità-Relazione.
3. Formalizzazione di tutti i vincoli non esprimibili nel modello ER.
4. Ristrutturazione ed ottimizzazione del modello ER.
5. Traduzione del modello ER nel corrispondente modello relazionale.
6. Implementazione effettiva del modello relazionale e di tutti i vincoli tramite SQL.
7. Implementazione delle query, procedure, funzioni, ecc. tramite SQL.

Tutte le fasi del progetto dovranno essere corredate da adeguata documentazione **in formato elettronico** che illustri quanto viene realizzato e le scelte intraprese. In particolare, dovranno essere necessariamente inclusi nella documentazione gli schemi ER risultanti dai passi (2) e (4), debitamente commentati, e il modello relazionale della base di dati ottenuto al passo (5), in cui siano messe in evidenza le chiavi delle varie tabelle e le relazioni tra queste ultime.

Il database finale, risultato dei passi (6) e (7), dovrà essere consegnato nella forma di un *script* SQL contenente la struttura del database (istruzioni CREATE, comprese eventuali procedure, funzioni e viste), dei dati di prova (istruzioni INSERT) e il codice delle query necessarie a realizzare le funzionalità richieste. **Il codice di ciascuna query dovrà essere preceduto del suo numero identificativo e dal testo della sua definizione**, come riportato nella presente specifica.

*Suggerimento*: potete usare le funzioni di esportazione presenti in phpMyAdmin e MySQL workbench oppure direttamente il comando mysqldump per esportare un dump del database contenente sia la struttura che i dati. Inoltre, per praticità, nella maggior parte dei casi potrete incorporare la anche definizione delle query nel dump del database, definendole come viste o stored procedures con nomi significativi come "Query_1", ecc.

Le parti della specifica marcate come *opzionali*, se omesse, non renderanno il progetto insufficiente ma non gli permetteranno comunque di raggiungere il massimo dei voti. Nel caso si decida di realizzarle, non sarà necessario che siano perfette o complete, ma che dimostrino chiaramente il vostro impegno nell'affrontare una tematica avanzata.

Nel caso di gruppi di lavoro composti da più componenti, *il contributo effettivo offerto da ciascun componente* alla realizzazione finale **deve** essere descritto nella documentazione (indicando, ad esempio, chi si è dedicato prevalentemente alla modellazione concettuale, chi ha realizzato il database con SQL, chi ha lavorato su ciascuna query, ecc.). In sede di esame, i responsabili potranno essere chiamati a riferire sugli aspetti loro delegati.

### Valutazione del Progetto

La documentazione e il codice del progetto descritti nella sezione precedente andranno consegnati, anche per email, almeno *una settimana prima* della data prevista per l'appello d'esame. Eventuali eccezioni a questa regola potranno essere concordate col docente.

In sede di esame saranno discussi eventuali problemi riscontrati nel progetto e potrà essere richiesta una dimostrazione del funzionamento di alcune query e/o dell'eventuale interfaccia realizzata (è quindi opportuno portare con sé un portatile con il progetto installato e funzionante).

Nel valutare il progetto consegnato saranno prese in considerazione le seguenti caratteristiche:

1. Rispetto delle specifiche e loro corretto raffinamento, ove necessario.
2. Correttezza e conformità alle specifiche dei modelli realizzati.
3. Correttezza tecnica dell'implementazione fisica del database (struttura, vincoli).
4. Correttezza tecnica delle query realizzate e loro aderenza alle funzionalità richieste.
5. Adeguatezza della documentazione.

A questa valutazione si aggiungerà quella generale derivata dalla discussione del progetto in sede d'esame.

### Ulteriori Informazioni

Questa specifica è disponibile in formato PDF sulla pagina web del corso di Laboratorio di Basi di Dati, all'indirizzo http://www.di.univaq.it/gdellape. Ulteriori informazioni e chiarimenti sulle specifiche possono essere richiesti direttamente via email all'indirizzo giuseppe.dellapenna@univaq.it.

Si ricorda che i progetti vanno svolti in *piccoli* gruppi (tre persone è il numero consigliato). Eccezioni a questa regola andranno concordate direttamente col docente.
