---
title: Panoramica di IA per la gestione dei contenuti di AEM
description: Scopri cos’è IA per l’analisi dei contenuti di AEM, perché è importante e come iniziare ad abilitarla e controllarla per il tuo ambiente AEM as a Cloud Service.
topic: Overview
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: IA per la gestione dei contenuti di AEM, panoramica, origine di contenuto, ricerca semantica, acquisizione, Cloud Manager
source-git-commit: 9b3c63be1aa95339086ee5994cd4dd7cdfa7e746
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---


# IA per la gestione dei contenuti di AEM - Introduzione

## Contenuti intelligenti, predisposizione all’intelligenza artificiale per progettazione {#ai-ready}

I clienti iniziano a incontrare i marchi tramite l’intelligenza artificiale prima di incontrare un sito web. Assistenti di chat, panoramiche dell’intelligenza artificiale, agenti, ricerca conversazionale, conferenze di intelligenza artificiale: tutti recuperano, riepilogano e rappresentano i contenuti del brand per conto del brand. Ciò che dicono è accurato, attuale e on-brand tanto quanto il contenuto che possono raggiungere.
Questo è il turno in cui IA per i contenuti di AEM è creata per. Tratta i contenuti del brand come la verità fondamentale su cui si basano le esperienze AI, e offre ai clienti di AEM gli strumenti per creare tale verità fondamentale più rapidamente dal lato dell’autore e distribuirla in modo chiaro alle esperienze basate sull’intelligenza artificiale per i consumatori dal lato della pubblicazione.

**Per quanto riguarda l&#39;autore**, AEM Content AI crea dei motivi nelle sorgenti del marchio approvate. L’authoring basato sull’intelligenza artificiale, l’individuazione del linguaggio naturale per contenuti di pagina, frammenti e risorse esistenti e la generazione basata sul riconoscimento del brand consentono ai team di produrre varianti per nuovi tipi di pubblico, aree geografiche e canali senza uscire da AEM e senza allontanarsi da ciò che è già approvato.

**Sul lato pubblicazione**, lo stesso contenuto è strutturato, gestito e indirizzabile per l&#39;IA da utilizzare. Frammenti, metadati, tassonomie e origini approvate sono esposti in forme che i sistemi di recupero, gli agenti e le interfacce conversazionali possono utilizzare con sicurezza, in modo che quando l’intelligenza artificiale parla per il brand, dica la verità del brand.

### Cosa significa per i clienti AEM {#what-it-means}

Il contenuto approvato è la difesa del marchio contro le allucinazioni. Quando l’intelligenza artificiale si basa su contenuti AEM gestiti, per impostazione predefinita le risposte rimangono precise, attuali e sul marchio.
L’authoring tiene il passo con la domanda dell’era dell’intelligenza artificiale. I team generano copie e immagini per più tipi di pubblico e momenti nell’esperienza di authoring, attingendo da origini approvate anziché lasciarle vuote.
La scoperta funziona come le persone e le macchine chiedono. La ricerca basata su intento in linguaggio naturale per risorse, frammenti, pagine e moduli trasforma il contenuto esistente in una risorsa riutilizzabile.
Personalization è scalabile tramite il riutilizzo, non la duplicazione. I componenti gestiti si ricombinano in varianti invece di moltiplicarsi in copie non tracciate.
I canali di pubblicazione ora includono superfici AI. Il contenuto viene distribuito in forme che gli esseri umani, gli agenti e le esperienze mediate dall’intelligenza artificiale possono utilizzare, senza pipeline separate per ciascuno di essi.

**Il punto principale è che il contenuto del marchio attendibile esistente è più prezioso ora di quanto non sia mai stato. Ogni frammento, risorsa e pagina approvata che già vive in AEM diventa la verità fondamentale da cui dipendono le esperienze basate sull&#39;intelligenza artificiale. L&#39;intelligenza artificiale dei contenuti di AEM è ciò che rende la libreria riutilizzabile, individuabile e pronta per il futuro.**

## Panoramica di IA per la gestione dei contenuti di AEM {#at-a-glance}

IA per la gestione dei contenuti di AEM è strutturata come uno stack a quattro livelli, ciascuno dei quali si basa su quello sottostante, dal contenuto affidabile alla base alle esperienze agentiche che potenzia in alto.

![Diagramma dello stack dell&#39;architettura di IA per la gestione dei contenuti di AEM a quattro livelli: origini di IA per la gestione dei contenuti alla base, servizi di base di IA per la gestione dei contenuti, orchestrazione dei contenuti agente e orchestrazione dell&#39;esperienza agente nella parte superiore](../assets/content-ai-four-layer-architecture-stack.png)

*Leggi lo stack dal basso verso l&#39;alto, dal contenuto attendibile alla base alle esperienze agente che gestisce nella parte superiore.*

1. Sorgenti di IA per la gestione dei contenuti
Le origini di contenuto sono entità gestite in IA per la gestione dei contenuti di AEM che si connettono a un corpo di contenuto attendibile. Un Content Source può fare riferimento a un tipo di contenuto gestito da AEM come risorse, frammenti di contenuto, pagine, moduli, metadati e tassonomie, nonché a origini non AEM come siti web di terze parti, knowledge base o portali di documentazione. Ogni Source di contenuti viene vettorizzato automaticamente e arricchito semanticamente per il recupero dell’alimentazione, la messa a terra e le esperienze di IA conversazionale. Definisci le origini di contenuto una volta e riutilizzale in tutte le API di IA per la gestione dei contenuti con aggiornamenti e aggiornamenti automatici incorporati.

1. Content AI Foundation Services
Le API e i servizi che consentono l’intelligenza semantica e l’intelligenza artificiale generativa nel contesto dei contenuti del brand. Lavorando sopra le origini di IA per la gestione dei contenuti, questi servizi permettono di recuperare, generare, modificare e ottimizzare in base al marchio, il tutto a partire dai contenuti approvati dal cliente.

1. Orchestrazione dei contenuti agente
MCP e agenti che trasformano i requisiti di contenuto basati su casi d’uso in azioni coordinate attraverso il linguaggio naturale. Questo livello consente agli autori e ad altri agenti di descrivere ciò di cui hanno bisogno in un linguaggio semplice e di disporre dei giusti servizi di base orchestrati per soddisfarli.

1. Orchestrazione esperienza agente
I casi d’uso innovativi che emergono quando i contenuti intelligenti di un brand soddisfano l’intelligenza artificiale su larga scala. Le soluzioni AEM stesse sono basate su questi servizi fondamentali e i clienti possono utilizzare le stesse API direttamente per creare le proprie esperienze agente sui propri contenuti. Dalle catene di fornitura dei contenuti basate sull’intelligenza artificiale ai percorsi di utenti conversazionali, questo livello è il punto in cui i contenuti regolamentati diventano un vantaggio competitivo.

Questi livelli sono connessi per progettazione: ogni servizio di intelligenza artificiale attinge dalla base dei contenuti e tutto ciò che è stato prodotto torna allo stesso sistema gestito, in modo che la creazione lato autore e la distribuzione lato pubblicazione condividano una sola fonte di verità.

## IA per la gestione dei contenuti di AEM in azione {#action}

Per arrivare a un’integrazione di IA per la gestione dei contenuti funzionante, sono necessarie due attività:

### &#x200B;1. Abilitare IA per la gestione dei contenuti per l’ambiente AEM {#enable}

**Prerequisito:** Prima di iniziare a utilizzare IA per la gestione dei contenuti, è necessario disporre di credenziali API con ambito nell&#39;ambiente AEM as a Cloud Service. Vedere [Configurare un progetto Adobe Developer Console](setup-adc-project.md).

### &#x200B;2. Controllare le origini di IA per la gestione dei contenuti {#control}

Imposta e gestisci le origini di IA per la gestione dei contenuti per abilitare le esperienze basate sull&#39;intelligenza artificiale. Consulta [Controllare le origini di contenuto](contentsources.md).

## Scopri le API di IA per la gestione dei contenuti  {#apis}

Esplora l’ampiezza funzionale di IA per l’analisi dei contenuti di AEM: le API mostrano tutto il potenziale della piattaforma. Consulta [API di IA per la gestione dei contenuti](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/).
