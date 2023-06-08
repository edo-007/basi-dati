

# Concetti ed Architetture


**Modelli dei dati**  
Insieme di concetti per descrivere la struttura di un database ed i vincoli da rispettare  

**Operazioni del modello dei dati**  
Operazioni per specificare recuperi ed aggionramenti del database in riferimento ai concetti del modello dei dati. Op. di base + Op definite da utente.

## Categorie modello dei dati
**Concettuale** (alto-livello, _semantico_)
> Concetti vicini al mondo in cui gli utenti percepiscono i dati. (es. entità obj)

**Fisico** (basso-livello, interno)
> Concetti che descrivono dettagliatamente come i dati sono memorizzati nella macchina.  

**Implementabili** (rappresentazionali)
> Concetti che possono essere comresi dagli utenti finali ma che non sono troppo lontani dal mondo in cui i dati sono organizzati nella macchina.

## Schema Vs Istanze

**Schema del Database:** Descrizione del database (struttura e vincoli)  
> **Diagramma di Schema:** Visualizzazione a diagramma di uno schema o di un suo qualche aspetto  
> **Costrutto dello Schema:** Componente dello schema o un oggetto all' interno di esso (STUDENTI, CORSI)  

**Istanza del Database:** I dati veri e propri contenuti del database in un particolare momento del tempo. Chiamata anche stato o occorrenza


## Schema Vs Stato

**Stato del Database:** Contenuto del DB in un particolare momento (solitamente ora)  
> **Stato Iniziale:** Stato del database appena caricato  
> **Stato Valido:** Stato che soddisfa strutture e vincoli del database  


Lo _schema_ del database non cambia molto spesso. Lo _stato_ del database cambia ogni volta che il database viene aggiornato.

schema = intensione  
stato  =  estensione

<hr> 

## Architettura a 3 livelli

• Proposta per supportare le caratteristiche dei DBMS di:
> - Indipendenza tra programmi e dati  
> - Supporto di viste multiple d’utente  
> - Uso di un catalogo per memorizzare la descrizione (schema) del database  

• Si vuole __separare__ _l’applicazione_ dalla _base di dati fisica_.


### I 3 Lv.

**Schema interno** che descrive le strutture di memorizzazione fisica ed i percorsi di accesso ai dati. Tipicamente usa un  modello dei dati fisico.

**Schema concettuale** [logico] al livello concettuale [logico], per descrivere le strutture ed i vincoli per tutto il database per una comunità di utenti. Usa un _modello dei dati concettuale o implementabile_.

**Schema esterno** al livello esterno, per descrivere le varie viste utente. Solitamente utilizza lo stesso modello dei dati del livello concettuale.

• È necessaria una *mappatura* tra i livelli di schemi per trasformare le richieste ed i dati.  
• I programmi applicativi fanno riferimento ad uno schema esterno e sono mappati dal DBMS sullo schema interno per l’esecuzione.

<hr>

## Indipendenza dei dati

**Indipendenza `logica` dei dati**: Capacità di modificare lo schema logico senza dover cambiare gli schemi esterni e le loro applicazioni.

**Indipendenza `fisica` dei dati**: Capacità di modificare lo schema interno senza dover cambiare lo schema logico.


Quando uno _schema di livello più basso viene modificato_, __solamente la mappatura__ tra questo schema e quelli di _livello
superiore_ devono essere modificate in un DBMS che supporti pienamente l’indipendenza dei dati.  
I livelli superiori rimangono inalterati. Quindi i programmi applicativi non devono essere modificati perché si riferiscono
solamente allo schema esterno.

* * * 

## Linguaggi dei DBMS

**Data Definition Language (DDL)**: 
> Usato dal DBA e dai progettisti per specificare lo `schema logico` del database.   
  In molti DBMS, il DDL è _utilizzato anche per definire gli schemi interno ed esterno_. 
  
> In qualche DMBS, _sono usati linguaggi separati_ per definire lo schema interno (`storage definition language` , __SDL__) e quello esterno (`view definition language`, __VDL__).

**Data Manipulation Language (DML)**: 
> Specificano _interrogazioni e gli aggiornamenti_ al database. Comandi DML (__data sublanguage__) incapsulati in un linguaggio di programmazione  classico (`linguaggio ospite`) oppure comandi DML stand-alone possono essere applicati direttamente (__query language__).
<br>

**Linguaggi di alto livello o non procedurali**: *Set-oriented*; specificano quali dati cercare e come estrarli. Anche chiamati dichiarativi. (`SQL`)

**Linguaggi di basso livello o procedurali**: *operano su un record per volta*; specificano come estrarre i dati ed includono costrutti come i cicli.

## Interfacce dei DBMS
- Interfacce basate su *menù* dove le richieste vengono composte da più step
- interfacce basate su *App* per dispositivi mobili
- Interfacce basate sui *moduli* (form) molto comuni sul Web
- Interfacce User-friendly: *grafiche* (Point and Click, Drag and Drop etc.)

Altre interfacce dei DBMS : `Lingua parlata, Parole chiave, Interfacce parametriche`  

**Consentono di**:
_creare_ accounts ed impostare le autorizzazioni, 
_impostare_ i parametri del sistema, 
_modificare_ gli schemi o i percorsi di accesso ai dati

<hr>

## Database System Utilities

- Loading data stored in files into a database. Includes data conversion tools.  
- Backing up the database periodically on tape.
- Reorganizing database file structures.
- Report generation utilities.
- Performance monitoring utilities.
- Other functions, such as sorting, user monitoring, data compression, etc. Other Tools  

### Data dictionary / repository  
Store schema descriptions and other information such as *design decisions*, *application program descriptions*, *user information*, *usage standards*, etc.  

- `Active data dictionary` is accessed by DBMS software and users/DBA.  
- `Passive data dictionary` is accessed by users/DBA only.  

- **Application Development Environments and CASE (computer-aided software engineering) tools:**
> - Examples – Power builder (Sybase), Builder (Borland) 

<hr>

### Architetture Centralizzate e Client – Server  

**DBMS Centralizzati**: 
> tutto le funzionalità sono raccolte in un singolo sistema; i programmi del DBMS, i programmi applicativi, le interfacce utente ed il database stesso sono su un unico computer.

**Architetture Client – Server di base**

Server Specializzati   
> • `Printer Servers`  
> • `Web Servers`  
> • `E-mail Servers`    

Clients
> • Forniscono _interfacce appropriate_ ed una _versione client_ del sistema per accedere ed utilizzare le risorse del server.  
> • macchine senza disco _oppure_ dei PC/Workstation con solamente il programma client.    
> • Sono connessi ai server attraverso qualche tipo di _rete_ (LAN: local area network, wireless network, etc.)  

DBMS Server
> • Forniscono i servizi di _interrogazione e di transazioni_ ai client.(detti anche _transaction servers_)

### Architetture Client – Server a due livelli per DBMS

• L' **interfaccia utente e applicativi** sono eseguiti sul client.  

• L’__interfaccia ODBC__ (Open Database Connectivity) fornisce una __API__ (`Application Program Interface`) che consente ai programmi lato client di effettuare chiamate al DBMS. La maggior parte dei produttori di DBMS forniscono i driver ODBC.  

• Un programma lato client può **connettersi a più DBMS**.

_In qualche DBMS alcune funzionalità proprie del server sono trasferite ai client, come ad esempio le funzioni di dizionario dei dati, di ottimizzazione e recovery. In questo caso il server viene indicato solamente come Data Server._

* * *

### Architetture Client – Server a tre livelli
 ( *per le applicazioni Web* )

Contiene un livello intermedio chiamato **Application Server o Web Server**:
> Contiene il software per le connessioni web, le regole e la logica (vincoli) dell’applicazionche accede ai dati necessari nel server DBMS.  
> Agisce come tramite per mandare i dati parzialmente processati tra server e client del DBMS.

**Ulteriori funzionalità e sicurezze :** cifratura dati a livello server e decrittazione dati sul client


### Classificazione dei DBMS

Basata sul **modello dei dati utilizzato**:
> • Legacy: Reticolari, Gerarchici  
> • Tradizionali: Relazionali  
> • Emergenti: NOSQL, Key-Value, Document.  

**Altre classificazioni**:  
• `SINGLE-user` (usati tipicamente su PC) **vs**. `MULTI-user` (la maggior parte dei DBMS).  
• `Centralizzati` (usano un singolo computer con un database) **vs**. `Distribuiti` (usano più computer e più database).  

> Distributed Database Systems have now come to be known as client server based database systems because they do not support a totally distributed environment, but rather a set of database servers supporting a set of clients.  


<br><br>

**Ambienti Distribuiti**  
• DBMS Distribuiti Omogenei  
• DBMS Distribuiti Disomogenei  
• Sistemi Multi-Database  



