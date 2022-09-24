---
titolo: Biblioteca
numero: 1
anno: 2017
---


-------
{#specifiche}


La *Biblioteca*rappresenta un semplice gestore di
catalogo bibliografico online.

Il catalogo conterrà una serie di *pubblicazioni* ,
ciascuna delle quali caratterizzata da un *titolo* , una lista di *autori* ,
un *editore* , una serie di *metadati* (vedi dopo) e, opzionalmente,
una *descrizione* testuale (sunto del contenuto o presentazione della
pubblicazione), un *indice* (composto dai titoli dei vari capitoli/sezioni
della pubblicazione, numerati e ordinati) e una serie di *sorgenti*
tramite le quali poter accedere alla pubblicazione o a parti di essa. Ciascuna
sorgente sarà caratterizzata da un *tipo* , una *URI* , da un *formato*
e da una *descrizione*. Esempi di sorgenti valide potrebbero essere i
seguenti:
- tipo="immagine", URI="http://server.net/cover.jpg",
formato="image/jpeg", descrizione="copertina"
- tipo="download", URI="http://server.net/book.pdf",
formato="application/pdf", descrizione="versione elettronica gratuita"
- tipo="acquisto", URI="http://www.amazon.it/xyz", formato="cartaceo,
copertina rigida", descrizione="acquista online"

Per quanto riguarda invece i *metadati* , questi saranno
costituiti (almeno) dalle seguenti informazioni: codice *ISBN* , numero di *pagine* ,
*lingua* , *data* di pubblicazione, lista delle *ristampe*
(numero e data) e *parole chiave* identificative (zero o più).

Ciascuna pubblicazione potrà essere associata a un certo
numero di *recensioni testuali* , le quali dovranno anche indicare *l'utente*
che le ha inserite e *la data/ora* dell'inserimento. Le recensioni saranno
*moderate* , quindi è necessario prevedere un *flag* che indichi se la
recensione è stata approvata oppure no dai moderatori. Infine, gli utenti
potranno anche assegnare il loro *like* alle pubblicazioni, che quindi
dovranno essere associate anche alla lista dei *like* ricevuti, con utente
e data.

Sarà inoltre necessario prevedere opportune strutture per
immagazzinare i dati dell'utenza. Il sistema, infatti, prevede due tipologie di
utenza: *attiva* e *passiva*. Gli utenti potranno registrarsi nel
sito fornendo i loro dati anagrafici, un indirizzo email (che verrà usato anche
come username) e, ovviamente, la password scelta. Il livello di utenza iniziale
sarà sempre quello passivo.

Per tener traccia delle modifiche effettuate alla
bibliografia dai vari utenti attivi, il sistema dovrà mantenere una "storia" di
ciascuna scheda bibliografica. Ogni *entry* di tale storia conterrà un *timestamp*,
il nome dell'utente e una descrizione della modifica. Potete scegliere voi il
dettaglio di questa descrizione: di base, sono accettabili anche descrizioni
del tipo "ha modificato la pubblicazione", "ha inserito la pubblicazione", "ha
approvato una recensione dell'utente X", ecc.

Ci sono indubbiamente molti vincoli che possono essere
applicati ai contenuti di questa base di dati. Ad esempio, *non dovrebbe
essere possibile per un utente inserire più di una recensione per la stessa
pubblicazione*. L'individuazione dei vincoli e la loro implementazione (con
vincoli sulle tabelle, trigger o quantomeno definendo il codice e le query
necessari a effettuarne il controllo) costituiscono un requisito importante per
lo sviluppo di un progetto realistico, e ne verrà tenuto conto durante la
valutazione finale.  


-------
{#operazioni}


1. Modifica del livello di un utente (da attivo a passivo e viceversa).
2. Estrazione elenco delle ultime dieci pubblicazioni inserite.
3. Estrazione elenco delle pubblicazioni aggiornate di recente (ultimi 30
giorni).
4. Estrazione elenco degli utenti più "collaborativi" (cioè quelli che hanno
inserito più pubblicazioni).
5. Estrazione elenco delle pubblicazioni inserite da un utente.
6. Estrazione catalogo, cioè elenco di tutte le pubblicazioni con titolo,
autori, editore e anno di pubblicazione, ordinato per titolo.
7. Estrazione dati completi di una pubblicazione specifica dato il suo ID.
8. Ricerca di pubblicazioni per ISBN, titolo, autore, e parole chiave.
9. Inserimento di una recensione relativa a una pubblicazione.
10. Approvazione o di una recensione (da parte del moderatore).
11. Inserimento di un *like* relativo a una pubblicazione.
12. Calcolo numero dei *like* per una pubblicazione.
13. Estrazione elenco delle recensioni approvate per una pubblicazione.
14. Estrazione elenco delle recensioni in attesa di approvazione.
15. Estrazione log delle modifiche effettuare su una pubblicazione.
16. Estrazione elenco delle pubblicazioni per le quali è disponibile un
download.
17. Estrazione della lista delle pubblicazioni in catalogo, ognuna con la
data dell'ultima ristampa
18. Data una pubblicazione, restituire tutte le pubblicazioni del catalogo
aventi gli stessi autori
