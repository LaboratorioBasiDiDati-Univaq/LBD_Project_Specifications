---
titolo: Tirocini
numero: 1
anno: 2020
materia: LBD
mainfile: Progetto_Master.rcp
thisfile: specifica
---

-------
{#specifiche}

Il database *Tirocini* contiene i dati necessari alla
gestione dell'iter completo dei tirocini universitari. In particolare, conterrà
i dati delle aziende e le relative proposte (dettagliate) di tirocinio. Gli
studenti, anch'essi registrati, potranno liberamente cercare tra proposte e
aziende. Tutte le informazioni sui tirocini in corso e conclusi saranno
registrate nel database, nel quale gli studenti potranno fornire anche il
proprio parere sulle aziende nella quali abbiano trascorso un periodo.

Un'*azienda* dovrà essere registrata con i seguenti
dati: ragione sociale/nome, indirizzo della sede legale, codice fiscale/partita
IVA, nome e cognome del legale rappresentante, nome, cognome, telefono e
indirizzo email della persona responsabile della convenzione per i tirocini,
foro competente (città alla cui sede giudiziaria le parti dovranno rivolgersi
in caso di disputa legale). Questi dati sono deducibili dallo schema di
convenzione quadro che trovate all'indirizzo <http://www.disim.univaq.it/didattica/risorsa-1632>.
All'atto della registrazione l'azienda non sarà visibile agli studenti né potrà
inserire annunci finché l'amministratore non imposterà il flag "verificata" sul
suo profilo.

Un'*offerta* di tirocinio, collegata ovviamente
all'azienda che l'ha pubblicata, dovrà invece specificare obbligatoriamente il
luogo in cui si svolgerà (che può essere anche presso la sede del tirocinante,
nel caso si possa svolgere in remoto), gli orari (se previsti), il numero di
mesi/ore del tirocinio, gli obiettivi (generici), le modalità (lavoro nel team
aziendale, lavoro freelance in remoto, ecc.), eventuali rimborsi spese o altre
facilitazioni previste. Questi dati sono deducibili dalle prime pagine del
progetto formativo che trovate all'indirizzo <http://www.disim.univaq.it/didattica/risorsa-2767>.

Lo *studente* dovrà anch'egli registrarsi inserendo i
dati previsti dalla prima pagina del progetto formativo, cioè nome, data e
luogo di nascita, residenza, codice fiscale, telefono, corso di laurea al quale
è iscritto, e indicando se è portatore di handicap.

All'atto della creazione (attivazione) del tirocinio, dovranno
essere inseriti nel database anche tutti gli altri dati previsti dalle prime
tre pagine del progetto formativo *che non siano già deducibili dalla
registrazione dell'azienda, dello studente o dell'offerta relativi al tirocinio*,
come ad esempio i dati del tutore universitario, ecc.

Alla fine del tirocinio, l'azienda dovrà invece inserire le
informazioni necessarie a completare la penultima pagina del progetto
formativo, quindi le ore di tirocinio effettivamente svolte, la descrizione
dettagliata dell'attività e il giudizio finale.

Infine, ogni studente, una volta concluso il tirocinio,
potrà inserire un feedback relativo all'esperienza in generale e all'azienda
presso cui si è svolto, esprimendo una valutazione di gradimento nella scala
0-5.

-------
{#operazioni}

1. Registrazione (inserimento dei dati del profilo) di un'azienda e di uno
studente.
2. Inserimento di una proposta di tirocinio da parte di un'azienda *(dovreste
bloccare questo inserimento se l'azienda non risulta verificata)*.
3. Ricerca dei tirocini con criteri quali la città sede del tirocinio, la
durata minima/massima, parole chiave contenute negli obiettivi, ecc. *(potete
realizzare query distinte o provare a combinare i criteri)*
4. Attivazione (inserimento) di un nuovo tirocinio, con tutti i dati
richiesti.
5. Lista delle aziende con offerte di tirocinio ancora aperte (cioè a cui
non è legato alcun tirocinio attivo o concluso).
6. Annullamento di un'offerta di tirocinio. *Questa azione deve rendere
l'offerta non più ricercabile (né, se possibile, collegabile a nuovi tirocini),
ma non deve assolutamente eliminare i dati dei tirocini in corso o completati
ad essa collegati!*
7. Lista dei tirocini svolti da uno studente.
8. Classifica di gradimento delle aziende, pesata in base al numero di
tirocini svoltisi presso di essa e/o al livello di gradimento espresso dai
relativi tirocinanti *(potete creare query separate per questi due criteri
oppure cercare di combinarli)*.
9. Individuazione dei tutori di universitari (interni) più richiesti per i
tirocini.
10. Chiusura del tirocinio con inserimento dei dati necessari.
11. Inserimento del feedback sul tirocinio/azienda (*a tirocinio chiuso*).
12. Lista dei tirocini in corso.
13. Lista dei tirocini che sono giunti a scadenza (cioè sono passati i mesi
dichiarati a partire dalla data di inizio) ma non sono ancora ufficialmente
chiusi (con le azioni di cui alla query 10).
