# Corso di Laboratorio di Basi di Dati
*Progetti A.A. 2020/2021* - Specifica 1

## Progetto "Tirocini"

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

Il database *Tirocini* contiene i dati necessari alla gestione dell'iter completo dei tirocini universitari. In particolare, conterrà i dati delle aziende e le relative proposte (dettagliate) di tirocinio. Gli studenti, anch'essi registrati, potranno liberamente cercare tra proposte e aziende. Tutte le informazioni sui tirocini in corso e conclusi saranno registrate nel database, nel quale gli studenti potranno fornire anche il proprio parere sulle aziende nella quali abbiano trascorso un periodo.

Un'*azienda* dovrà essere registrata con i seguenti dati: ragione sociale/nome, indirizzo della sede legale, codice fiscale/partita IVA, nome e cognome del legale rappresentante, nome, cognome, telefono e indirizzo email della persona responsabile della convenzione per i tirocini, foro competente (città alla cui sede giudiziaria le parti dovranno rivolgersi in caso di disputa legale). Questi dati sono deducibili dallo schema di convenzione quadro che trovate all'indirizzo <http://www.disim.univaq.it/didattica/risorsa-1632>. All'atto della registrazione l'azienda non sarà visibile agli studenti né potrà inserire annunci finché l'amministratore non imposterà il flag "verificata" sul suo profilo.

Un'*offerta* di tirocinio, collegata ovviamente all'azienda che l'ha pubblicata, dovrà invece specificare obbligatoriamente il luogo in cui si svolgerà (che può essere anche presso la sede del tirocinante, nel caso si possa svolgere in remoto), gli orari (se previsti), il numero di mesi/ore del tirocinio, gli obiettivi (generici), le modalità (lavoro nel team aziendale, lavoro freelance in remoto, ecc.), eventuali rimborsi spese o altre facilitazioni previste. Questi dati sono deducibili dalle prime pagine del progetto formativo che trovate all'indirizzo <http://www.disim.univaq.it/didattica/risorsa-2767>.

Lo *studente* dovrà anch'egli registrarsi inserendo i dati previsti dalla prima pagina del progetto formativo, cioè nome, data e luogo di nascita, residenza, codice fiscale, telefono, corso di laurea al quale è iscritto, e indicando se è portatore di handicap.

All'atto della creazione (attivazione) del tirocinio, dovranno essere inseriti nel database anche tutti gli altri dati previsti dalle prime tre pagine del progetto formativo *che non siano già deducibili dalla registrazione dell'azienda, dello studente o dell'offerta relativi al tirocinio*, come ad esempio i dati del tutore universitario, ecc.

Alla fine del tirocinio, l'azienda dovrà invece inserire le informazioni necessarie a completare la penultima pagina del progetto formativo, quindi le ore di tirocinio effettivamente svolte, la descrizione dettagliata dell'attività e il giudizio finale.

Infine, ogni studente, una volta concluso il tirocinio, potrà inserire un feedback relativo all'esperienza in generale e all'azienda presso cui si è svolto, esprimendo una valutazione di gradimento nella scala 0-5.

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
1. Registrazione (inserimento dei dati del profilo) di un'azienda e di uno studente.
2. Inserimento di una proposta di tirocinio da parte di un'azienda *(dovreste bloccare questo inserimento se l'azienda non risulta verificata)*.
3. Ricerca dei tirocini con criteri quali la città sede del tirocinio, la durata minima/massima, parole chiave contenute negli obiettivi, ecc. *(potete realizzare query distinte o provare a combinare i criteri)*
4. Attivazione (inserimento) di un nuovo tirocinio, con tutti i dati richiesti.
5. Lista delle aziende con offerte di tirocinio ancora aperte (cioè a cui non è legato alcun tirocinio attivo o concluso).
6. Annullamento di un'offerta di tirocinio. *Questa azione deve rendere l'offerta non più ricercabile (né, se possibile, collegabile a nuovi tirocini), ma non deve assolutamente eliminare i dati dei tirocini in corso o completati ad essa collegati!*
7. Lista dei tirocini svolti da uno studente.
8. Classifica di gradimento delle aziende, pesata in base al numero di tirocini svoltisi presso di essa e/o al livello di gradimento espresso dai relativi tirocinanti *(potete creare query separate per questi due criteri oppure cercare di combinarli)*.
9. Individuazione dei tutori di universitari (interni) più richiesti per i tirocini.
10. Chiusura del tirocinio con inserimento dei dati necessari.
11. Inserimento del feedback sul tirocinio/azienda (*a tirocinio chiuso*).
12. Lista dei tirocini in corso.
13. Lista dei tirocini che sono giunti a scadenza (cioè sono passati i mesi dichiarati a partire dalla data di inizio) ma non sono ancora ufficialmente chiusi (con le azioni di cui alla query 10).

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
