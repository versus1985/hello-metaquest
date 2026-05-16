# Prompt pulito — contesto e istruzioni per ripartire da zero

Voglio ripartire da zero su un nuovo PC con lo sviluppo di una prima applicazione per **Meta Quest**.

## Contesto

Sono il possessore di un visore Meta Quest e voglio iniziare a sviluppare applicazioni che girino sul visore.

L'obiettivo iniziale non è creare subito un'app complessa, ma costruire una prima **Hello World VR** per validare tutto il flusso di lavoro:

1. setup dell'ambiente di sviluppo;
2. creazione del progetto;
3. test locale senza visore, quando possibile;
4. build Android/Quest;
5. installazione e avvio sul Meta Quest.

Questa prima app deve essere semplice, ma la scelta tecnologica deve permettere di crescere in futuro verso applicazioni più complesse con:

- scene 3D;
- asset importati o creati con Blender;
- interazioni con controller;
- UI spaziale;
- fisica;
- hand tracking;
- eventualmente passthrough / mixed reality;
- deploy nativo sul visore.

## Scelta tecnologica desiderata

La scelta consigliata è:

- **Unity LTS** come motore principale;
- **OpenXR** come base XR standard;
- **XR Plug-in Management** per configurare XR in Unity;
- **XR Interaction Toolkit** per interazioni e simulazione in editor;
- **Input System** di Unity;
- **Android Build Support** per generare APK installabili sul Quest;
- **Meta XR SDK** come step successivo per funzionalità specifiche Meta Quest.

Per il primo progetto non voglio introdurre complessità inutile: la Hello World deve funzionare anche senza dipendere obbligatoriamente dal Meta XR SDK. Il Meta XR SDK potrà essere aggiunto in seguito per feature più native come hand tracking, passthrough e building blocks Meta.

## Perché Unity invece di WebXR

WebXR è interessante per prototipi rapidi nel browser del Quest, ma in questo caso voglio costruire una base che possa scalare verso app native più strutturate.

Unity è preferibile perché offre:

- migliore gestione di scene 3D complesse;
- pipeline matura per asset 3D;
- buon supporto per controller e input XR;
- possibilità di build nativa Android/Quest;
- integrazione futura con Meta XR SDK;
- strumenti di profiling e ottimizzazione;
- ecosistema più ampio per VR standalone.

## Obiettivo della prima applicazione

Creare una prima app Unity chiamata indicativamente:

```text
hello-metaquest
```

La prima versione deve mostrare una scena minimale con:

- camera/player iniziale;
- pavimento o ambiente base;
- luce direzionale;
- testo 3D `Hello Meta Quest` davanti all'utente;
- eventuale piccola animazione del testo, per confermare che la scena stia girando;
- configurazione pronta per build Android/Quest.

## Requisiti del progetto

Il progetto deve essere:

- semplice da aprire con Unity Hub;
- compatibile con Unity LTS, preferibilmente Unity 2022.3 LTS o versione LTS equivalente;
- testabile in Unity Editor anche senza Quest collegato;
- pronto per essere convertito/buildato su piattaforma Android;
- documentato con istruzioni chiare per setup, test e deploy;
- pensato come base incrementale per aggiungere controller, XR Origin, ray interaction e asset 3D.

## Prerequisiti da considerare

Sul nuovo PC serviranno:

1. **Unity Hub**;
2. **Unity LTS**, preferibilmente 2022.3 LTS;
3. moduli Unity:
   - Android Build Support;
   - Android SDK & NDK Tools;
   - OpenJDK;
4. account Meta configurato come sviluppatore;
5. Developer Mode attiva sul Meta Quest;
6. cavo USB-C per il primo deploy;
7. opzionale ma consigliato: **Meta Quest Developer Hub** per installazione APK, gestione dispositivo e log;
8. opzionale in futuro: **Blender** per modellazione/import asset 3D.

## Debug e test senza Quest

Voglio poter testare il più possibile anche senza avere il Quest collegato.

Nel primo step deve essere possibile usare:

- Unity Play Mode;
- camera standard o XR-simulated setup;
- logica C#;
- scena 3D;
- posizionamento oggetti;
- luci/materiali;
- UI o testo world-space.

È chiaro che senza visore non potrò validare completamente:

- performance reali sul Quest;
- frame rate reale;
- scala percepita in VR;
- comfort;
- tracking reale di testa/controller/mani;
- passthrough;
- permessi e comportamento Android reale;
- resa nelle lenti;
- installazione APK sul dispositivo.

Il workflow desiderato è quindi:

1. sviluppare e testare spesso in Unity Editor;
2. fare build Android quando il progetto compila;
3. testare periodicamente sul Quest fisico.

## Build e deploy desiderati

La procedura finale deve permettere di:

1. aprire il progetto in Unity;
2. generare o aprire la scena Hello World;
3. testare in Play Mode;
4. passare piattaforma a Android;
5. abilitare OpenXR per Android;
6. configurare Player Settings per Quest;
7. generare un APK;
8. installare l'APK sul Quest tramite:
   - Build And Run da Unity;
   - oppure Meta Quest Developer Hub;
   - oppure ADB, se necessario.

## Impostazioni Android/Quest da prevedere

Nel progetto bisognerà prevedere o documentare:

- package name, ad esempio `com.example.hellometaquest`;
- target architecture: **ARM64**;
- minimum API level compatibile con Quest, ad esempio Android 10/API 29 o superiore;
- OpenXR abilitato per Android;
- eventuali profili/controller Meta Quest in OpenXR;
- build development opzionale per debug;
- uso di logcat o Meta Quest Developer Hub per leggere i log.

## Roadmap dopo la Hello World

Dopo la prima Hello World, voglio procedere per step:

### Step 1 — Hello World e primo deploy

- scena minimale;
- testo 3D;
- test in editor;
- build APK;
- installazione sul Quest.

### Step 2 — Base XR più reale

- aggiunta di XR Origin;
- setup camera rig XR;
- controller tracking;
- simulazione input in editor.

### Step 3 — Prima interazione

- oggetto 3D cliccabile;
- ray interaction;
- cambio colore o posizione quando selezionato;
- feedback visivo/audio.

### Step 4 — Asset 3D

- import di modelli `.fbx` o `.glb`;
- workflow con Blender;
- materiali e luci;
- ottimizzazione per Quest.

### Step 5 — Funzionalità Quest native

- integrazione Meta XR SDK;
- hand tracking;
- passthrough/mixed reality;
- performance profiling;
- packaging più serio.

## Criteri di successo della prima fase

La prima fase è completata quando:

- il progetto si apre correttamente in Unity;
- non ci sono errori nella Console;
- la scena Hello World parte in Play Mode;
- il testo `Hello Meta Quest` è visibile davanti all'utente;
- il progetto può essere switchato a piattaforma Android;
- Unity riesce a generare un APK;
- l'APK può essere installato e avviato sul Meta Quest.

## Vincoli

- Mantieni la prima versione molto semplice.
- Evita dipendenze non necessarie nella Hello World iniziale.
- Non partire da WebXR: usare Unity come base principale.
- Scrivere documentazione chiara.
- Rendere il progetto testabile localmente anche senza visore.
- Preparare il progetto in modo incrementale, così da poter aggiungere XR Origin, controller e asset 3D nei passaggi successivi.

## Richiesta operativa

Partendo da questo contesto, aiutami a ricreare da zero il progetto `hello-metaquest`.

Prima proponi un piano sintetico di implementazione, poi procedi a generare i file necessari per una prima Hello World Unity apribile da Unity Hub e testabile in locale.
