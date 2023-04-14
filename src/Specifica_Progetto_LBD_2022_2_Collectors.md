---
titolo: Collectors
numero: 2
anno: 2022
materia: LBD
mainfile: Progetto_Master.rcp
thisfile: specifica
---

-------
{#specifiche}

Il database *Collectors* memorizza informazioni relative a collezioni di dischi (anche se lo stesso
tipo di database potrebbe adattarsi quasi a qualunque tipo di collezione,
useremo i dischi come caso di studio in modo da poter aggiungere più dettagli
alla specifica).

Nel database andranno prima di tutto registrati i dati (saranno
sufficienti nickname e indirizzo email) relativi ai *collezionisti*, e poi i dati relativi alle loro *collezioni* di dischi (dovete
prevedere che ogni collezionista possa creare più collezioni, ciascuna con un
nome distinto). Per ogni *disco* in una
collezione, dovranno essere specificati gli autori, il titolo, l'anno di uscita,
l'etichetta (casa editrice), il genere (scelto da una lista predefinita di generi
musicali), lo stato di conservazione dell'oggetto (scelto da una lista
predefinita), il formato (vinile, CD, digitale,...), il numero di barcode, se disponibile (i codici a
barre garantiscono l'identificazione univoca dell'elemento), e poi ovviamente
la lista delle *tracce*, ciascuna con titolo, durata, ed eventuali informazioni
su compositore ed esecutore (cantante, musicista), se diverso da quelli
dell'intero disco. Infine, ogni disco potrebbe essere associato a una o più immagini
(copertina, retro, eventuali facciate interne o libretti, ecc.). Insomma,
cercate di essere il più realistici possibile.

Per ogni disco, il collezionista potrà inoltre indicare
l'eventuale numero di *doppioni* a sua
disposizione (spesso si hanno più copie dello stesso disco, magari a seguito di
scambi, e magari anche perché se ne prevede la rivendita).

I collezionisti potranno decidere di *condividere* la propria collezione con specifici utenti o in maniera
pubblica. Ogni collezione avrà quindi associato un flag privato/pubblico e la
lista di collezionisti con i quali è stata condivisa.

-------
{#operazioni}

1. Inserimento di una nuova collezione.
2. Aggiunta di dischi a una collezione e di tracce a un disco.
3. Modifica dello stato di pubblicazione di una collezione (da privata a pubblica e viceversa) e aggiunta di nuove condivisioni a una collezione.
4. Rimozione di un disco da una collezione.
5. Rimozione di una collezione.
6. Lista di tutti i dischi in una collezione.
7. Track list di un disco.
8. Ricerca di dischi in base a nomi di autori/compositori/interpreti e/o titoli. Si potrà decidere di includere nella ricerca le collezioni di un certo collezionista e/o quelle condivise con lo stesso collezionista e/o quelle pubbliche. *(Suggerimento: potete realizzare diverse query in base alle varie combinazioni di criteri di ricerca. Usate la UNION per unire i risultati delle ricerche effettuate sulle collezioni private, condivise e pubbliche)*
9. Verifica della visibilità di una collezione da parte di un collezionista. *(Suggerimento: una collezione è visibile a un collezionista se è sua, condivisa con lui o pubblica)*
10. Numero dei brani (tracce di dischi) distinti di un certo autore (compositore, musicista) presenti nelle collezioni pubbliche.
11. Minuti totali di musica riferibili a un certo autore (compositore, musicista) memorizzati nelle collezioni pubbliche.
12. Statistiche (*una query per ciascun valore*): numero di collezioni di ciascun collezionista, numero di dischi per genere nel sistema.
13. *Opzionalmente*, dati un numero di barcode, un titolo e il nome di un autore, individuare tutti i dischi presenti nelle collezioni che sono più coerenti con questi dati (funzionalità utile, ad esempio, per individuare un disco già presente nel sistema prima di inserirne un doppione). L'idea è che il barcode è univoco, quindi i dischi con lo stesso barcode sono senz'altro molto coerenti, dopodichè è possibile cercare dischi con titolo simile e/o con l'autore dato, assegnando maggior punteggio di somiglianza a quelli che hanno più corrispondenze. Questa operazione può essere svolta con una stored procedure o implementata nell'interfaccia Java/PHP.
