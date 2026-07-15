---
title: Panoramica di IA per la gestione dei contenuti di AEM
description: Scopri che cos’è IA per la gestione dei contenuti di AEM, perché è importante e come iniziare ad abilitarla e controllarla per il tuo ambiente AEM as a Cloud Service.
topic: Overview
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: IA per la gestione dei contenuti di AEM, panoramica, origine contenuti, ricerca semantica, acquisizione, Cloud Manager
source-git-commit: 2ff1bbdd3ff224e2a6b389243c78af5fd228d5ee
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 75%

---


# IA per la gestione dei contenuti di AEM: introduzione

## Contenuti intelligenti, progettati per l’IA {#ai-ready}

I clienti iniziano a incontrare i marchi tramite l’intelligenza artificiale prima di incontrare un sito web. Assistenti di chat, panoramiche dell’intelligenza artificiale, agenti, ricerca conversazionale, conferenze di intelligenza artificiale: tutti recuperano, riepilogano e rappresentano i contenuti del brand per conto del brand. Ciò che dicono è accurato, attuale e on-brand tanto quanto il contenuto che possono raggiungere.
Questo è il turno in cui IA per i contenuti di AEM è creata per. Tratta i contenuti del brand come la verità fondamentale su cui si basano le esperienze AI, e offre ai clienti di AEM gli strumenti per creare tale verità fondamentale più rapidamente dal lato dell’autore e distribuirla in modo chiaro alle esperienze basate sull’intelligenza artificiale per i consumatori dal lato della pubblicazione.

**Dal lato dell’autore**, l’IA per la gestione dei contenuti di AEM basa la creazione dei contenuti su origini del brand approvate. L’authoring basato sull’IA, la ricerca in linguaggio naturale tra i contenuti delle pagine esistenti, i frammenti e le risorse, nonché la generazione di contenuti in base al brand consentono ai team di produrre varianti destinate a nuovi tipi di pubblico, regioni e canali senza uscire da AEM e senza discostarsi da quanto già approvato.

**Durante la fase di pubblicazione**, lo stesso contenuto viene strutturato, gestito e reso accessibile affinché l’IA possa utilizzarlo. Frammenti, metadati, tassonomie e origini approvate vengono presentati in formati che i sistemi di ricerca, gli agenti e le interfacce conversazionali possono utilizzare con sicurezza: così, quando l’IA parla a nome del brand, ne trasmette l’essenza autentica.

### Cosa significa per la clientela di AEM {#what-it-means}

Il contenuto approvato è la difesa del marchio contro le allucinazioni. Quando l’intelligenza artificiale si basa su contenuti AEM gestiti, per impostazione predefinita le risposte rimangono precise, attuali e sul marchio.
L’authoring tiene il passo con la domanda dell’era dell’intelligenza artificiale. I team generano copie e immagini per più tipi di pubblico e momenti nell’esperienza di authoring, attingendo da origini approvate anziché lasciarle vuote.
La scoperta funziona come le persone e le macchine chiedono. La ricerca basata su intento in linguaggio naturale per risorse, frammenti, pagine e moduli trasforma il contenuto esistente in una risorsa riutilizzabile.
Personalization è scalabile tramite il riutilizzo, non la duplicazione. I componenti gestiti si ricombinano in varianti invece di moltiplicarsi in copie non tracciate.
I canali di pubblicazione ora includono superfici AI. Il contenuto viene distribuito in forme che gli esseri umani, gli agenti e le esperienze mediate dall’intelligenza artificiale possono utilizzare, senza pipeline separate per ciascuno di essi.

**Il punto fondamentale è che i contenuti dei brand affidabili già esistenti hanno oggi più valore che mai. Ogni frammento, risorsa e pagina approvati già presenti in AEM costituiscono la base su cui si fondano le esperienze basate sull’IA; l’IA per la gestione dei contenuti di AEM è ciò che rende tale libreria riutilizzabile, facilmente reperibile e pronta a dare vita alle novità future.**

## Panoramica dell’IA per la gestione dei contenuti di AEM {#at-a-glance}

L’IA per la gestione dei contenuti di AEM è strutturata come uno stack a quattro livelli: ogni livello si basa su quello sottostante, partendo dai contenuti affidabili che ne costituiscono la base fino alle esperienze agentiche che alimenta al livello superiore.

![Diagramma dello stack dell’architettura dell’IA per la gestione dei contenuti di AEM a quattro livelli: le origini dell’IA per la gestione dei contenuti alla base, i servizi fondamentali dell’IA per la gestione dei contenuti, l’orchestrazione dei contenuti agentici e l’orchestrazione delle esperienze agentiche nella parte superiore](../assets/content-ai-four-layer-architecture-stack.png)

*Leggi lo stack dal basso verso l’alto, dal contenuto attendibile alla base alle esperienze agentiche che gestisce nella parte superiore.*

1. Origini dell’IA per la gestione dei contenuti
Le origini del contenuto sono entità gestite nell’IA per la gestione dei contenuti di AEM che si connettono a un corpo di contenuto attendibile. Un’origine del contenuto può fare riferimento a un tipo di contenuto gestito da AEM come risorse, frammenti di contenuto, pagine, moduli, metadati e tassonomie, nonché a origini non AEM come siti web di terze parti, knowledge base o portali di documentazione. Ogni origine del contenuto viene automaticamente vettorializzata e arricchita semanticamente per potenziare le esperienze di ricerca, contestualizzazione e IA conversazionale. Definisci le origini dei contenuti una volta e riutilizzale in tutte le API di IA per la gestione dei contenuti grazie alla funzionalità integrata di aggiornamento automatico.

1. Servizi fondamentali dell’IA per la gestione dei contenuti
API e servizi che consentono l’intelligenza semantica e l’IA generativa nel contesto dei contenuti del brand. Integrandosi con le origini dell’IA per la gestione dei contenuti, questi servizi consentono il recupero, la generazione, la personalizzazione in base al brand e l’ottimizzazione, il tutto a seconda dei contenuti approvati dalla clientela.

1. Orchestrazione dei contenuti agentici
MCP e agenti che trasformano i requisiti di contenuto basati su casi d’uso in azioni coordinate attraverso il linguaggio naturale. Questo livello consente agli autori e ad altri agenti di descrivere le proprie esigenze in un linguaggio semplice e di disporre dei servizi fondamentali orchestrati per soddisfarle.

1. Orchestrazione delle esperienza agentiche
Casi d’uso innovativi che emergono quando i contenuti intelligenti di un brand soddisfano l’IA su larga scala. Le soluzioni AEM si basano proprio su questi servizi fondamentali e la clientela può utilizzare direttamente le stesse API per creare le proprie esperienze agentiche sui propri contenuti. Dalle catene di fornitura dei contenuti basate sull’IA ai percorsi di utenti conversazionali, questo livello è il punto in cui i contenuti gestiti diventano un vantaggio competitivo.

Questi livelli sono integrati tra loro: ogni servizio di IA attinge dalla base di contenuti e tutto ciò che viene prodotto confluisce nuovamente nello stesso sistema gestito; in questo modo, la creazione da parte degli autori e la consegna durante la fase di pubblicazione condividono un’unica fonte di verità.

## IA per la gestione dei contenuti di AEM in azione {#action}

Per ottenere un’integrazione funzionante dell’IA per la gestione dei contenuti è necessario eseguire due operazioni:

### &#x200B;1. Abilitare l’IA per la gestione dei contenuti per l’ambiente AEM {#enable}

**Prerequisito:** prima di iniziare a utilizzare l’IA per la gestione dei contenuti, è necessario disporre di credenziali API con ambito nell’ambiente AEM as a Cloud Service. Consulta [Configurare un progetto in Adobe Developer Console](setup-adc-project.md).

### &#x200B;2. Verificare le origini dell’IA per la gestione dei contenuti {#control}

Imposta e gestisci le origini di IA per la gestione dei contenuti per abilitare le esperienze basate sull&#39;intelligenza artificiale. Per ulteriori informazioni, consulta [Controllare le origini di contenuto](contentsources.md).

## Informazioni sulle API dell’IA per la gestione dei contenuti  {#apis}

Esplora l’ampiezza funzionale dell’IA per la gestione dei contenuti di AEM: le API mostrano tutto il potenziale della piattaforma. Consulta [API di IA per la gestione dei contenuti](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/).
