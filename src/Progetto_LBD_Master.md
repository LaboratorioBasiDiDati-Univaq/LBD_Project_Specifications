<html><head>
<meta charset="UTF-8"/>
<title>${nomecorso}: Progetti di Fine Corso</title>
<style>${css?no_esc}</style>
</head>

<body>

# Corso di ${nomecorso}<br/>*Progetti A.A. ${anno}/${(anno?number)+1}* - Specifica ${numero!""}

<section class="specifica">

## Progetto "${titolo}"
> Versione ${versione!"1.0"}

### Premessa

I progetti di fine corso si ispirano sempre ad esigenze
reali. La specifica informale del problema data nei paragrafi seguenti può
essere, come in ogni caso reale, incompleta e, in alcuni punti, ambigua o
contraddittoria. Lo studente dovrà quindi raffinare e disambiguare le
specifiche mediante l'interazione con il committente. In alcuni casi allo
studente sarà richiesto di valutare diverse possibili alternative, per poi
sceglierne una in maniera motivata. Le motivazioni di tutte le scelte
interpretative, progettuali e implementative andranno sempre chiaramente
documentate nel progetto e verranno discusse in sede di esame.

*Nota* : alcune delle funzionalità richieste dalla
specifica potrebbero non essere realizzabili con singole query, ma richiedere
l'uso di strumenti più avanzati messi a disposizione dal DBMS, come le
procedure. In ogni caso, tali procedure avrebbero una o più query come parte
principale. L'uso di queste caratteristiche avanzate aumenta notevolmente il
valore di un progetto. Tuttavia, nel caso si decida di non utilizzarle
nell'implementazione, è necessario comunque presentare lo pseudocodice
corrispondente, e realizzare *completamente* le query relative.  

### Specifiche

<section class="descrizione">${body_specifiche?no_esc}</section>

Ci sono indubbiamente svariati vincoli che possono essere
applicati ai contenuti di questa base di dati. L'individuazione dei vincoli e
la loro implementazione (con vincoli sulle tabelle, trigger o quantomeno
definendo il codice e le query necessari a effettuarne il controllo)
costituiscono un requisito importante per lo sviluppo di un progetto
realistico, e ne verrà tenuto conto durante la valutazione finale.  

### Operazioni da realizzare

Di seguito sono illustrate schematicamente le operazioni
previste sulla base di dati, ciascuna da realizzare tramite una query (o, se
necessario, tramite più query, *opzionalmente* racchiuse in una *stored
procedure*). Ovviamente, ogni ulteriore raffinamento o arricchimento di
queste specifiche aumenterà il valore del progetto.

<section class="operazioni">${body_operazioni?no_esc}</section>

È possibile inserire procedure di gestione addizionali che
si ritengano utili.

</section>

<#if !(escludi_indicazioni??)>

<section class="indicazioni break">${indicazioni?no_esc}</section>

</#if>


<#if includi_scheda??>

<section class="scheda break">${scheda?no_esc}</section>

</#if>


</body>
</html>