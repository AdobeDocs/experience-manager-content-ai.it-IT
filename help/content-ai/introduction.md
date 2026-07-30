---
title: Panoramica di IA per la gestione dei contenuti di AEM
description: Scopri che cos’è IA per la gestione dei contenuti di AEM, perché è importante e come iniziare ad abilitarla e controllarla per il tuo ambiente AEM as a Cloud Service.
topic: Overview
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: IA per la gestione dei contenuti di AEM, panoramica, origine contenuti, ricerca semantica, acquisizione, Cloud Manager
source-git-commit: 2ff1bbdd3ff224e2a6b389243c78af5fd228d5ee
workflow-type: ht
source-wordcount: '885'
ht-degree: 100%

---


# IA per la gestione dei contenuti di AEM: introduzione

## Contenuti intelligenti, progettati per l’IA {#ai-ready}

Le persone iniziano a conoscere i brand tramite l’IA prima ancora di visitare un sito web. Assistenti di chat, panoramiche IA, agenti, ricerca conversazionale, concierge basati su IA: tutti recuperano, riepilogano e rappresentano i contenuti del brand per conto dello stesso. Ciò che dicono è accurato, attuale e in linea con il brand solo nella misura in cui lo sono i contenuti a cui riescono ad accedere.
Questo è il cambiamento per cui è stata progettata l’IA per la gestione dei contenuti di AEM. Considera i contenuti del brand come la base su cui si fondano le esperienze di IA e garantisce alla clientela AEM gli strumenti per creare tale base più rapidamente dal lato dell’autore e per fornirla in modo chiaro per le esperienze basate sull’IA rivolte ai consumatori quando si è nella fase di pubblicazione.

**Dal lato dell’autore**, l’IA per la gestione dei contenuti di AEM basa la creazione dei contenuti su origini del brand approvate. L’authoring basato sull’IA, la ricerca in linguaggio naturale tra i contenuti delle pagine esistenti, i frammenti e le risorse, nonché la generazione di contenuti in base al brand consentono ai team di produrre varianti destinate a nuovi tipi di pubblico, regioni e canali senza uscire da AEM e senza discostarsi da quanto già approvato.

**Durante la fase di pubblicazione**, lo stesso contenuto viene strutturato, gestito e reso accessibile affinché l’IA possa utilizzarlo. Frammenti, metadati, tassonomie e origini approvate vengono presentati in formati che i sistemi di ricerca, gli agenti e le interfacce conversazionali possono utilizzare con sicurezza: così, quando l’IA parla a nome del brand, ne trasmette l’essenza autentica.

### Cosa significa per la clientela di AEM {#what-it-means}

I contenuti approvati sono la difesa del brand contro le allucinazioni. Quando l’IA si basa su contenuti AEM controllati, le risposte rimangono accurate, aggiornate e in linea con il brand per impostazione predefinita.
L’authoring tiene il passo con la domanda dell’era dell’IA. I team generano testi e immagini per un pubblico più ampio e per diversi contesti direttamente dall’esperienza di authoring, attingendo da origini approvate anziché partire da zero.
La ricerca funziona nel modo in cui le persone e le macchine effettivamente formulano le domande. La ricerca in linguaggio naturale e basata sull’intento tra risorse, frammenti, pagine e moduli trasforma i contenuti esistenti in una riserva riutilizzabile.
La personalizzazione si espande attraverso il riutilizzo, non la duplicazione. I componenti gestiti si ricombinano in varianti invece di moltiplicarsi in copie non tracciate.
I canali di pubblicazione ora includono superfici IA. I contenuti vengono forniti in formati che possono essere fruiti da persone, agenti ed esperienze mediate dall’IA, senza pipeline separate per ciascuno di essi.

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

Configura e gestisci le origini IA per la gestione dei contenuti per abilitare le esperienze basate sull’IA. Consulta [Verificare le origini dei contenuti](contentsources.md).

## Informazioni sulle API dell’IA per la gestione dei contenuti  {#apis}

Esplora l’ampiezza funzionale dell’IA per la gestione dei contenuti di AEM: le API mostrano tutto il potenziale della piattaforma. Consulta [API dell’IA per la gestione dei contenuti](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/).
