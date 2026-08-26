---
title: Introduzione alla ricerca con il servizio IA gestione contenuti di AEM
description: 'Questa guida spiega come abilitare la ricerca sul sito con il servizio IA gestione contenuti: connetti i contenuti, quindi scegli un componente di ricerca per presentarli ai visitatori.'
topic: Configuration
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: IA gestione contenuti di AEM, Ricerca con IA gestione contenuti di AEM, GenSearch, Ricerca rapida, Origini IA gestione contenuti, Acquisizione, Cloud Manager
source-git-commit: 51fa66b5ac0ef77e438db76530788826da65f91e
workflow-type: ht
source-wordcount: '1487'
ht-degree: 100%

---


# Introduzione alla ricerca con il servizio IA gestione contenuti di AEM

La ricerca tradizionale nel sito confronta le parole digitate da chi visita il sito con quelle presenti nel contenuto. Questo funziona bene se nella ricerca viene utilizzata la stessa terminologia usata nei contenuti, ma non se si fanno delle domande, si esprime un intento o semplicemente si utilizzano termini diversi. La ricerca è uno dei segnali più chiari dell’intento dei visitatori su un sito, e una ricerca che non produce alcun risultato spesso determina il fallimento di un percorso: i contenuti non vengono trovati, il coinvolgimento cala e si perdono potenziali conversioni. Sempre più spesso, le persone si aspettano che la ricerca “comprenda” ciò che intendono dire, non solo ciò che hanno digitato; è proprio questa base di comprensione dell’intento che rende possibili, in primo luogo, le risposte generative.

La ricerca tramite il serivizio IA gestione contenuti di AEM non sostituisce l’esperienza di ricerca del tuo sito, ma la fa evolvere: dalla semplice corrispondenza delle parole chiave alla comprensione del significato e dell’intento, fino a rispondere direttamente alle domande. La ricerca semantica aggiunge il recupero basato sull’intento all’esperienza di ricerca esistente, mettendo in evidenza contenuti pertinenti anche quando una query non corrisponde esattamente alla formulazione del contenuto. La ricerca generativa si basa su quella stessa struttura di recupero per produrre risposte contestualizzate e generate, fondate sui contenuti del tuo sito: si tratta di un passo in più e non corrisponde quindi al recupero semantico.

Per chi visita il tuo sito, offre maggiore pertinenza, il supporto di un linguaggio naturale, un minor numero di ricerche senza risultati e risposte più rapide. Per la tua azienda, ciò significa una migliore corrispondenza dell’intento di ricerca, una maggiore visibilità dei contenuti e una base di ricerca pronta per l’IA, senza dover ricostruire da zero la tua esperienza di ricerca. E per il tuo team si tratta di un aggiornamento graduale: il componente di ricerca esistente può passare, passo dopo passo, da funzionalità lessicali a semantiche e infine a generative, senza richiedere un’implementazione completamente nuova.

Per raggiungere questo obiettivo occorre prendere due decisioni: in che modo i contenuti vengono inseriti nell’IA per la gestione dei contenuti e quale componente li presenta ai visitatori. Collega i contenuti, quindi aggiungi un componente di ricerca a una pagina: il tuo sito sarà così pronto a fornire ai visitatori i risultati più pertinenti e le risposte basate sul loro intento.

## Prerequisiti {#prerequisites}

Prima di iniziare, verifica che siano soddisfatte le seguenti condizioni:

* Disponi di un programma Cloud Manager attivo con almeno un ambiente AEM as a Cloud Service.
* Il tuo utente è assegnato ai profili di prodotto **[!UICONTROL Utenti AEM]** (per visualizzare le origini dei contenuti) e/o **[!UICONTROL Amministratori AEM]** (per crearle e modificarle), assegnati al livello di **pubblicazione**: l’IA per la gestione dei contenuti indicizza i contenuti pubblicati, non quelli creati. Per la procedura completa, consulta [Assegnare un utente a un profilo di prodotto AEM](contentsources.md#assign-product-profile).
* È stato eseguito il provisioning del profilo di prodotto dell’ambiente in **Adobe Admin Console**.

>[!NOTE]
>
>Il solo accesso a Cloud Manager non è sufficiente. Per visualizzare o gestire le origini dei contenuti, un utente necessita anche di un profilo di prodotto AEM assegnato al livello di pubblicazione.

## Passaggio 1a: collegare un indice esistente {#option-a}

Gli indici esistenti dell’archivio vengono visualizzati automaticamente nell’elenco di origini dei contenuti come Tipo di origine AEM, in base a ciò che indicizzano, ad esempio Pagine, Risorse o Frammenti di contenuto. All’inizio sono contrassegnati come **Con limitazioni** e bloccati, e non sono ancora ricercabili tramite l’IA per la gestione dei contenuti.

1. Accedi a [Cloud Manager](https://my.cloudmanager.adobe.com/), seleziona il programma e apri la scheda **[!UICONTROL Configurazione dell’IA per la gestione dei contenuti]** per l’ambiente da configurare.
1. Trova l’origine in cui desideri eseguire la ricerca (ad esempio **Pagine**) e seleziona l’icona di blocco. Solo gli utenti con il profilo di prodotto **[!UICONTROL Amministratori AEM]** possono eseguire questa operazione; quelli con il profilo di prodotto **[!UICONTROL Utenti AEM]** possono visualizzare le origini dei contenuti, ma non modificare la loro ricercabilità.
1. Leggi attentamente la finestra di dialogo **Rendere ricercabile l’origine?** dialogo con attenzione. Si avverte che, una volta reso consultabile, gli elenchi di controllo accesso (ACL) di Apache Oak non saranno applicati a questo indice: qualsiasi utente autenticato potrà recuperare tutti i suoi contenuti. Seleziona **Comprendo che gli elenchi di controllo accesso (ACL) non saranno applicati e che tutti i contenuti di questa origine saranno ricercabili**, quindi seleziona **Rendi ricercabile**.
1. Conferma le modifiche allo stato in **Disponibile**. Accanto all’origine rimane visualizzata un’icona di avviso a ricordare in modo permanente che per quell’origine gli ACL vengono ignorati.
1. Esegui una ricerca di prova per verificare che i risultati vengano restituiti correttamente.

>[!WARNING]
>
>Rendere un indice esistente ricercabile in questo modo aggira completamente gli ACL di Apache Oak relativi a quell’origine: qualsiasi utente autenticato può recuperare tutti i suoi contenuti tramite la ricerca, indipendentemente dalle proprie normali autorizzazioni relative all’archivio. Esegui questa operazione solo per le origini che puoi rendere note integralmente.

>[!NOTE]
>
>Questo percorso è l’ideale se disponi già di un indice con i contenuti del tuo sito, ad esempio i contenuti delle pagine. Utilizza questo indice invece di impostare un meccanismo di ricerca per indicizzazione separato.

## Passaggio 1b: effettuare una ricerca per indicizzazione in un sito web {#option-b}

Utilizza questo percorso se non disponi già di un indice di ricerca per il sito. Il crawler dell’IA per la gestione dei contenuti ne crea e aggiorna uno per te. Questo processo di ricerca per indicizzazione viene definito anche **acquisizione** in Cloud Manager e in questa guida.

1. Apri la scheda **[!UICONTROL Configurazione dell’IA per la gestione dei contenuti]**, come nel passaggio 1a.
1. Seleziona **[!UICONTROL Crea origine]** e compila i campi. Solo gli utenti con il profilo di prodotto **[!UICONTROL Amministratori AEM]** possono aggiungere nuove origini dei contenuti.

   | Campo | Descrizione |
   | --- | --- |
   | **[!UICONTROL Nome della configurazione dell’IA per la gestione dei contenuti]** | Identificatore univoco per questa origine. Non modificabile dopo la creazione. |
   | **[!UICONTROL Indirizzo del sito web]** | URL principale in cui effettuare una ricerca per indicizzazione, ad esempio `https://www.example.com/`. |
   | **[!UICONTROL Escludi URL]** | *(Facoltativo)* Pattern di URL da saltare durante la scansione. |
   | **[!UICONTROL Frequenza di aggiornamento]** | Settimanale, giornaliera, 4 volte al giorno, 60 min o 15 min. |

1. Seleziona **[!UICONTROL Crea origine]**. L’acquisizione viene avviata automaticamente e l’origine viene spostata in **Indicizzazione**.
1. Monitora lo stato finché non raggiunge **Disponibile**:

   | Stato | Significato |
   | --- | --- |
   | **Nuova** | Origine appena creata; l’acquisizione automatica non è ancora iniziata. |
   | **Indicizzazione** | Ricerca per indicizzazione e indicizzazione in corso. |
   | **Disponibile** | Indicizzazione completata: pronta per elaborare le query di ricerca. |

1. Seleziona l’icona di **ricerca** accanto all’origine ed esegui una query di prova per verificare che il contenuto sia stato indicizzato correttamente.

>[!CAUTION]
>
>Origine bloccata nell’**[!UICONTROL indicizzazione]**? Riprova innanzitutto l’acquisizione dal menu (...). Se continua a non procedere, verifica che l’indirizzo del sito web sia accessibile al pubblico e che i tuoi pattern **[!UICONTROL Escludi URL]** non stiano filtrando tutte le pagine.

## Passaggio 2: scegliere un componente di ricerca {#choose-component}

Esistono due componenti in grado di inserire elementi di ricerca in una pagina, basati su fondamenti diversi:

| | Confronto tra ricerca rapida (v3) e ricerca semantica | Ricerca con l’IA per la gestione dei contenuti di AEM |
| --- | --- | --- |
| Foundation | Componente core della ricerca rapida esistente, aggiornato alla versione 3 | Nuovo componente autonomo: chiama direttamente le API dell’IA per la gestione dei contenuti |
| Origine contenuti | Contenuto del sito esistente, già in un indice, arricchito per la corrispondenza semantica | Origine dell’IA per la gestione dei contenuti (passaggio 1a o 1b) |
| Risposta generativa | No: migliora la qualità della corrispondenza solo dell’elenco dei risultati esistente | Sì: riepilogo facoltativo generato dall’IA con origini e dichiarazione di non responsabilità |
| Adattamento migliore | Siti che utilizzano già la ricerca rapida e che desiderano un aggiornamento più leggero e incrementale | Componente suggerito per l’intera gamma di funzionalità di IA per la gestione dei contenuti: ricerca semantica, ricerca generativa e ricerca nel linguaggio naturale (NLS) |

## Confronto tra ricerca rapida (v3) e ricerca semantica {#quicksearch}

Se il sito utilizza già il classico componente di ricerca rapida di [!DNL AEM], v3 introduce un pulsante di attivazione/disattivazione **Ricerca IA** che i visitatori possono attivare, senza bisogno di nuovi componenti, proxy oppure origini dei contenuti.

* La ricerca continua a essere eseguita nello stesso percorso JCR/QueryBuilder di oggi: non cambia nulla nel servlet dei risultati né nel modo in cui questi vengono sottoposti a rendering.
* Quando un visitatore abilita il pulsante di attivazione/disattivazione, il componente antepone alla query un marcatore speciale che la indirizza alla ricerca semantica anziché alla semplice ricerca full-text per parole chiave.
* Non esiste alcun riepilogo di risposte generative in questo percorso. Migliora la qualità della corrispondenza dell’elenco dei risultati esistenti, non aggiunge una risposta di IA generativa.
* **Il passaggio 1 (onboarding dell’IA per la gestione dei contenuti) non è applicabile a questo percorso.** Nessuna origine dei contenuti da creare o collegare. Questo componente esegue direttamente le query sull’indice della pagina esistente.

>[!NOTE]
>
>Se la ricerca semantica non funziona come previsto dopo l’abilitazione del pulsante di attivazione/disattivazione, crea un ticket di assistenza.

Questo percorso è adatto se desideri un aggiornamento incrementale della ricerca semantica senza adottare un nuovo componente o nuove origini dei contenuti. Se desideri un’esperienza con risposte generative, non è il percorso giusto; a tal fine, utilizza la ricerca con l’IA per la gestione dei contenuti di AEM.

## Ricerca con l’IA per la gestione dei contenuti di AEM {#gensearch}

La ricerca con l’IA per la gestione dei contenuti di AEM è un componente core di [!DNL AEM] che consente ai visitatori di cercare un’orgine dei contenuti direttamente da una pagina, con funzionalità di ricerca sia semantica sia generativa.

>[!VIDEO](https://video.tv.adobe.com/v/3497308)

>[!NOTE]
>
>Le funzionalità di ricerca generativa vengono acquistate separatamente tramite una SKU per l’IA. Contatta il tuo rappresentante del reparto vendite Adobe per abilitarle per il tuo account.

### Prerequisiti {#gensearch-prerequisites}

* Componenti core di [!DNL AEM] installati nel progetto.
* Almeno un’origine dei contenuti già creata e con stato **Disponibile**.
* Configurazione OSGi del **client dell’IA per la gestione dei contenuti di AEM** (`ContentAIClientImpl`) impostata sia per l’authoring sia per la pubblicazione, con credenziali API valide e un’origine dei contenuti predefinita.

Per la guida completa all’installazione che descrive come rendere il componente disponibile agli autori, collegare la relativa libreria client e configurare la finestra di dialogo, consulta la [documentazione sui componenti core](https://www.adobe.com/go/aem_cmp_library_it).

## Congratulazioni. {#congratulations}

Hai configurato correttamente le funzionalità di ricerca semantica e generativa.

>[!VIDEO](https://video.tv.adobe.com/v/3497306)

## Passaggi successivi {#next-steps}

* [Configurare un progetto in Adobe Developer Console](setup-adc-project.md): crea il progetto ADC e le credenziali necessarie per chiamare direttamente l’API dell’IA per la gestione dei contenuti.
* [Riferimento all’API dell’IA per la gestione dei contenuti](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/): esegui una query sul contenuto indicizzato utilizzando endpoint di ricerca semantica, generativa o ibrida.
* [Documentazione sui componenti core](https://www.adobe.com/go/aem_cmp_library_it): ulteriori informazioni sui componenti proxy e sui criteri dei modelli.
