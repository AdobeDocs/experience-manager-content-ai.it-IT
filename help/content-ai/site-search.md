---
title: Introduzione alla Ricerca IA dei contenuti di AEM
description: 'Questa guida spiega come abilitare la ricerca sul sito con IA per la gestione dei contenuti: collega i contenuti, quindi scegli un componente di ricerca per presentarli ai visitatori.'
topic: Configuration
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: IA per la gestione dei contenuti di AEM, Ricerca IA dei contenuti di AEM, GenSearch, Ricerca rapida, origini di IA per la gestione dei contenuti, Acquisizione, Cloud Manager
source-git-commit: 51fa66b5ac0ef77e438db76530788826da65f91e
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 6%

---


# Introduzione alla Ricerca IA dei contenuti di AEM

La ricerca tradizionale nel sito confronta le parole digitate da un visitatore con quelle presenti nel contenuto. Questo funziona bene quando i visitatori utilizzano la stessa terminologia utilizzata dai contenuti, ma si rompe nel momento in cui pongono una domanda, esprimono un intento o semplicemente formulano le cose in modo diverso. La ricerca è uno dei segnali più chiari di intento dei visitatori su un sito, quindi una corrispondenza fallita spesso significa un percorso fallito: il contenuto non viene scoperto, il coinvolgimento scende e le conversioni vanno perse. I visitatori si aspettano sempre di più che la ricerca comprenda il loro significato, non solo quello che hanno digitato, ma che la stessa base consapevole dell’intento sia ciò che rende possibili le risposte generative.

La Ricerca IA dei contenuti di AEM non sostituisce l’esperienza di ricerca del sito, ma lo evolve, dalle parole chiave corrispondenti, alla comprensione del significato e delle intenzioni, alle risposte dirette alle domande. La ricerca semantica aggiunge il recupero in base all’intento all’esperienza di ricerca esistente, evidenziando contenuti rilevanti anche quando una query non condivide la formulazione esatta del contenuto. La ricerca generativa si basa sullo stesso fondamento di recupero per produrre risposte contestuali e generate basate sul contenuto del sito: un passaggio distinto, non lo stesso del recupero semantico.

Per i visitatori, questo significa maggiore rilevanza, supporto del linguaggio naturale, meno ricerche a risultato zero e risposte più veloci. Per la tua azienda, significa una migliore corrispondenza degli intenti, un’individuazione dei contenuti più efficace e una base di ricerca pronta per l’intelligenza artificiale, senza dover ricreare da zero la tua esperienza di ricerca. Per il tuo team si tratta di un aggiornamento incrementale: il componente di ricerca esistente può passare gradualmente da funzionalità lessicali, semantiche a generative, anziché richiedere un’implementazione completamente nuova.

Per arrivare a questo si devono prendere due decisioni: come il contenuto entra in IA per la gestione dei contenuti e quale componente lo porta ai visitatori. Connetti il contenuto, quindi aggiungi un componente di ricerca a una pagina: il sito è pronto per fornire ai visitatori i risultati più rilevanti e le risposte basate sulle finalità.

## Prerequisiti {#prerequisites}

Prima di iniziare, verifica che siano soddisfatte le seguenti condizioni:

* Disponi di un programma Cloud Manager attivo con almeno un ambiente AEM as a Cloud Service.
* Il tuo utente è assegnato al profilo di prodotto **[!UICONTROL Utenti AEM]** (per visualizzare le origini di contenuto) e/o **[!UICONTROL Amministratori AEM]** (per crearli e modificarli), assegnati al livello **pubblica** - Indici IA per la gestione dei contenuti pubblicati, non contenuti creati. Consulta [Assegnare un utente a un profilo di prodotto AEM](contentsources.md#assign-product-profile) per la procedura completa.
* Il provisioning del profilo di prodotto dell&#39;ambiente è stato eseguito in **Adobe Admin Console**.

>[!NOTE]
>
>Il solo accesso a Cloud Manager non è sufficiente. Per visualizzare o gestire le origini di contenuto, l’utente necessita anche di un profilo di prodotto AEM assegnato al livello di pubblicazione.

## Passaggio 1a - Collegare un indice esistente {#option-a}

Gli indici esistenti dell’archivio vengono visualizzati automaticamente nell’elenco Origini contenuto come AEM di tipo Source, come mostrato dagli indici, ad esempio Pagine, Assets o Frammenti di contenuto. Hanno inizio con **Limitato** e sono bloccati, non ancora ricercabili tramite IA per la gestione dei contenuti.

1. Accedi a [Cloud Manager](https://my.cloudmanager.adobe.com/), seleziona il programma e apri la scheda **[!UICONTROL Configurazione di IA per la gestione dei contenuti]** per l&#39;ambiente da configurare.
1. Trova l&#39;origine in base alla quale desideri eseguire la ricerca (ad esempio, **Pagine**) e seleziona l&#39;icona a forma di lucchetto. Solo gli utenti con il profilo di prodotto **[!UICONTROL Amministratori AEM]** possono eseguire questa operazione - **[!UICONTROL Utenti AEM]** possono visualizzare le origini di contenuto, non modificare la loro ricercabilità.
1. Leggere **Rendere ricercabile l&#39;origine?** dialogare con attenzione. Avvisa che gli elenchi di controllo di accesso (ACL) di Apache Oak non verranno applicati per questo indice una volta che sarà possibile eseguire la ricerca: qualsiasi utente autenticato sarà in grado di recuperare tutto il suo contenuto. Verifica **Sono consapevole che i controlli di accesso (ACL) non sono applicati e che tutto il contenuto dell&#39;origine sarà ricercabile**, quindi seleziona **Rendi ricercabile**.
1. Conferma le modifiche di stato in **Disponibile**. Accanto all’origine viene mantenuta un’icona di avviso per ricordare in modo permanente che per essa vengono ignorati gli ACL.
1. Esegui una ricerca di test per verificare che i risultati vengano restituiti correttamente.

>[!WARNING]
>
>Rendendo possibile la ricerca di un indice esistente in questo modo si ignorano completamente gli ACL Apache Oak per tale origine: qualsiasi utente autenticato può recuperare tutto il suo contenuto tramite la ricerca, indipendentemente dalle sue normali autorizzazioni nell’archivio. Eseguire questa operazione solo per le fonti che si è a proprio agio a esporre completamente.

>[!NOTE]
>
>Questo percorso è adatto se disponi già di un indice con il contenuto del sito, ad esempio il contenuto della pagina. Utilizza tale indice invece di impostare un meccanismo di scansiona separato.

## Passaggio 1b - Scansionare un sito web {#option-b}

Usa questo percorso se non disponi già di un indice di ricerca per il sito. Il crawler di IA per la gestione dei contenuti ne crea e aggiorna uno per te. Questo scansiono viene definito anche **acquisizione** in Cloud Manager e in questa guida.

1. Aprire la scheda **[!UICONTROL Configurazione IA per la gestione dei contenuti]**, come nel passaggio 1a.
1. Seleziona **[!UICONTROL Crea Source]** e compila i campi. Solo gli utenti con il profilo di prodotto **[!UICONTROL Amministratori AEM]** possono aggiungere nuove origini di contenuto.

   | Campo | Descrizione |
   | --- | --- |
   | **[!UICONTROL Nome della configurazione dell’IA per la gestione dei contenuti]** | Un identificatore univoco per questa origine. Non modificabile dopo la creazione. |
   | **[!UICONTROL Indirizzo del sito web]** | URL principale da scansionare, ad esempio `https://www.example.com/`. |
   | **[!UICONTROL Escludi URL]** | *(Facoltativo)* Pattern di URL da saltare durante la scansione. |
   | **[!UICONTROL Frequenza di aggiornamento]** | Settimanale, Giornaliero, Giornaliero 4×, 60 Min o 15 Min. |

1. Seleziona **[!UICONTROL Crea origine]**. L’acquisizione viene avviata automaticamente e l’origine viene spostata in **Indicizzazione**.
1. Monitora lo stato fino a raggiungere **Disponibile**:

   | Stato | Significato |
   | --- | --- |
   | **Nuova** | Source è appena stato creato; l&#39;acquisizione automatica non è ancora iniziata. |
   | **Indicizzazione** | Scansiona e indicizzazione in corso. |
   | **Disponibile** | Indicizzazione completata: pronta per distribuire le query di ricerca. |

1. Seleziona l&#39;icona **cerca** accanto all&#39;origine ed esegui una query di test per verificare che il contenuto sia stato indicizzato correttamente.

>[!CAUTION]
>
>Origine bloccata in **[!UICONTROL Indicizzazione]**? Riprova l&#39;acquisizione dal menu (...). Se ancora non avanza, verifica che l&#39;indirizzo del sito Web sia raggiungibile pubblicamente e che i tuoi **[!UICONTROL modelli di esclusione URL]** non filtrino ogni pagina.

## Passaggio 2: scegliere un componente di ricerca {#choose-component}

Esistono due componenti che possono inserire la ricerca in una pagina, basati su basi diverse:

| | Ricerca rapida (v3) con ricerca semantica | Ricerca IA contenuto AEM |
| --- | --- | --- |
| Foundation | Componente core Ricerca rapida esistente, aggiornato alla versione 3 | Nuovo componente autonomo: chiama direttamente le API di IA per la gestione dei contenuti |
| Origine contenuto | Il contenuto del sito esistente, già in un indice, arricchito per la corrispondenza semantica | Un Source di IA per la gestione dei contenuti (passaggio 1a o 1b) |
| Risposta generativa | No: migliora la qualità della corrispondenza solo dell’elenco dei risultati esistente | Sì - riepilogo facoltativo generato dall’intelligenza artificiale con origini e una liberatoria |
| Adatta | Siti che utilizzano già la Ricerca rapida e che desiderano un aggiornamento più leggero e incrementale | Il componente suggerito per l’intera gamma di funzionalità di IA per la gestione dei contenuti: ricerca semantica, ricerca generativa e ricerca nel linguaggio naturale (NLS) |

## Ricerca rapida (v3) con ricerca semantica {#quicksearch}

Se il sito utilizza già il componente di ricerca rapida [!DNL AEM] classico, v3 aggiunge un consenso **Ricerca IA** per attivare i visitatori. Non è necessario alcun nuovo componente, proxy o Source dei contenuti.

* La ricerca continua a essere eseguita nello stesso percorso JCR/QueryBuilder di oggi, senza apportare alcuna modifica al servlet dei risultati o al rendering dei risultati.
* Quando un visitatore abilita l’interruttore, il componente aggiunge alla query un prefisso con un marcatore speciale che la indirizza alla corrispondenza semantica invece che al testo normale.
* Non esiste alcun riepilogo di risposta generativa su questo percorso. Migliora la qualità della corrispondenza dell’elenco dei risultati esistenti, non aggiunge una risposta generativa di IA.
* **Il passaggio 1 (onboarding di IA per la gestione dei contenuti) non è applicabile a questo percorso.** Nessun Source di contenuto da creare o connettere. Questo componente esegue direttamente le query sull’indice della pagina esistente.

>[!NOTE]
>
>Se la ricerca semantica non funziona come previsto dopo l’attivazione dell’interruttore, genera un ticket di supporto.

Questo percorso è adatto se desideri un aggiornamento incrementale della ricerca semantica senza adottare un nuovo componente o Origini di contenuto. Se desideri un’esperienza a risposta generativa, non è il percorso giusto; a tale scopo utilizza la Ricerca IA Contenuto di AEM.

## Ricerca IA contenuto AEM {#gensearch}

AEM Content Ricerca IA è un componente di base [!DNL AEM] che consente ai visitatori di cercare un Source di contenuti direttamente da una pagina, con funzionalità di ricerca sia semantica che generativa.

>[!VIDEO](https://video.tv.adobe.com/v/3497308)

>[!NOTE]
>
>Le funzionalità di ricerca generativa vengono acquistate separatamente tramite una SKU di intelligenza artificiale. Contatta il tuo rappresentante commerciale Adobe per abilitarlo per il tuo account.

### Prerequisiti {#gensearch-prerequisites}

* Componenti core [!DNL AEM] installati nel progetto.
* Almeno un Source dei contenuti è già stato creato e si trova nello stato **Disponibile**.
* Configurazione OSGi del client **AEM Content AI** (`ContentAIClientImpl`) impostata sia per l&#39;authoring che per la pubblicazione, con credenziali API valide e un Source dei contenuti predefinito.

Per la guida completa alla configurazione, che descrive come rendere il componente disponibile agli autori, come effettuare il cablaggio della libreria client e come configurare la finestra di dialogo, consulta la [documentazione dei Componenti core](https://www.adobe.com/go/aem_cmp_library_it).

## Congratulazioni. {#congratulations}

Le funzionalità di ricerca semantica e generativa sono state configurate.

>[!VIDEO](https://video.tv.adobe.com/v/3497306)

## Passaggi successivi {#next-steps}

* [Configura un progetto Adobe Developer Console](setup-adc-project.md) - Crea il progetto ADC e le credenziali necessarie per chiamare direttamente l&#39;API di IA per la gestione dei contenuti.
* [Riferimento API IA per la gestione dei contenuti](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/) - Eseguire una query sul contenuto indicizzato utilizzando endpoint di ricerca semantici, generativi o ibridi.
* [Documentazione dei Componenti core](https://www.adobe.com/go/aem_cmp_library_it) - Ulteriori informazioni sui componenti proxy e sui criteri dei modelli.
