---
titolo: PollWeb
numero: 1
anno: 2021
materia: LBD
mainfile: Progetto_Master.rcp
thisfile: specifica
---

-------
{#specifiche}

Il database modella i dati di un sistema di sondaggi online.
Ciascun sondaggio avrà un utente responsabile, un titolo, un testo di apertura
e uno di chiusura, e sarà composto da una serie di domande. Ciascuna domanda, a
sua volta, potrà essere di una delle seguenti tipologie:
1. Testo breve: una riga di testo;
2. Testo lungo: più righe di testo;
3. Numero: solo numeri interi;
4. Data: solo date, opzionalmente con ora associata;
5. Scelta singola: vengono presentate una serie di
ozioni e l'utente deve sceglierne esattamente una;
6. Scelta multipla: vengono presentate una serie di
opzioni e l'utente può sceglierne una o più.

Tutti i tipi di domanda appena elencati avranno degli
attributi comuni: codice (usato per identificare univocamente la domanda),
testo (il testo della domanda), nota (una nota esplicativa che potrebbe
apparire dopo il quesito per guidarne la compilazione), obbligatoria (se
impostato, indica che l'utente deve necessariamente rispondere alla domanda, o
scegliere almeno una delle risposte nel caso delle domande a scelta multipla).
Altri attributi specifici potranno essere aggiunti a ciascun tipo di domanda
per definirla meglio, ad esempio

- Lunghezza minima e massima di un campo di testo;
- Valore minimo e massimo per i campi numerici (e
magari anche per quelli data);
- Espressione regolare che deve fare match con un
campo di testo;
- Numero minimo e/o massimo di opzioni
selezionabili per le scelte multiple.

Questi attributi sono tutti opzionali, ma più ne gestirete
più realistico diverrà il vostro progetto.

Un utente del sistema (che immagineremo definito dal un
profilo contenente i comuni dati anagrafici, anche questi ovviamente
memorizzati nel database) potrà essere invitato a compilare un sondaggio associandolo
ad esso e fornendogli una password temporanea, utile solo a compilare quel
determinato sondaggio (quindi se un utente viene invitato a compilare più
sondaggi, avrà una sola username ma password distinte per ciascuno di essi).

Quando un utente compila un sondaggio, le risposte da lui
fornite, opportunamente riferite alle domande a cui corrispondono, andranno
ovviamente immagazzinate nel database.

*Suggerimento: i più intraprendenti di voi potrebbero
trovare comodo definire questo database, la cui struttura è piuttosto
generica/dinamica nella parte relativa ai quesiti e alle relative risposte.
mescolando il modello relazionale con strutture JSON, sfruttando le estensioni
JSON di MySQL. Tuttavia, tutto può essere realizzato anche col "solito" modello
relazionale* *J.*

-------
{#operazioni}

1. Registrazione (inserimento dei dati del profilo) di un utente.
2. Abilitazione di un utente alla compilazione di un sondaggio.
3. Definizione di un sondaggio e aggiunta delle relative domande, una alla
volta.
4. Registrazione della risposta di un utente a una domanda di un sondaggio.
5. Elenco degli utenti che non hanno ancora risposto a un sondaggio cui
sono stati invitati.
6. Valore minimo, medio, massimo delle risposte a un particolare quesito
numerico.
7. Visualizzazione di tutti le risposte a un sondaggio di un determinato
utente.
8. Cancellazione di tutti i dati immagazzinati riferibili a un certo utente,
ad esclusione del suo profilo.
9. Modifica delle opzioni disponibili per una domanda a risposta multipla.
10. Conteggio del numero di risposte ricevute per un certo sondaggio.
11. Conteggio del numero di risposte a un certo quesito a risposta multipla
in cui gli utenti hanno selezionato una specifica opzione.
