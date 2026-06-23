---
title: Configurare un progetto Adobe Developer Console per IA per la gestione dei contenuti di AEM
description: Scopri come impostare un progetto Adobe Developer Console e autenticare le chiamate API ai servizi di IA per la gestione dei contenuti di AEM utilizzando l’autenticazione Server-to-Server o Chiave API.
topic: Configuration
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: IA per la gestione dei contenuti di AEM, Adobe Developer Console, autenticazione, server-to-server, chiave API, token di accesso
source-git-commit: 2ff1bbdd3ff224e2a6b389243c78af5fd228d5ee
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 2%

---


# Configurare un progetto Adobe Developer Console {#configure-adc-project}

Per richiamare l’API di AEM Content AI Services, è necessario disporre delle credenziali emesse da un progetto Adobe Developer Console (ADC). Questa pagina illustra come creare il progetto, selezionare un metodo di autenticazione e generare le credenziali incluse in ogni richiesta API.

Vai a [Adobe Developer Console](https://developer.adobe.com/console/) per iniziare la tua organizzazione.

## Prerequisiti {#prerequisites}

Prima di iniziare, verifica quanto segue:

* Hai accesso a [Adobe Developer Console](https://developer.adobe.com/console/) per la tua organizzazione.
* Sei stato aggiunto come **Sviluppatore** nel profilo di prodotto di AEM Content AI Services in **Adobe Admin Console**. Senza questo ruolo, la scheda API **[!UICONTROL AEM Content AI Services]** risulta disabilitata e l&#39;opzione di autenticazione **[!UICONTROL Server-to-Server]** è nascosta.
* Si conoscono i numeri del programma e dell&#39;ambiente per il profilo di prodotto che si desidera selezionare (ad esempio, `AEM User - publish - Program 12345 - Environment 67890`).
* Hai il ruolo di **[Amministratore di sistema](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-admin-console/admin-roles)** in Admin Console per il programma. Questo ruolo consente di gestire i profili di prodotto e assegnare gli utenti all’ambiente.

## Scegli un metodo di autenticazione {#choose-auth}

AEM Content AI Services supporta due metodi di autenticazione. Scegli quello che corrisponde alla tua integrazione:

| Metodo | Ideale per |
| --- | --- |
| [Server-to-Server](#s2s-auth) | Servizi di back-end che chiamano l’API senza interazione dell’utente. Restituisce un token di accesso di breve durata. |
| [Chiave API](#api-key-auth) | Integrazioni lato client o basate su browser che chiamano direttamente l’API. Restituisce una chiave di lunga durata con ambito nei domini consentiti. |

## Autenticazione server-to-server {#s2s-auth}

1. Seleziona **[!UICONTROL API e servizi]**, quindi **[!UICONTROL API]**.

   ![Developer Console con API e servizi](../assets/e2e-env-setup-28.png)

1. Filtra per **AEM Content AI Services**, quindi seleziona **[!UICONTROL Crea progetto]** per avviare un nuovo progetto oppure **[!UICONTROL Aggiungi API]** se aggiungi il servizio a un progetto esistente.

   >[!NOTE]
   >
   >Se la scheda API è disabilitata e viene visualizzato il messaggio &quot;Licenza richiesta&quot;, l’ambiente AEM as a Cloud Service potrebbe non essere modernizzato. Consulta [Modernizzazione dell&#39;ambiente AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup#modernization-of-aem-as-a-cloud-service-environment).

1. Nella finestra di dialogo **[!UICONTROL Configura API]**, selezionare **[!UICONTROL Autenticazione da server a server]**.

   ![Finestra di dialogo Configura API con selezione server-to-server](../assets/e2e-env-setup-29.png)

   >[!TIP]
   >
   >Se l’opzione Server-to-Server non è disponibile, l’utente che configura l’integrazione non viene aggiunto come Sviluppatore al profilo di prodotto. Vedere [Abilitare l&#39;autenticazione server-to-server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation).

1. Se necessario, rinominare le credenziali. Seleziona **[!UICONTROL Avanti]**.

   ![Passaggio Adobe Developer Console per rinominare le nuove credenziali server-to-server prima di selezionare Next](../assets/e2e-env-setup-30.png)

1. Seleziona l&#39;**[!UICONTROL utente AEM - pubblicazione - programma XXX - ambiente XXX]** e/o **[!UICONTROL utente AEM - autore - programma XXX - ambiente XXX]** profilo prodotto, quindi seleziona **[!UICONTROL Salva]**.

   ![Selezione profili di prodotto con i profili di pubblicazione e creazione degli utenti di AEM per il programma e l&#39;ambiente di destinazione](../assets/e2e-env-setup-31.png)

1. Controlla l’API e la configurazione dell’autenticazione.

   ![Schermata di revisione che riepiloga l&#39;API selezionata, il tipo di autenticazione e il nome delle credenziali](../assets/e2e-env-setup-33.png)

   ![Dettagli della schermata di revisione che mostrano i profili di prodotto assegnati per le credenziali](../assets/e2e-env-setup-34.png)

### Generare un token di accesso {#generate-token}

1. Nel progetto ADC, vai a **[!UICONTROL Credenziali]** e seleziona **[!UICONTROL Genera token di accesso]**.

   ![Pagina Credenziali con il pulsante Genera token di accesso evidenziato](../assets/e2e-env-setup-32.png)

1. Includi il token nell&#39;intestazione `Authorization` di ogni richiesta API:

   ```http
   Authorization: Bearer YOUR_ACCESS_TOKEN
   ```

   >[!WARNING]
   >
   >Memorizza il token in modo sicuro. Scade e deve essere rigenerato periodicamente.

## Autenticazione chiave API {#api-key-auth}

1. Quando aggiungi l&#39;API di AEM Content AI Services al progetto, seleziona **[!UICONTROL Chiave API]** nella finestra di dialogo **[!UICONTROL Seleziona tipo di autenticazione]**.

   ![Seleziona tipo di autenticazione chiave API](../assets/onboarding-api-key-01.png)

1. Conferma le credenziali della chiave API.

   ![Aggiungi credenziali chiave API](../assets/onboarding-api-key-02.png)

1. Per limitare le origini che possono utilizzare la chiave, configura i domini consentiti.

   ![Configura domini consentiti](../assets/onboarding-api-key-03.png)

1. La chiave API (ID client) viene visualizzata in **[!UICONTROL Credenziali collegate]**. Seleziona **[!UICONTROL Copia]**.

   ![Copia chiave API da credenziali connesse](../assets/onboarding-api-key-04.png)

1. Includi la chiave in ogni richiesta API:

   ```http
   x-api-key: YOUR_API_KEY
   ```

   Il progetto è ora pronto. Utilizza la chiave con ogni richiesta di AEM Content AI Services.

## Passaggi successivi {#next-steps}

* [Controlla le tue origini di contenuto](contentsources.md) - Configura un&#39;origine di contenuto in Cloud Manager e attiva l&#39;acquisizione.
* [Riferimento API di IA per la gestione dei contenuti](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/). Utilizzare il token di accesso o la chiave API per eseguire query sul contenuto indicizzato.
