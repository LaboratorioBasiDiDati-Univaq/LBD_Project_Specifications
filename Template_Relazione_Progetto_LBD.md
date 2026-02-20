# Laboratorio di Basi di Dati:  *Progetto "Titolo"*

**Gruppo di lavoro**:

| Matricola | Nome | Cognome | Contributo al progetto |
|:---------:|:----:|:-------:|:----------------------:|
|           |      |         |                        |
|           |      |         |                        |

**Data di consegna del progetto**: gg/mm/aaaa

## Analisi dei requisiti

- E' possibile riportare in questa sezione i **requisiti** copiati dal documento di specifica, oppure semplicemente riassumerne gli aspetti più importanti. 

- Vanno quindi (eventualmente) discusse tutte le scelte progettuali relative al dominio, le ambiguità e il modo in cui sono state risolte.

- E' possibile infine inserire qui un glossario che riporta tutti gli oggetti di dominio individuati, con la loro semantica, i loro eventuali sinonimi e le loro proprietà.

## Progettazione concettuale

- Riportate qui il **modello ER finale** della vostra base di dati. Cercate di renderlo *leggibile*, altrimenti correggerlo diventerà impossibile. Se è troppo piccolo, dividetelo in parti e/o allegate anche un'immagine ad alta risoluzione alla relazione.

- Commentate gli elementi non visibili nella figura (ad esempio il contenuto degli attributi composti) nonché le scelte/assunzioni che vi hanno portato a creare determinate strutture, se lo ritenete opportuno.

**Errori da evitare:**

- *Usare ID "sintetici" nei diagrammi ER come chiavi di entità in cui è possibile invece definire delle vere chiavi usando gli attributi ed eventualmente le relazioni.*   
  Come spiegato a lezione, nella progettazione concettuale dobbiamo sforzarci di produrre documenti, compreso il diagramma ER, che siano il più possibile aderenti alla realtà del dominio modellato. Se quindi dobbiamo distinguere tra loro le istanze di un'entità, dobbiamo farlo usando le informazioni effettivamente presenti in tali istanze. Solo a livello relazionale, e poi nel DBMS, potremo scegliere di creare chiavi "sintetiche", spesso usando le colonne auto-generate offerte dal DBMS, per praticità e velocità, "declassando" invece la chiave precedentemente identificata a un vincolo UNIQUE.

- *Inserire nelle entità attributi che derivano dalla successiva trasformazione nel modello relazionale.*   
  Ad esempio, i campi che vengono inseriti nelle tabelle relazionali per fungere da FOREIGN KEY non devono mai comparire nel modello ER, in quanto sono semplicemente utilizzati per realizzare nel modello relazionale la semantica delle relazioni dell'ER stesso. In altre parole, nel modello ER le relazioni sono esplicite e graficamente rappresentate, mentre le FOREIGN KEY le sostituiscono solo nel modello relazionale. 
  
- *Usare un diagramma delle classi (ad esempio quello generato dal MySQL Workbench) e non un "vero" diagramma ER come quello visto a lezione.*   
  Ci sono molti programmi di grafica con cui potete realizzare dei diagrammi ER con entità e vere relazioni (e se proprio non li trovate, potete sempre disegnarli a mano). Altri editor, invece, molto più legati al DBMS e al modello sottostante, vi permettono solo di creare degli pseudo-ER che sono una sorta di diagrammi delle classi (o delle tabelle in questo caso), in cui le cardinalità sono espresse graficamente (consiglio, soprattutto all'inizio, di usare invece le coppie di numeri (min,max) per la massima chiarezza) e soprattutto non sono previste le relazioni (indicate dai box a forma di rombo nell'ER classico). Questo porta a non inserire esplicitamente tali relazioni nel diagramma (ma solo una linea di associazione tra le entità, spesso senza un nome significativo) e/o a rappresentare le relazioni tramite generiche "join tables", che sono invece qualcosa che appartiene al modello relazionale.  

### Formalizzazione dei vincoli non esprimibili nel modello ER

- Elencate gli altri **vincoli** sui dati che avete individuato e che non possono essere espressi nel diagramma ER.

## Progettazione logica

### Ristrutturazione ed ottimizzazione del modello ER

- Riportate qui il **modello ER ristrutturato** ed eventualmente ottimizzato. 

- Discutete le scelte effettuate, ad esempio nell'eliminare una generalizzazione o nello scindere un'entità.

**Errori da evitare:**

- *Confondere la fase di ristrutturazione / ottimizzazione del modello ER con una iterazione di raffinamento del diagramma ER.*   
  Quella che definiamo "ristrutturazione e ottimizzazione del modello ER" è una fase ben specifica del processo, e non fa più propriamente parte della fase della progettazione concettuale, che arrivati a questo punto deve aver prodotto un modello ER finale, completo e corretto. Questa fase prevede invece solo una serie di trasformazioni che devono essere applicate al modello ER per adattarlo al meglio alla successiva trasformazione in modello relazionale. Ogni altra modifica al modello ER, quale l'inserimento di nuovi attributi o relazioni che non derivino dalle operazioni ammesse in questa fase, è un errore.

### Traduzione del modello ER nel modello relazionale

- Riportate qui il **modello relazionale** finale, derivato dal modello ER ristrutturato della sezione precedente e che verrà implementato in SQL in quella successiva. 

- Nel modello evidenziate le chiavi primarie e le chiavi esterne.

## Progettazione fisica

### Implementazione del modello relazionale

- Inserite qui lo *script SQL* con cui **creare il database** il cui modello relazionale è stato illustrato nella sezione precedente. Ricordate di includere nel codice tutti i vincoli che possono essere espressi nel DDL. 

- Potete *opzionalmente* fornire anche uno script separato di popolamento (INSERT) del database su cui basare i test delle query descritte nella sezione successiva.

**Errori da evitare:**

- *Non inserire esplicitamente le azioni ON DELETE e ON UPDATE sulle FOREIGN KEY.*   
  Non inserire queste azioni vuol dire affidarsi ai default del DBMS, che solitamente sono troppo restrittivi, soprattutto per gli ON UPDATE. E' sempre meglio dichiarare esplicitamente il comportamento che si vuole applicare automaticamente in questi casi, anche se il default ci soddisfa, per rendere chiare le nostre intenzioni.

### Implementazione dei vincoli

- Nel caso abbiate individuato dei **vincoli ulteriori** che non sono esprimibili nel DDL, potrete usare questa sezione per discuterne l'implementazione effettiva, ad esempio riportando il codice di procedure o trigger, o dichiarando che dovranno essere implementati all'esterno del DBMS.

### Implementazione funzionalità richieste

- Riportate qui il **codice che implementa tutte le funzionalità richieste**, che si tratti di SQL o di pseudocodice o di entrambi. *Il codice di ciascuna funzionalità dovrà essere preceduto dal suo numero identificativo e dal testo della sua definizione*, come riportato nella specifica.

- Se necessario, riportate anche il codice delle procedure e/o viste di supporto.

#### Funzionalità 1

> Definizione come da specifica

```sql
CODICE
```

#### Funzionalità 2

> Definizione come da specifica

```sql
CODICE
```

## Interfaccia verso il database

- Opzionalmente, se avete deciso di realizzare anche una **(semplice) interfaccia** (a linea di comando o grafica) in un linguaggio di programmazione a voi noto (Java, PHP, ...) che manipoli il vostro database , dichiaratelo in questa sezione, elencando
  le tecnologie utilizzate e le funzionalità invocabili dall'interfaccia. 

- Il relativo codice sorgente dovrà essere *allegato *alla presente relazione.

-----

**Raccomandazioni finali**

- Questo documento è un modello che spero possa esservi utile per scrivere la documentazione finale del vostro progetto di Laboratorio di Basi di Dati.

- Cercate di includere tutto il codice SQL nella documentazione, come indicato in questo modello, per facilitarne la correzione. Potete comunque allegare alla documentazione anche il *dump* del vostro database o qualsiasi altro elemento che ritenete utile ai fini della valutazione.

- Ricordate che la documentazione deve essere consegnata, anche per email, almeno *una settimana prima* della data prevista per l'appello d'esame. Eventuali eccezioni a questa regola potranno essere concordate col docente.
