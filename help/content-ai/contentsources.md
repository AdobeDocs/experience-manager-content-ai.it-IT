---
title: Configurare e gestire le origini di IA per la gestione dei contenuti
description: Scopri come configurare la funzione IA per la gestione dei contenuti di AEM in Cloud Manager impostando la prima origine di contenuto e attivando l’acquisizione.
topic: Configuration
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: IA per la gestione dei contenuti di AEM, origini di IA per la gestione dei contenuti, acquisizione, Cloud Manager, Adobe Developer Console
source-git-commit: 2ff1bbdd3ff224e2a6b389243c78af5fd228d5ee
workflow-type: tm+mt
source-wordcount: '1225'
ht-degree: 1%

---


# Configurare e gestire le origini di IA per la gestione dei contenuti

Questa guida illustra come configurare le origini di IA per la gestione dei contenuti in Cloud Manager, dal rispetto dei prerequisiti alla creazione di un’origine di contenuto, confermando che è indicizzata e disponibile.

## Prerequisiti {#prerequisites}

Prima di iniziare, verifichi che siano soddisfatte le seguenti condizioni:

* Hai un programma Cloud Manager attivo con almeno un ambiente AEM as a Cloud Service.
* L&#39;utente è assegnato al profilo di prodotto **Utenti AEM** per l&#39;ambiente di destinazione, che consente all&#39;utente di visualizzare le origini di contenuto.
* L&#39;utente è assegnato al profilo di prodotto **Amministratori AEM** per l&#39;ambiente di destinazione, che consente all&#39;utente di creare e modificare origini di contenuto. L&#39;accesso a Cloud Manager da solo non è sufficiente. Vedere [Assegnare un utente a un profilo di prodotto AEM](#assign-product-profile).
* È stato eseguito il provisioning del profilo di prodotto dell&#39;ambiente in **Adobe Admin Console**.

## Assegnare un utente a un profilo di prodotto AEM {#assign-product-profile}

Utilizzare questa procedura per concedere a un utente l&#39;accesso a [!DNL Adobe Experience Manager] as a Cloud Service per un ambiente specifico. Assegna il profilo corrispondente all’accesso richiesto dall’utente:

* **[!UICONTROL Utenti AEM]** - visualizza origini di contenuto.
* **[!UICONTROL Amministratori AEM]**: crea e modifica origini di contenuto.

>[!NOTE]
>
>Gli utenti devono appartenere a un profilo di prodotto AEM, ad esempio **[!UICONTROL Utenti AEM]** o **[!UICONTROL Amministratori AEM]** per accedere ad AEM. L’accesso a Cloud Manager da solo non è sufficiente.

Per assegnare questi profili, devi essere un amministratore di sistema con il profilo di prodotto Cloud Manager [!UICONTROL Proprietario business]. Assicurati che il nome e l’indirizzo e-mail dell’utente siano pronti.

1. In [Cloud Manager](https://my.cloudmanager.adobe.com/), passa al programma e seleziona **[!UICONTROL Gestisci accesso]** per l&#39;ambiente di destinazione. Viene aperta una nuova scheda [!DNL Adobe Admin Console] per tale ambiente.
1. Seleziona il profilo di prodotto **[!UICONTROL Utenti AEM]** o **[!UICONTROL Amministratori AEM]** per il livello **publish**, ad esempio `AEM Administrators - publish - Program 12345 - Environment 67890`. IA per la gestione dei contenuti indicizza i contenuti pubblicati, pertanto il profilo deve essere assegnato a livello di pubblicazione, non di authoring.
1. Selezionare **[!UICONTROL Aggiungi utente]**.
1. Inserisci il nome e l’indirizzo e-mail dell’utente, quindi salva la modifica. L’utente viene aggiunto al profilo di prodotto.

Ripeti questi passaggi per ogni ambiente a cui l’utente deve accedere, ad esempio sviluppo, staging o produzione.

>[!CAUTION]
>
>Non modificare o eliminare i profili di prodotto predefiniti denominati **[!UICONTROL Amministratori AEM]** o **[!UICONTROL Utenti AEM]**. La ridenominazione di **[!UICONTROL Amministratori AEM]** comporta la rimozione dei diritti di amministratore da tutti gli utenti a esso assegnati.

### Verifica l’assegnazione {#verify-assignment}

Per verificare che l&#39;assegnazione sia riuscita:

1. In [!DNL Admin Console], riapri il profilo di prodotto assegnato.
1. Verificare che l&#39;utente sia visualizzato nell&#39;elenco dei membri.

Se stai cercando di risolvere i problemi di accesso o token, verifica che l’utente sia aggiunto direttamente al profilo di prodotto e non solo tramite un gruppo.

## Passaggio 1: aprire la scheda di configurazione IA per la gestione dei contenuti {#open-tab}

1. Accedi a [Cloud Manager](https://my.cloudmanager.adobe.com/) e seleziona il tuo programma.

   ![Home di Cloud Manager con la scheda del programma](../assets/content-ai-onboarding-step-1.png)

1. Dalla **[!UICONTROL Panoramica del programma]**, individua la sezione **[!UICONTROL Ambienti]** e seleziona l&#39;ambiente da configurare.

   ![Panoramica del programma con un ambiente di produzione evidenziato](../assets/content-ai-onboarding-step-2.png)

1. Nella pagina dei dettagli dell&#39;ambiente selezionare la scheda **[!UICONTROL Configurazione IA per la gestione dei contenuti]**.

   ![Pagina dei dettagli dell&#39;ambiente con la scheda Configurazione di IA per la gestione dei contenuti evidenziata](../assets/content-ai-onboarding-step-3.png)

## Passaggio 2: creare un Source di IA per la gestione dei contenuti {#create-source}

Un’origine di contenuto definisce il sito web scansionato e indicizzato da IA per la gestione dei contenuti.

1. Nella scheda **[!UICONTROL Configurazione IA per la gestione dei contenuti]** selezionare **[!UICONTROL Crea Source]**.

   ![Scheda Configurazione IA per la gestione dei contenuti con il pulsante Crea Source](../assets/content-ai-onboarding-step-4.png)

1. Nella finestra di dialogo **[!UICONTROL Crea/Aggiungi nuovo Source di IA per la gestione dei contenuti]**, compila i campi:

   | Campo | Descrizione |
   | --- | --- |
   | **[!UICONTROL Nome configurazione IA per la gestione dei contenuti]** | Un identificatore univoco per questa origine (ad esempio, `my-site-index`). Non può essere modificato dopo la creazione. |
   | **[!UICONTROL Descrizione]** | *(Facoltativo)* Breve descrizione dell&#39;origine di contenuto. |
   | **[!UICONTROL Indirizzo sito Web]** | URL principale del sito Web da scansionare (ad esempio, `https://www.example.com/`). |
   | **[!UICONTROL Escludi URL]** | *(Facoltativo)* pattern di URL da saltare durante la scansiona. |
   | **[!UICONTROL Frequenza di aggiornamento]** | Con quale frequenza la funzione IA per l’analisi dei contenuti scansiona nuovamente la sorgente: settimanale, giornaliera, giornaliera 4×, 60 min o 15 min. |

   ![Finestra di dialogo Crea Source di IA per la gestione dei contenuti con i campi Nome e Indirizzo sito Web compilati ed evidenziato il pulsante Crea Source](../assets/content-ai-onboarding-step-5-0.png)

   ![Elenco a discesa della frequenza di aggiornamento con le opzioni disponibili](../assets/content-ai-onboarding-step-5-1.png)

1. Selezionare **[!UICONTROL Crea Source]**.

## Passaggio 3: attivare l’acquisizione {#trigger-acquisition}

Dopo la creazione dell&#39;origine, lo stato è **Nuovo**. Esegui un&#39;acquisizione iniziale per avviare l&#39;indicizzazione.

1. Nell&#39;elenco di origine, seleziona l&#39;icona **altre azioni** (...) accanto all&#39;origine, quindi seleziona **[!UICONTROL Attiva acquisizione]**.

   ![Elenco origini IA per la gestione dei contenuti con il menu altre azioni aperto ed Attivazione acquisizione evidenziata](../assets/content-ai-onboarding-step-7.png)

1. Nella finestra di dialogo **[!UICONTROL Trigger acquisizione]**, controlla i dettagli dell&#39;origine - **[!UICONTROL Origine contenuto]**, **[!UICONTROL Ultima esecuzione]** e **[!UICONTROL Prossima esecuzione pianificata]** - e seleziona **[!UICONTROL Trigger]**.

   ![Finestra di dialogo di conferma dell&#39;acquisizione del trigger](../assets/content-ai-onboarding-step-8.png)

## Passaggio 4: monitorare lo stato dell’indicizzazione {#monitor-status}

Dopo l’avvio dell’acquisizione, lo stato dell’origine viene aggiornato in tempo reale.

| Stato | Significato |
| --- | --- |
| **Nuovo** | Source creato; non è ancora stata eseguita alcuna acquisizione. |
| **Indicizzazione** | Acquisizione in corso; il contenuto viene scansionato e indicizzato. |
| **Disponibile** | Indicizzazione completata. L’origine è pronta per elaborare le query di ricerca. |

![Elenco origini contenuto con stato indicizzazione](../assets/content-ai-onboarding-step-9.png)

![Elenco origini contenuto con stato Disponibile](../assets/content-ai-onboarding-step-10.png)

Attendi che lo stato raggiunga **Disponibile** prima di cercare nell&#39;indice o testare l&#39;API.

## Passaggio 5: cercare contenuti indicizzati {#search-content}

Una volta che lo stato dell&#39;origine è **Disponibile**, è possibile eseguire query di ricerca direttamente da Cloud Manager per verificare che il contenuto sia stato indicizzato correttamente.

1. Nell&#39;elenco delle origini, seleziona **[!UICONTROL Cerca]** accanto all&#39;origine.

   ![Elenco origini di contenuto con il pulsante Cerca evidenziato in un&#39;origine disponibile](../assets/content-ai-onboarding-step-13.png)

1. Immettere una query nel campo di ricerca. I risultati mostrano un elenco di elementi corrispondenti con un punteggio di corrispondenza e un tipo di contenuto (ad esempio, **PAGINA** o **PDF**). Selezionando un risultato si apre un&#39;anteprima a destra.

   ![Pannello di ricerca con una query, risultati corrispondenti con punteggi corrispondenti e un riquadro di anteprima per il primo risultato](../assets/content-ai-onboarding-step-14.png)

## Modificare o eliminare un Source {#modify-source}

Per aggiornare una configurazione di origine dopo che è stata creata:

1. Nell&#39;elenco di origine, selezionare l&#39;icona **altre azioni** (...) accanto all&#39;origine, quindi selezionare **[!UICONTROL Modifica]**.

   ![Elenco origini di contenuto con il menu altre azioni aperto e Modifica evidenziato](../assets/content-ai-onboarding-step-11.png)

1. Nella finestra di dialogo **[!UICONTROL Modifica Source di IA per la gestione dei contenuti]**, aggiorna **[!UICONTROL Descrizione]**, **[!UICONTROL Indirizzo sito Web]**, **[!UICONTROL Escludi URL]** o **[!UICONTROL Frequenza di aggiornamento]** in base alle esigenze. Il nome di configurazione di **[!UICONTROL IA per la gestione dei contenuti]** è di sola lettura e non può essere modificato.

1. Seleziona **[!UICONTROL Salva]** per applicare le modifiche, oppure seleziona **[!UICONTROL Elimina]** nella parte inferiore sinistra della finestra di dialogo per rimuovere completamente l&#39;origine.

   >[!WARNING]
   >
   >L’eliminazione di un’origine è permanente. Tutto il contenuto indicizzato per tale origine viene rimosso e non può più essere utilizzato per le query di ricerca.

   ![Finestra di dialogo Modifica Source di IA per la gestione dei contenuti con i campi modificabili evidenziati e un pulsante Elimina in basso a sinistra](../assets/content-ai-onboarding-step-12.png)

L’elenco delle sorgenti viene aggiornato in base alle modifiche apportate. Se hai eliminato l’origine, questa non viene più visualizzata nell’elenco.

## Passaggi successivi {#next-steps}

* [Configura un progetto Adobe Developer Console](setup-adc-project.md) - Crea il progetto ADC e le credenziali necessarie per chiamare l&#39;API.
* [Riferimento API IA per la gestione dei contenuti](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/) - Eseguire una query sul contenuto indicizzato utilizzando endpoint di ricerca semantici, full-text o ibridi.

## Risoluzione di problemi {#troubleshooting}

* **Source rimane in [!UICONTROL Indicizzazione] per un periodo prolungato.** Riprova l’acquisizione dal menu (...). Se lo stato non avanza dopo una seconda esecuzione, verifica che l&#39;**[!UICONTROL indirizzo del sito Web]** sia raggiungibile pubblicamente e che i **[!UICONTROL modelli Escludi URL]** non filtrino ogni pagina.
* **Source torna a [!UICONTROL New] dopo un&#39;esecuzione.** Il crawler non è riuscito a recuperare alcuna pagina dall&#39;URL principale configurato. Verificare che l&#39;URL risponda con `200 OK` e che il sito non stia bloccando le richieste automatizzate.
* **[!UICONTROL La ricerca] non restituisce alcun risultato per un&#39;origine [!UICONTROL Disponibile].** Indicizzazione riuscita, ma nessun contenuto corrisponde alla query. Prova con una query più ampia o controlla che gli URL scansionati includano le pagine previste.
