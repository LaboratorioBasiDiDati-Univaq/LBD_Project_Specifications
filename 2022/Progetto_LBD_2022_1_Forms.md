# Corso di Laboratorio di Basi di Dati
*Progetti A.A. 2022/2023* - Specifica 1

## Progetto "Forms"

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

Il database *Forms* memorizza modelli di documento (lettere tipo, modulistica pubblica, ecc.) e permette di compilarli "al volo". Ogni *modello* avrà associato un nome, una descrizione, un riferimento all'autore (gli *autori* , con le loro email e gli altri dati di base, dovranno essere anch'essi registrati nel database), la data di ultima modifica, il numero (intero) di versione, il linguaggio di sviluppo (ad esempio HTML, testo semplice, RTF, ecc.) e, ovviamente, il *testo* (per semplicità supporremo di avere solo modelli memorizzabili come testo semplice) del modello stesso. In tale testo potranno essere presenti di *campi* , scritti ad esempio nella forma "{}".

Ciascun *campo* sarà definito nel database (associandolo al modello) con il suo nome, una descrizione, il tipo di dato che può contenere (testo, numero, elemento da lista) e un valore suggerito/di default. Per i campi di tipo testo sarà possibile specificare anche una lunghezza minima e massima, per quelli di tipo numero un valore minimo e massimo e, per gli elementi da lista, ovviamente, la lista tra cui scegliere (che dovrete scegliere come modellare nella maniera migliore).

I modelli inseriti da un autore dovranno essere approvati prima di essere utilizzabili dagli altri utenti. Per questo ogni modello disporrà di un flag apposito, che ne inibirà la compilazione finchè non sarà impostato al valore vero.

Gli utenti, anche anonimi, potranno avviare la compilazione di uno specifico modello fornendone l'identificativo. Il sistema creerà allora un'*istanza* del modulo associata al modello e all'utente che l'ha creata, nel caso non sia anonimo. A ogni istanza sarà associato un identificativo, o token, che l'utente potrà poi usare per associare all'istanza stessa i dati corrispondenti ai campi del modello, che verranno anch'essi memorizzati nel database (per un periodo di tempo limitato) e potranno essere usati per generare il documento compilato finale a partire dal modello.

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
1. Inserimento di un modello e definizione dei relativi campi.
2. Approvazione di un modello.
3. Conteggio dei modelli inseriti da ciascun autore.
4. Lista modelli modificati più di recente.
5. Aggiornamento di un modello (con reimpostazione automatica della data di ultima modifica e incremento automatico del numero di versione).
6. Lista (formattata al meglio possibile) di tutti i campi di un determinato modello e delle informazioni ad esso associate.
7. Avvio della compilazione di un'istanza di uno specifico modello (con generazione del relativo token).
8. Inserimento dei dati associati ai campi di un'istanza, dato il relativo token (ovviamente è possibile inserire i dati di ciascun campo tramite query distinte).
9. Rimozione di un'istanza.
10. Lista dei modelli più compilati dagli utenti.
11. Log delle compilazioni (token di istanza, data di creazione) di uno specifico modello.
12. Verifica della coerenza tra i valori dei campi inseriti per una certa istanza e la definizione dei campi stessi: tutti i campi richiesti hanno un valore non nullo? I vincoli di lunghezza e valore di ciascun campo sono rispettati? (*suggerimento: definire almeno le query necessarie a ciascun controllo, che ritornino un valore pseudo-booleano; potrete poi provare a creare una procedura che realizzi il controllo completo iterando tra i campi del modello e verificando i corrispondenti dati dell'istanza*).
13. *Opzionalmente*, è possibile provare a scrivere il codice che sostituisce, nel testo del modello associato a un'istanza, i campi con i corrispondenti valori forniti dall'utente e memorizzati nella base di dati. Questa operazione può essere svolta con una stored procedure (usando cursori e funzioni di sostituzione di stringa) o implementata nell'interfaccia Java/PHP.

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

Questa specifica è disponibile nel repository del corso di Laboratorio di Basi di Dati, all'indirizzo https://github.com/LaboratorioBasiDiDati-Univaq/LBD_Project_Specifications. Ulteriori informazioni e chiarimenti sulle specifiche possono essere richiesti direttamente via email all'indirizzo giuseppe.dellapenna@univaq.it.

Si ricorda che i progetti vanno svolti in *piccoli* gruppi (due/tre persone è il numero consigliato). Eccezioni a questa regola andranno concordate direttamente col docente.
