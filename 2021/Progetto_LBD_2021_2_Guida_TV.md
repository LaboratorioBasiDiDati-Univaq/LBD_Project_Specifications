# Corso di Laboratorio di Basi di Dati
*Progetti A.A. 2021/2022* - Specifica 2

## Progetto "Guida TV"

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

Il database "Guida TV" alimenta una guida online ai programmi televisivi. I relativi dati costituiranno quindi il palinsesto di un certo numero di canali televisivi, per ognuno dei quali sarà disponibile l'elenco dei programmi per ogni giorno. Verranno pubblicati i programmi dei sette giorni successivi a quello corrente (ovviamente potranno essercene anche meno, in base ai dati forniti dai vari editori), mentre per i programmi dei giorni passati, anch'essi disponibili, è possibile prevedere un limite oltre il quale tali informazioni saranno cancellate dal database, per evitare inutile carico.

Di ogni programma avremo l'ora di inizio e fine, il nome, una breve descrizione e il genere (i generi dovrebbero essere prelevati da una lista predefinita). Potrà essere presente anche un link a una scheda di approfondimento nonché un'immagine. Quest'ultima potrà essere interna o collegata tramite un link esterno. Se il programma rappresenta un episodio di una serie, avremo anche il numero di stagione e il numero di episodio nella stagione. Infine, ai programmi potranno essere collegate delle "persone coinvolte", ciascuna caratterizzata da uno specifico ruolo, ad esempio attore, regista, presentatore, ecc.

Dall'esterno, sarà possibile consultare il palinsesto di ogni canale (programmi di un certo giorno) ed effettuare ricerche per titolo e/o genere, eventualmente ristrette a uno specifico canale e/o a un intervallo temporale. La struttura del database dovrà quindi favorire questo tipo di query.

*Suggerimento: considerate che molto spesso nei palinsesti figurano più volte gli stessi programmi, oppure episodi di una stessa serie. Nel progettare il database provate a ottimizzarne al meglio la struttura in base a questa considerazione. Ad esempio, se un film viene replicato in due giorni diversi, il database non dovrebbe contenerne due volte tutte le informazioni di base (titolo, descrizione, link...): solo i dati di messa in onda (canale, ora, ecc.), che sono gli unici a cambiare, dovrebbero esistere in due versioni diverse.*

Il database conterrà anche i dati di una serie di utenti registrati. Questi potranno, in particolare, specificare le modalità di ricezione di una email giornaliera con gli ultimi aggiornamenti al palinsesto. La mail potrà contenere i programmi del giorno per alcuni canali selezionati, eventualmente solo per certe fasce orarie (mattino/pomeriggio/sera/notte).

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
1. Registrazione (inserimento dei dati del profilo) di un utente.
2. Inserimento di un programma televisivo (due casi: programma singolo o episodio di una serie).
3. Generazione del palinsesto odierno di un canale (lista di ora di inizio, nome programma, ora di fine e genere per ogni programma del giorno, ovviamente ordinata per ora di inizio).
4. Lista dei canali/date/orari in cui sono trasmessi gli episodi di una certa serie.
5. Lista dei programmi (o canali) maggiormente "preferiti" dagli utenti (cioè indicati come parte della loro mail giornaliera).
6. Eliminazione di un programma televisivo dal database (considerate come eliminarlo e quando permetterne veramente la cancellazione!).
7. Ricerca dei film di un certo genere in programma nei prossimi sette giorni.
8. Ricerca dei programmi a cui partecipa a qualsiasi titolo (o con un titolo specificato) una certa persona.
9. Numero programmi distinti trasmessi da ciascuna emittente in un determinato giorno.
10. Minuti totali di programmazione per un certo canale in un certo giorno (ottenuti sommando la durata, eventualmente calcolata, di tutti i programmi che ha in palinsesto per quel giorno).
11. Generazione della email giornaliera per un utente in base alle sue preferenze (cioè generazione del testo da inserire nell'email, come da preferenze dell'utente).

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
