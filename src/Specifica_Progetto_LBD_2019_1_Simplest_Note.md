---
titolo: Simplest Note
numero: 1
anno: 2019
materia: LBD
mainfile: Progetto_Master.rcp
thisfile: specifica
---

-------
{#specifiche}

Il database *SimplestNote* rappresenta la parte dati di
un semplice blocco note online, con possibilità di condivisione delle note,
revisione delle stesse e creazione di collegamenti tra note.

Il sito dovrà essere accessibile solo a un'utenza
registrata. Ciascun utente avrà a disposizione un blocco note virtuale,
composto da un numero arbitrario di pagine, che di seguito chiameremo
semplicemente *note* , ognuna dotata di *titolo* e *contenuto* .
Le singole note saranno associate alla data di creazione e a un numero
arbitrario di *tag* , intesi come parole o brevi sequenze di parole (ad
esempio "*novità* ", "*lavoro* " o "*corrispondenza privata*").

Il contenuto di ciascuna nota sarà composto da uno o più *paragrafi*
sequenziali. Ciascun paragrafo conterrà del testo, la data di ultima modifica e
un riferimento all'ultimo utente che ne ha modificato il contenuto. Il sistema
provvederà a salvare tutte le revisioni di ciascun paragrafo, in modo da
fornire una storia della stesura delle note. *In pratica, ad ogni modifica di
un paragrafo ne verrà creata una nuova copia, mentre il paragrafo col contenuto
precedente rimarrà nella base di dati come "storia".*

Sarà possibile condividere una nota con altri utenti del
sistema, fornendo loro accesso in lettura ed eventualmente anche in scrittura.

Infine, sarà possibile creare *gerarchie di note*,
definendo alcune note come sotto-note di altre.

-------
{#operazioni}


1. Inserimento di un utente.
2. Estrazione della data di ultima modifica di una nota. *Suggerimento:
si guardi alle date di ultima modifica dei singoli paragrafi.*
3. Estrazione della lista delle note presenti nel blocco di un utente con titolo
e data ultima modifica.
4. Creazione di una nuova nota nel blocco di un utente (vuota, fornendo
solo il titolo).
5. Visualizzazione del testo di una specifica nota. *Suggerimento:
concatenate il testo contenuto nelle ultime versioni dei paragrafi ad essa
associati.*
6. Accodamento di un paragrafo di testo a una nota.
7. Aggiornamento di un paragrafo di testo di una nota da parte di uno
specifico utente. *Suggerimento: prima di modificare un paragrafo, salvatene
la versione precedente.*
8. Ricerca di una nota in base al testo presente (sottostringa) nel titolo,
nel contenuto o nei tag. *Suggerimento: scrivete tre query separate.*
9. Concessione a un utente dei privilegi di lettura (o scrittura) su una
specifica nota.
10. Impostazione di una nota come sotto-nota di un'altra
11. Visualizzazione di tutte le sotto-note di una data nota. *Suggerimento:
con una singola query potrete visualizzare le sotto-note di primo livello (in
quanto SQL non è ricorsivo).* *Opzionalmente, provate ad estrarre tutte le
sotto-note (quindi anche le sotto-sotto-note e così via)*.
12. Visualizzazione dello storico delle modifiche per un determinato
paragrafo di una nota.
