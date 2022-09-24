---
titolo: Meeting Planner
numero: 2
anno: 2019
---

-------
{#specifiche}

Il database *MeetingPlanner* rappresenta la parte dati
di un semplice sistema per organizzare riunioni.

In particolare, il database conterrà una lista di *sale
riunioni* disponibili. A ciascuna sala andranno associati il nome,
l'ubicazione, la capienza e una serie di attrezzature, scelte da una lista
predefinita (ad es. proiettore di lucidi, aria condizionata, impianto
microfonico, ecc.).

Gli organizzatori potranno creare delle *proposte di
riunione* specificando *quando* e *dove* (cioè in quale delle sale
riunioni) la riunione potrebbe svolgersi e invitando una serie di partecipanti.
Tali partecipanti saranno registrati nel database con i loro dati anagrafici,
comprensivi di un indirizzo email. Una proposta potrà contenere anche diverse
alternative, cioè diverse coppie (*quando* , *dove*).

Ciascun partecipante potrà accettare o declinare l'invito
relativo a ciascuna delle alternative specificate nella proposta, e questa
informazione andrà ovviamente registrata nel database.

Sulla base delle adesioni, una riunione potrà essere marcata
come confermata in una delle date proposte o annullata.

-------
{#operazioni}

1. Inserimento di una sala riunioni
2. Associazione delle attrezzature a una sala riunioni
3. Correzione (modifica) dell'ubicazione di una sala riunioni.
4. Cancellazione di una sala riunioni (si presti attenzione ad evitare le
inconsistenze).
5. Ricerca di una sala riunioni libera in una certa data e con una capienza
minima specificata.
6. Creazione di un invito a riunione (con specifica dei partecipanti) con
varie alternative di data/luogo.
7. Verifica di un partecipante: è in lista per una specifica riunione?
8. Registrazione della decisione di un partecipante su una delle alternative
contenute in un invito.
9. Estrazione del numero di adesioni a ciascuna delle alternative di una
riunione
10. Calcolo dell'alternativa di una riunione che ha ricevuto maggiori
adesioni
11. Individuazione dei partecipanti che non hanno ancora risposto a un
invito
12. Conferma di una riunione e dell'alternativa prescelta
13. Estrazione degli effettivi partecipanti a una riunione (cioè quelli che
hanno dato la loro adesione all'alternativa prescelta)
