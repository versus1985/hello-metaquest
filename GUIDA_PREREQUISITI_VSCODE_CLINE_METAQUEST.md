# Guida Completa Prerequisiti PC

Questa guida ti prepara un PC Windows per fare sviluppo "vibe coding" con VS Code + Cline su un progetto Unity destinato a Meta Quest.

Obiettivo pratico:
- sviluppare in Unity e VS Code con ciclo rapido;
- testare spesso in Editor;
- fare build APK Android;
- installare e avviare su Meta Quest.

---

## 1) Prerequisiti Hardware Consigliati

Minimo (funziona):
- CPU 4-6 core
- RAM 16 GB
- SSD con almeno 50 GB liberi
- GPU dedicata o integrata recente

Consigliato (fluido):
- CPU 8+ core
- RAM 32 GB
- SSD NVMe con almeno 120 GB liberi
- GPU dedicata con driver aggiornati
- Cavo USB-C dati di buona qualita (non solo ricarica)

---

## 2) Prerequisiti Software (Windows)

Obbligatori:
- Windows 10/11 aggiornato
- Unity Hub
- Unity LTS (consigliata: 2022.3 LTS)
- Moduli Unity Android:
  - Android Build Support
  - Android SDK & NDK Tools
  - OpenJDK
- Visual Studio Code
- Estensione Cline in VS Code
- Account Meta con Developer Mode abilitata

Fortemente consigliati:
- Meta Quest Developer Hub
- Git
- 7-Zip

---

## 3) Download Ufficiali

### Unity
- Unity Hub: https://unity.com/download
- Archivio versioni Unity LTS: https://unity.com/releases/editor/archive
- Unity Docs: https://docs.unity3d.com/

### XR in Unity
- XR Plug-in Management: https://docs.unity3d.com/Packages/com.unity.xr.management@latest
- OpenXR plugin Unity: https://docs.unity3d.com/Packages/com.unity.xr.openxr@latest
- XR Interaction Toolkit: https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@latest
- Input System: https://docs.unity3d.com/Packages/com.unity.inputsystem@latest

### VS Code e Cline
- Visual Studio Code: https://code.visualstudio.com/
- Marketplace Cline: https://marketplace.visualstudio.com/items?itemName=saoudrizwan.claude-dev
- Sito progetto Cline: https://cline.bot/

### Meta Quest
- Meta Quest Developer (portale): https://developers.meta.com/horizon/
- Meta Quest Developer Hub: https://developers.meta.com/horizon/develop/tools/meta-quest-developer-hub/
- Documentazione Unity per Meta: https://developers.meta.com/horizon/documentation/unity/

### Android / ADB
- Android Platform Tools (ADB): https://developer.android.com/tools/releases/platform-tools
- Android Developer Docs: https://developer.android.com/docs

### Utility
- Git: https://git-scm.com/download/win
- 7-Zip: https://www.7-zip.org/

---

## 4) Setup Operativo Completo (Step-by-step)

## Step 0 - Aggiornamento PC
1. Aggiorna Windows e riavvia.
2. Aggiorna driver GPU.
3. Verifica spazio disco libero (almeno 80-120 GB consigliati).

## Step 1 - Installa Unity Hub + Unity LTS
1. Installa Unity Hub.
2. Da Unity Hub, installa una Unity LTS (consigliata 2022.3.x).
3. Durante installazione, seleziona i moduli:
   - Android Build Support
   - Android SDK & NDK Tools
   - OpenJDK
4. Verifica in Unity Hub che l'Editor mostri i moduli Android installati.

## Step 2 - Installa VS Code + estensioni
1. Installa VS Code.
2. Installa estensioni consigliate:
   - Cline
   - C# (Microsoft)
   - Unity (Microsoft)
   - opzionali: GitLens, Error Lens
3. Accedi a GitHub in VS Code (se usi Copilot/Cline con provider compatibile).

## Step 3 - Configura Cline
1. Apri VS Code.
2. Vai su estensione Cline e scegli provider modello (es. OpenAI, Anthropic, OpenRouter, Azure OpenAI).
3. Inserisci API key/configurazione richiesta dal provider.
4. Esegui test rapido: chiedi a Cline una modifica banale su un file di testo e verifica che funzioni.

Nota: il provider dipende dal tuo account e dal tuo piano. Cline richiede un backend LLM configurato.

## Step 4 - Configura Meta Quest come dispositivo developer
1. Crea/usa account Meta developer.
2. Abilita Developer Mode sul visore (tramite app Meta Quest sul telefono).
3. Collega il Quest al PC via USB-C.
4. Sul visore, accetta prompt:
   - autorizzazione debug USB
   - trust del PC (sempre consenti)
5. Installa Meta Quest Developer Hub (consigliato) per gestione device e APK.

## Step 5 - Verifica ADB
1. Apri terminale PowerShell.
2. Esegui:

```powershell
adb devices
```

3. Se compare il seriale del Quest con stato `device`, il collegamento e OK.
4. Se compare `unauthorized`, rimetti il visore e conferma la richiesta USB debug.

Se `adb` non e riconosciuto:
- usa il path di Platform Tools Android;
- oppure aggiungi Platform Tools al PATH di sistema.

## Step 6 - Apri progetto Unity e verifica compilazione
1. Apri il progetto da Unity Hub.
2. Attendi import pacchetti.
3. Controlla la Console Unity: deve essere senza errori di compilazione C#.
4. Premi Play in Editor e verifica che la scena parta.

## Step 7 - Configurazione Android/Quest in Unity
1. File > Build Settings > Android > Switch Platform.
2. In Player Settings:
   - Package Name es. `com.example.hellometaquest`
   - Target Architectures: ARM64
   - Min API Level: almeno Android 10 (API 29) o superiore
3. In XR Plug-in Management:
   - abilita OpenXR su Android
4. In OpenXR:
   - verifica feature/profile compatibili Quest

## Step 8 - Primo build APK
1. In Build Settings, aggiungi la scena corrente in "Scenes In Build".
2. Clicca Build (o Build And Run).
3. Salva output APK in cartella dedicata, ad esempio `Builds/Android/`.
4. Verifica che la build termini senza errori.

## Step 9 - Installazione su Quest
Opzioni:
1. Build And Run da Unity.
2. Installazione da Meta Quest Developer Hub.
3. ADB manuale:

```powershell
adb install -r .\Builds\Android\hello-metaquest.apk
```

4. Avvia app dal visore e verifica la scena Hello.

---

## 5) Setup VS Code consigliato per "vibe coding"

Obiettivo: iterazioni piccole, veloci, sicure.

Configurazioni consigliate:
1. Apri workspace sulla root del progetto Unity.
2. Usa Git con commit piccoli e frequenti.
3. Chiedi a Cline modifiche incrementalissime (1 change set alla volta).
4. Dopo ogni modifica:
   - controlla Console Unity;
   - fai Play Mode;
   - solo poi procedi al passo successivo.
5. Esegui build Android periodica, non solo a fine giornata.

Prompt efficace per Cline (template):

```text
Modifica solo [file specifici].
Obiettivo: [risultato chiaro].
Vincoli: non toccare altri file, niente refactor globale.
Dopo modifica, mostrami cosa e cambiato e i rischi.
```

---

## 6) Verifiche di pronto utilizzo (Checklist)

Spunta tutti i punti:

- [ ] Unity Hub installato
- [ ] Unity LTS installata con moduli Android completi
- [ ] VS Code installato
- [ ] Cline installato e provider LLM configurato
- [ ] Quest in Developer Mode
- [ ] Debug USB autorizzato sul visore
- [ ] `adb devices` mostra il Quest
- [ ] Progetto si apre senza errori compilazione
- [ ] Play Mode funziona in Editor
- [ ] Switch Android completato
- [ ] OpenXR abilitato su Android
- [ ] APK generato con successo
- [ ] APK installato e avviato su Quest

Quando tutti i check sono verdi, il PC e pronto per sviluppo continuativo.

---

## 7) Troubleshooting rapido

### Problema: Unity non builda Android
Cause tipiche:
- modulo Android mancante
- SDK/NDK/OpenJDK non rilevati

Fix:
1. Riapri Unity Hub e verifica moduli installati.
2. In Unity: Edit > Preferences > External Tools, verifica path SDK/NDK/JDK.

### Problema: Quest non compare in ADB
Fix:
1. Cambia cavo USB-C.
2. Cambia porta USB.
3. Rimetti visore e riconferma debug USB.
4. Riavvia servizio ADB:

```powershell
adb kill-server
adb start-server
adb devices
```

### Problema: OpenXR warning/error
Fix:
1. Controlla XR Plug-in Management su Android.
2. Aggiorna pacchetti XR nel Package Manager.
3. Verifica feature abilitate in OpenXR.

### Problema: Cline non esegue bene le modifiche
Fix:
1. Riduci scope richiesta (pochi file).
2. Dai vincoli espliciti (cosa non toccare).
3. Chiedi output diff e validazione post-modifica.

---

## 8) Roadmap minima dopo setup completato

1. Hello World stabile (test Editor + Quest).
2. XR Origin + controller simulation in Editor.
3. Prima interazione (ray/select + feedback visivo).
4. Import asset 3D ottimizzati per Quest.
5. Meta XR SDK per feature native (hand tracking/passthrough).

---

## 9) Comandi utili rapidi

Verifica device:

```powershell
adb devices
```

Install APK:

```powershell
adb install -r .\Builds\Android\hello-metaquest.apk
```

Log runtime (base):

```powershell
adb logcat
```

---

## 10) Risultato Atteso

Se segui questa guida, avrai:
- PC pronto per sviluppo Unity VR;
- workflow VS Code + Cline operativo;
- pipeline build/install funzionante su Meta Quest;
- base solida per evolvere da Hello World a interazioni XR reali.
