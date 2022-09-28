---
titolo: Developers
numero: 2
anno: 2020
materia: LBD
mainfile: Progetto_Master.rcp
thisfile: specifica
---

-------
{#specifiche}

Il database *Developers* rappresenta uno strumento di
supporto allo sviluppo di software in maniera collaborativa. Gli utenti del
sito, che chiameremo *sviluppatori* (in senso lato, potrebbero anche
essere dei grafici) dovranno inizialmente registrarsi fornendo, oltre ai loro
dati anagrafici e di contatto, anche il loro curriculum in forma testuale
oppure come PDF da caricare nel sistema. Gli sviluppatori dovranno inoltre
elencare le loro capacità (che chiameremo *skill* ), scelte da una lista
predefinita di *skill* presenti nel sistema, indicando per ciascuna il *livello*
di competenza raggiunto (diciamo da 1 a 10, ad esempio "Programmazione C++"
livello 8, oppure "Responsive design" livello 5, ecc.). Le skill potranno *opzionalmente*
avere una struttura gerarchica (ad esempio "Design interfacce Swing" potrebbe
essere un "figlio" di "Programmazione Java"), per meglio organizzarne la
successiva ricerca.

Ogni sviluppatore potrà creare dei *progetti* , divenendone
*coordinatore* , e associarvi dei *task* , cioè attività da realizzare
per completarlo. Un *task* sarà corredato da una *descrizione*
testuale, dal *numero di collaboratori* che dovranno lavorarci, e da un *intervallo
temporale* fissato per il suo completamento. Ogni *task* , inoltre, avrà
un *tipo* (molto generico e scelto da una lista predefinita, come
"sviluppo", "grafica", "documentazione", ecc.) e un elenco *skill*
richieste a chi ci lavorerà, ognuna con un *livello* minimo di competenza
(sempre nella scala da 1 a 10). Le *skill* andranno scelte dalla stessa
lista usata per definire le capacità degli sviluppatori, ma in questo caso potranno
essere solo quelle specifiche per il tipo di *task* selezionato (ad
esempio "Programmazione Java" non deve essere disponibile per un task di tipo
"grafica")*.*

Un *task* potrà essere *aperto* (attivo) o *chiuso* (concluso). Su ciascun task collaboreranno uno o più sviluppatori. Il
coordinatore del progetto potrà anche assegnare a ciascun collaboratore una *valutazione*
(in una scala 1-5).

A ciascun task potranno essere associati uno o più *file*,
ciascuno corredato di nome, tipo, data di ultima modifica, utente che ha
compiuto l'ultima modifica, e ovviamente contenuto. Il sistema dovrà conservare
tutte le precedenti versioni di ciascun file (cioè registrarne la "storia"
completa).

Infine, nell'ambito di un progetto potranno essere postati *messaggi*
(annunci, richieste, discussioni interne) sia pubblici, cioè visibili da ogni
utente, sia privati, cioè visibili solo dagli iscritti al progetto.

-------
{#operazioni}

1. Lista di tutti i progetti attivi nel sistema (cioè con *task* ancora aperti).
2. Inserimento di un nuovo un progetto e dei suoi *task*.
3. Individuazione dei progetti più attivi, sulla base delle ultime modifiche ai loro files.
4. Individuazione dei progetti *stagnanti* , cioè con *task* attivi tra i cui file l'ultima modifica risalga a più di un anno addietro.
5. Ricerca di sviluppatori sulla base di un insieme di *skill* e *opzionalmente* con un livello minimo di competenza per ciascuna di esse. *Per semplicità, potete limitarvi a una o due skill.*
6. Ricerca di progetti per parola chiave (nel nome o nella descrizione).
7. Inserimento di uno sviluppatore.
8. Aggiornamento delle *skill* di uno sviluppatore.
9. Inserimento di una valutazione per uno sviluppatore relativamente a un *task* a cui ha collaborato.
10. Generazione del "curriculum" di uno sviluppatore, cioè della lista dei progetti/*task* a cui ha lavorato o lavora. Se il *task* è terminato, tale lista includerà anche la valutazione dello sviluppatore data dal coordinatore del progetto.
11. Modifica di un progetto: variazione delle date associate a un *task.*
12. Esclusione di uno sviluppatore da un task a cui sta correntemente partecipando.
13. Ripristino della versione precedente (in ordine temporale) di un file sorgente.
14. Generazione della storia delle modifiche a un file sorgente: data e nome dell'utente che ha effettuato le modifiche.
