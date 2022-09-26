---
titolo: Guida TV
numero: 1
anno: 2021
materia: LBD
---

-------
{#specifiche}

Il database "Guida TV" alimenta una guida online ai
programmi televisivi. I relativi dati costituiranno quindi il palinsesto di un
certo numero di canali televisivi, per ognuno dei quali sarà disponibile
l'elenco dei programmi per ogni giorno. Verranno pubblicati i programmi dei
sette giorni successivi a quello corrente (ovviamente potranno essercene anche
meno, in base ai dati forniti dai vari editori), mentre per i programmi dei
giorni passati, anch'essi disponibili, è possibile prevedere un limite oltre il
quale tali informazioni saranno cancellate dal database, per evitare inutile
carico.

Di ogni programma avremo l'ora di inizio e fine, il nome,
una breve descrizione e il genere (i generi dovrebbero essere prelevati da una lista
predefinita). Potrà essere presente anche un link a una scheda di
approfondimento nonché un'immagine. Quest'ultima potrà essere interna o
collegata tramite un link esterno. Se il programma rappresenta un episodio di
una serie, avremo anche il numero di stagione e il numero di episodio nella
stagione. Infine, ai programmi potranno essere collegate delle "persone
coinvolte", ciascuna caratterizzata da uno specifico ruolo, ad esempio attore,
regista, presentatore, ecc.

Dall'esterno, sarà possibile consultare il palinsesto di
ogni canale (programmi di un certo giorno) ed effettuare ricerche per titolo
e/o genere, eventualmente ristrette a uno specifico canale e/o a un intervallo
temporale. La struttura del database dovrà quindi favorire questo tipo di query.

*Suggerimento: considerate che molto spesso nei palinsesti
figurano più volte gli stessi programmi, oppure episodi di una stessa serie.
Nel progettare il database provate a ottimizzarne al meglio la struttura in
base a questa considerazione. Ad esempio, se un film viene replicato in due
giorni diversi, il database non dovrebbe contenerne due volte tutte le
informazioni di base (titolo, descrizione, link...): solo i dati di messa in onda
(canale, ora, ecc.), che sono gli unici a cambiare, dovrebbero esistere in due
versioni diverse.*

Il database conterrà anche i dati di una serie di utenti
registrati. Questi potranno, in particolare, specificare le modalità di
ricezione di una email giornaliera con gli ultimi aggiornamenti al palinsesto.
La mail potrà contenere i programmi del giorno per alcuni canali selezionati,
eventualmente solo per certe fasce orarie (mattino/pomeriggio/sera/notte).

-------
{#operazioni}

1. Registrazione (inserimento dei dati del profilo) di un utente.
2. Inserimento di un programma televisivo (due casi: programma singolo o
episodio di una serie).
3. Generazione del palinsesto odierno di un canale (lista di ora di inizio,
nome programma, ora di fine e genere per ogni programma del giorno, ovviamente
ordinata per ora di inizio).
4. Lista dei canali/date/orari in cui sono trasmessi gli episodi di una
certa serie.
5. Lista dei programmi (o canali) maggiormente "preferiti" dagli utenti
(cioè indicati come parte della loro mail giornaliera).
6. Eliminazione di un programma televisivo dal database (considerate come
eliminarlo e quando permetterne veramente la cancellazione!).
7. Ricerca dei film di un certo genere in programma nei prossimi sette
giorni.
8. Ricerca dei programmi a cui partecipa a qualsiasi titolo (o con un
titolo specificato) una certa persona.
9. Numero programmi distinti trasmessi da ciascuna emittente in un
determinato giorno.
10. Minuti totali di programmazione per un certo canale in un certo giorno
(ottenuti sommando la durata, eventualmente calcolata, di tutti i programmi che
ha in palinsesto per quel giorno).
11. Generazione della email giornaliera per un utente in base alle sue
preferenze (cioè generazione del testo da inserire nell'email, come da
preferenze dell'utente).
