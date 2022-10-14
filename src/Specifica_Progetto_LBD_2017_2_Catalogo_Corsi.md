---
titolo: Catalogo Corsi
numero: 2
anno: 2017
materia: LBD
mainfile: Progetto_Master.rcp
thisfile: specifica
---

-------
{#specifiche}


Il *Catalogo Corsi* rappresenta un catalogo di corsi
universitari online, semplificato ma rispondente ai principali requisiti di
trasparenza e completezza necessari per questo tipo di sistema.

Per prima cosa, il sistema dovrà supportare la **pubblicazione
bilingue** (italiano e inglese) di tutti i contenuti, requisito necessario
per l'internazionalizzazione. Dovrete quindi avere due versioni, una per
ciascuna lingua, per quasi tutte le informazioni elencate di seguito.

Inoltre poter creare una "guida virtuale" sarà necessario
che **il sistema raccolga tutte queste informazioni anno per anno** . Ciò
significa che dovrete **predisporre un sistema col quale i dati relativi a uno
specifico corso di seguito esposti siano associati a un anno accademico**, e
che ne possano quindi esistere diverse copie, per differenti anni accademici.

Ciascun corso dovrà essere necessariamente associato alle
informazioni che seguono. Qualunque altro extra, derivante dalla vostra
esperienza diretta, sarà apprezzato e magari di ispirazione per il futuro.
- Dati di base: nome, codice, settore scientifico-disciplinare
(SSD, ad esempio INF/01), lingua, semestre
- Lista docenti titolari
- Descrizione del corso: prerequisiti, obiettivi di apprendimento,
modalità d'esame, modalità di insegnamento, sillabo/programma analitico
(suddiviso per punti, in generale un punto per ciascun credito)
- Libri di testo (autore, titolo, volume, anno, editore, link web
se disponibile)
- Relazioni con altri insegnamenti: corsi propedeutici, corsi mutuati,
moduli (nel caso di corsi integrati)
- Collegamenti esterni (link): homepage del corso, risorse esterne,
forum/eLearning
- Note (ogni dettaglio per il quale non è prevista una voce
specifica)
- Informazioni sull'erogazione: lista dei corsi di laurea/curriculum
per il quale il corso è fruibile, con indicazione del relativo anno di corso,
del suo valore in crediti (CFU) e della rispettiva tipologia (A, B, C, D, F)

Gli *obiettivi di apprendimento* citati nella lista dovranno essere strutturati secondo i
cosiddetti *descrittori di Dublino* , richiesti dai processi di
standardizzazione europei. I descrittori richiedono che gli obiettivi del corso
siano descritti sulla base dei risultati raggiunti in cinque aree: *Knowledge*
(quali conoscenze sono acquisite con il corso?), *Application* (come e
dove sono applicabili le conoscenze derivanti dal corso?), *Evaluation*
(se e in che modo le conoscenze acquisite possono aiutare nel valutare,
giudicare, comparare...?), *Communication* (se e in che modo gli studenti
possono trasmettere la conoscenza acquisita?), *Lifelong learning skills*
(il corso fornisce strumenti per continuare ad apprendere determinati
argomenti?).

Ogni corso sarà infine associato a una lista di aggiornamenti svolti sui suoi dati. Ogni
record di tale lista farà riferimento al corso oggetto della modifica e al
docente che l'ha effettuata, e conterrà un *timestamp* e una descrizione
testuale del tipo "l'utente ha modificato le informazioni del corso".

Ci sono indubbiamente molti vincoli che possono essere
applicati ai contenuti di questa base di dati. Ad esempio, *alcune delle
informazioni relative a un corso, come gli obiettivi, non possono mai essere nulle
o vuote* , e *un corso non può essere erogato nello stesso anno accademico,
corso di laurea e curriculum in anni differenti ma con numero di crediti
diverso*. L'individuazione dei vincoli e la loro implementazione (con
vincoli sulle tabelle, trigger o quantomeno definendo il codice e le query
necessari a effettuarne il controllo) costituiscono un requisito importante per
lo sviluppo di un progetto realistico, e ne verrà tenuto conto durante la
valutazione finale.  

-------
{#operazioni}



1. Estrazione della lista completa dei corsi, eventualmente filtrata per
nome (anche parziale), codice, SSD, semestre, docente, lingua. (realizzate una
query-tipo che mostri come combinare questi parametri di filtro);
2. Creazione di un corso;
3. Inserimento/aggiornamento dei titolari di un corso;
4. Inserimento delle informazioni su un corso relative a uno specifico anno
accademico;
5. Visualizzazione della lista delle modifiche relative a un determinato corso;
6. Visualizzazione dell'attività di un determinato utente (operazioni
svolte) negli ultimi trenta giorni;
7. Estrazione delle informazioni base di un corso relative a un determinato
anno accademico;
8. Estrazione delle informazioni base *più recenti* relative a un
corso;
9. Elenco degli anni accademici per i quali esistono informazioni per un
determinato corso;
10. Storico (lista ordinata per anno accademico) dei titolari di un corso;
11. Elenco dei corsi erogati per uno specifico corso di laurea/curriculum in
un determinato anno accademico;
12. Data una lista di codici, verificare a quanti crediti assommano i
relativi corsi in uno specifico anno accademico e corso di laurea/curriculum;
13. Lista di tutti gli insegnamenti erogati al primo semestre di uno
specifico anno accademico;
14. Calcolo del numero di crediti erogati al secondo anno di uno specifico
corso di laurea/curriculum in un determinato anno accademico;
15. Calcolo del numero di crediti assegnati a ciascun docente (cioè la somma
dei crediti dei corsi di cui risulta titolare) in un determinato anno
accademico;
16. Estrazione della lista dei corsi mutuati da un determinato corso;
17. Estrazione della lista dei corsi tenuti in inglese nel corrente anno
academico;
18. Estrazione della lista dei curriculum per ciascun corso di laurea che
erogano almeno trenta crediti.
