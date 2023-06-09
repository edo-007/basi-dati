
# Lez. 03 - Modellazione dei Dati mediante il Modello Entità–Associazione (ER)


Diagramma ER dello Schema AZIENDA Notazioni alternative – Diagrammi di classe UML, etc... 

### Database AZIENDA

L’azienda è organizzata in __DIPARTIMENTI__. Ogni dipartimento ha un nome, un numero ed un dipendente che lo dirige (direttore). Occorre gestire la data di inizio incarico del direttore del dipartimento.

Ogni dipartimento controlla un certo numero di __PROGETTI__. Ciascun progetto ha un nome, un numero e viene svolto in un singolo luogo (lideale?).

Occorre memorizzare il _codice scale_, _l’indirizzo_, lo _stipendio_, il _sesso_ e la _data di nascita_ di ciascun __DIPENDENTE__. Ciascun dipendente lavora per un solo dipartimento ma può essere impiegato in più di un progetto. Occorre gestire il numero di ore settimanali che ciascun dipendente impiega in ciascun progetto assegnatoli. Occorre gestire anche il supervisore di ciascun dipendente.



> Le **entità** sono specifici oggetti o cose del mini-mondo che sono rappresentate del database. Per esempio i DIPENDENTI, i DIPARTIMENTI, i PROGETTI. Uno specifico dipendente (e.g. Mario Rossi) viene definito un’istanza dell’entità DIPENDENTI.

> Gli **attributi** sono proprietà usate per descrivere un’entità. Per esempio i DIPENDENTI possono avere un Nome, un Codice Fiscale, un Indirizzo, etc...  
Ciascun attributo ha un insieme di valori (o tipo di dati) associato ad esso. Esempio: intero, stringa, data, ...

> Un **istanza** di un’entità avrà un valore per ciascuno degli attributi. Ad esempio uno speci co dipendente può avere Nome=‘Mario Rossi’,  
CF=‘MRRSSU73D24D548V’, Indirizzo=‘Via Paradiso 12’, ...

* * * 

### Tipi di Attributi

- **Semplici:** Ciascuna istanza ha un valore singolo, atomico per l’attributo. Ad esempio ( _CF, Sesso, ..._)

**Composti ( )**
L’attributo può essere composto da varie componenti. Per esempio, Indirizzo (Via/Viale/Piazza, nome, numero, cap, paese) oppure Nome
(Nome proprio, Cognome). La composizione può anche formare gerarchie in cui alcune componenti sono loro stesse composte.

**Multivalore { }**
Un’istanza può avere valori multipli per l’attributo. Ad esempio, TitoloDiStudio. Denotati come {TitoloDiStudio}.


### Entità, Istanze e Attributi chiave

- Le Entità vengono anche chiamate Tipi di Entità ed ogni elemento in questa entità viene chiamato Istanza dell’Entità

- In ogni Entità esiste un *Attributo che il cui valore è distinto (cioè unico) per ogni singola istanza* (elemento) dell’Entità.
    > Un Attributo con questa caratteristica è detto **Attributo chiave** Il valore dell’Attributo chiave è utile per identi care univocamente una singola istanza dell’Entità

* * *


### Associazioni

Un’**associazione** mette in riferimento *due o più entità* con uno specifico significato.  
Ogni **istanza di associazione** mette in riferimento due o più istanze di entità.  

Ad esempio, DIPENDENTE Mario Rossi *lavora* sul PROGETTO Database, oppure il DIPENDENTE Mario Rossi *dirige* il DIPARTIMENTO Database.  

Le associazioni si indicano generalmente con un verbo e le entità che vengono messe in riferimento si dice partecipano all’associazione. Ad esempio, DIPENDENTE e PROGETTO partecipano all’associazione LAVORA SU.   
**Grado di un’ associazione** = _# entità partecipati_. 
> LAVORA SU è un’associazione binaria (grado 2).


### Associazioni ed Istanze di Associazione

Più di un’associazione può avere le stesse entità come partecipanti. Ad esempio DIRIGE e LAVORA PER sono due associazioni distinte tra DIPENDENTI e DIPARTIMENTI, ma con signi cati diversi e istanze di associazione di inerenti.

### Entità Deboli ed Associazioni Identificanti


Un’entità è definita **debole** se `non possiede un attributo chiave`.  

Le sue istanze sono identi cate da una combinazione di:  

> Valore di una **chiave parziale** dell’entità debole;

> **Istanza dell’entità identificante** a cui è associata (tramite l’associazione identificante).  

**Esempio**:  
Le istanze dell’entità PARENTE possono essere identi cate dal Nome e dalla DataDiNascita, e dall’istanza dell’entità DIPENDENTE a cui sono associate. PARENTE è quindi un’entità debole con DIPENDENTE come entità identificante attraverso l’associazione identificante PARENTE DI.

### Vincoli sulle Associazioni
Vincoli sui rapporti di cardinalità:

**Cardinalità Massima**  
• Uno a uno (1:1)  
• Uno a molti (1:N) or Molti a uno (N:1)  
• Molti a molti (N:M)  

**Cardinalità Minima**  (_chiamato anche vincolo di partecipazione o vincolo di dipendenza di esistenza_)  
• zero (_partecipazione opzionale, non dipendenza di esistenza_)  
• uno o più (_partecipazione obbligatoria, dipendenza di esistenza_)  

### Associazioni ed Istanze di Associazione

Si possono esprimere anche **associazioni ricorsive**. Ambedue i partecipanti sono la stessa entità, ma con ruoli diversi.   
> COMANDATO DA è un’associazione ricorsiva con DIPENDENTE;  
Un’istanza di DIPENDENTE (*nel ruolo di  subordinato, lavoratore*) è associata ad un’altra istanza di DIPENDENTE (*nel ruolo di supervisore, boss, capo*). 

Nei diagrammi ER è necessario specificare i nomi dei ruoli che riveste l’entità partecipante in modo da permettere le distinzioni del caso.

**Un’associazione può avere anche degli attributi**; ( OreSettimanali in LAVORA SU ) 

> L’attributo può essere spostato **ad una qualsiasi** delle entità partecipanti nel caso l’associazione abbia rapporto di **cardinalità 1:1**.

> L’attributo può essere spostato all’istanza partecipante di **cardinalità maggiore** nel caso l’associazione abbia rapporto di **cardinalità 1:N**.

> L’attributo deve essere **proprio dell’associazione** nel caso si abbia rapporto di **cardinalità N:M**.
* * *
### Vincoli Strutturali
*un modo per esprimere la semantica delle associazioni*

**Rapporto di Cardinalità**   (di associazioni binarie)
> 1:1, 1:N, N:1, oppure M:N  

> MOSTRATO INDICANDO IL _NUMERO APPROPRIATO_ SUL SEGMENTO TRA ENTITÀ ED ASSOCIAZIONE

**Vincolo di partecipazione** (su ciascuna entità partecipante)
> Totale (*dipendenza di esistenza*) oppure parziale

> MOSTRATO UTILIZZANDO UN **SEGMENTO DOPPIO**  
### Notazione alternativa (min, max)
• Specificata su tutte le partecipazioni di un’entità **E** ad un’associazione **R**.
• Specica che ciascuna istanza e dell’entità E partecipa in `almeno min` ed al `massimo max` istanze di associazione   dell’associazione R.
> Default (no vincoli): min = 0, max = n

> Derivata dalla conoscenza dei vincoli del mini-mondo.

#### Esempio Notazione (min, max)
_Un dipartimento ha esattamente un direttore e un dipendente può dirigere (al massimo) un solo dipartimento._  
• Specificare (0,1) per la partecipazione di DIPENDENTE in DIRIGE
• Specificare (1,1) per la partecipazione di DIPARTIMENTO in DIRIGE
> .
>   |DIPENDENTE| ---`(0,1)`-----< __DIRIGE__ >----`(1,1)`--- |DIPARTINENTO|  
> .

<br>

_Un dipendente può lavorare per uno ed uno solo dipartimento ma un dipartimento può avere un numero qualsiasi di dipendenti._  
• Specificare (1,1) per la partecipazione di DIPENDENTE in LAVORA PER
• Specificare (0,n) per la partecipazione di DIPARTIMENTO in LAVORA PER
> .
>   |DIPENDENTE| ---`(1,1)`-----< __LAVORA PER__ >----`(0,N)`--- |DIPARTINENTO|  
> .

### Associazioni di grado superiore

_Le associazioni possono essere binarie, ternarie,..., n-arie._

In generale, `1 associazione n-aria` __!=__  `n associazioni binarie`

* * *
#### Data Modeling Tools

 DISEGNO
- Notazione concettuale poco signi cativa
- Per evitare problemi di estetica e di algoritmi per la disposizione, sono disponibili essenzialmente solo rettangoli
e linee e non rappresentano niente più che associazioni e vincoli su chiave primaria-esterna nelle tabelle risultanti.

 METODOLOGIA
- Scarso supporto interno
- Scarsi strumenti per la veri ca dei diagrammi o per suggerimenti.
* * *

### Problemi con il modello ER

Non supporta astrazioni molto utili quali:

> Sottoclassi  
> Specializzazione/generalizzazione.  

Modello EER  (_Extended Entity-Relationship_)  
> Incorpora associazioni di sottoclasse 
> Incorpora gerarchie di Specializzazione/Generalizzazione 

