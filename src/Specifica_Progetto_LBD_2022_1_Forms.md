---
titolo: Forms
numero: 1
anno: 2022
materia: LBD
mainfile: Progetto_Master.rcp
thisfile: specifica
---

-------
{#specifiche}

Il database *Forms* memorizza
modelli di documento (lettere tipo, modulistica pubblica, ecc.) e permette di
compilarli "al volo". Ogni *modello* avrà associato un nome, una descrizione, 
un riferimento all'autore (gli *autori*, con le loro email e gli altri dati di base, 
dovranno essere anch'essi registrati nel database), la data di ultima modifica, 
il numero (intero) di versione, il linguaggio di sviluppo (ad
esempio HTML, testo semplice, RTF, ecc.) e, ovviamente, il *testo* (per semplicità 
supporremo di avere solo modelli memorizzabili come testo semplice) del modello stesso. 
In tale testo potranno essere presenti di *campi*, scritti ad esempio nella forma "{{nome}}".

Ciascun *campo* sarà definito nel database (associandolo al modello) con il suo nome, una
descrizione, il tipo di dato che può contenere (testo, numero, elemento da
lista) e un valore suggerito/di default. Per i campi di tipo testo sarà
possibile specificare anche una lunghezza minima e massima, per quelli di tipo
numero un valore minimo e massimo e, per gli elementi da lista, ovviamente, la
lista tra cui scegliere (che dovrete scegliere come modellare nella maniera migliore).

I modelli inseriti da un autore dovranno essere approvati
prima di essere utilizzabili dagli altri utenti. Per questo ogni modello
disporrà di un flag apposito, che ne inibirà la compilazione finchè non sarà
impostato al valore vero.

Gli utenti, anche anonimi, potranno avviare la compilazione di uno specifico 
modello fornendone l'identificativo. Il sistema creerà allora un'*istanza* del modulo
associata al modello e all'utente che l'ha creata, nel caso non sia anonimo. A ogni istanza
sarà associato un identificativo, o token, che l'utente potrà poi usare per associare all'istanza stessa 
i dati corrispondenti ai campi del modello, che verranno anch'essi memorizzati nel database 
(per un periodo di tempo limitato) e potranno essere usati per generare il documento
compilato finale a partire dal modello.

-------
{#operazioni}

1. Inserimento di un modello e definizione dei relativi campi.
2. Approvazione di un modello.
3. Conteggio dei modelli inseriti da ciascun autore.
4. Lista modelli modificati più di recente.
5. Aggiornamento di un modello (con reimpostazione automatica
della data di ultima modifica e incremento automatico del numero di versione).
6. Lista (formattata al meglio possibile) di tutti
i campi di un determinato modello e delle informazioni ad esso associate.
7. Avvio della compilazione di un'istanza di uno
specifico modello (con generazione del relativo token).
8. Inserimento dei dati associati ai campi di
un'istanza, dato il relativo token (ovviamente è possibile inserire i dati di
ciascun campo tramite query distinte).
9. Rimozione di un'istanza.
10. Lista dei modelli più compilati dagli utenti.
11. Log delle compilazioni (token di istanza, data di creazione) di uno specifico modello.
12. Verifica della coerenza tra i valori dei campi inseriti per una certa istanza e la
definizione dei campi stessi: tutti i campi richiesti hanno un valore non
nullo? I vincoli di lunghezza e valore di ciascun campo sono rispettati? (*suggerimento: definire almeno le query
necessarie a ciascun controllo, che ritornino un valore pseudo-booleano; potrete poi provare a creare una procedura che realizzi il controllo completo iterando tra i campi del modello e verificando i corrispondenti dati dell'istanza*).
13. *Opzionalmente*, è possibile provare a
scrivere il codice che sostituisce, nel testo del modello associato a
un'istanza, i campi con i corrispondenti valori forniti dall'utente e
memorizzati nella base di dati. Questa operazione può essere svolta con una
stored procedure (usando cursori e funzioni di sostituzione di stringa) o
implementata nell'interfaccia Java/PHP.
