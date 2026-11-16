# MONOPOLICSYNTH - KORG DRUMLOGUE

**FREE - MONOPOLICSYNTH - KORG DRUMLOGUE**  
**Monopolic - Korg drumlogue**

![Version](https://shields.io)
![Author](https://shields.io)
![Platform](https://shields.io)
![Built with](https://shields.io)

**MONOPOLIC** è un sintetizzatore utente per **Korg drumlogue** creato da **CrystalMatrix (aka Paquini Balandra)**, ispirato alla classica architettura a 4 oscillatori del leggendario sintetizzatore analogico **Korg Mono/Poly (1981)**.

Sviluppato visivamente in **Plugdata** con la libreria **Heavylib** e compilato in C++ nativo tramite **hvcc (Heavy Compiler Collection)**, Monopolic porta la versatilità dei 4 VCO con modulazione incrociata (FM), modulazione di larghezza d'impulso (PWM) e filtro risonante direttamente sulla traccia **USER** del drumlogue.

---

## 🎛️ Caratteristiche Principali

* **Architettura a 4 Oscillatori (`OSC 1` - `OSC 4`):**
  * Fedele allo spirito del Mono/Poly originale, dispone di 4 oscillatori indipendenti con forme d'onda selezionabili (*Off, Sinusoide, Triangolare, Dente di sega e Impulso*) generate con anti-aliasing **PolyBLEP**.
  * Intonazione individuale in un intervallo di **±3 ottave (`-36` a `+36` semitoni)** con leggere scordature analogiche interne (*detune* fisso su OSC 2, 3 e 4) per ottenere bassi potenti, lead corposi e sonorità in stile *unison*.
* **Sezione di Modulazione (`FM & PWM`):**
  * Oscillatore modulatore dedicato (`FMWAVE`, `FMFREQ`, `FMDEPTH`, `FMGAIN`) per creare timbri metallici, suoni percussivi ed effetti di modulazione incrociata.
  * Modulazione di larghezza d'impulso (`PWM`) regolabile in tempo reale.
* **Filtro Passa-Basso Risonante (circa 24 dB/oct):**
  * Doppio stadio di filtri `vcf~` in serie con controllo della frequenza di taglio (`CUTOFF` da 20 Hz a 16 kHz), risonanza (`RES0`) e inviluppo dedicato (`F.ENV`).
* **Inviluppi Dinamici (`SELADSRS`):**
  * Un unico blocco di 4 controlli (`ATTACK`, `DECAY`, `SUSTAIN`, `RELEASE`) che permette di modificare sia l'inviluppo di ampiezza (VCA) sia quello del filtro (VCF) tramite un selettore, evitando di affollare le pagine del menu.
* **Matrice di Routing Intelligente (`MACROSEL`):**
  * Sistema di controllo centralizzato tramite una manopola master (`MACRO`) e un selettore a 22 posizioni (`MACROSEL`) per dosare i livelli individuali di ciascun oscillatore e le relative mandate di modulazione.

---

## 🎚️ Mappatura dei Parametri (`@hv_param`)

Monopolic mette a disposizione **23 parametri** organizzati sullo schermo OLED del Korg drumlogue:

### Filtro e Controllo Macro

| # | Nome a Schermo | Intervallo | Funzione |
| :--- | :--- | :--- | :--- |
| **1** | `CUTOFF` | `0.0 - 1.0` | Frequenza di taglio del filtro passa-basso (curva esponenziale). |
| **2** | `RES0` | `0.0 - 1.0` | Risonanza del doppio filtro `vcf~`. |
| **3** | `F.ENV` | `0.0 - 1.0` | Quantità di modulazione dell'inviluppo sul taglio del filtro. |
| **4** | `MACRO` | `0.0 - 1.0` | Regola il livello o l'intensità della destinazione selezionata in `MACROSEL`. |
| **5** | `MACROSEL` | `0 - 21` | Seleziona il parametro interno controllato dalla manopola `MACRO` *(vedi tabella sotto)*. |
| **6** | `FMWAVE` | `0 - 5` | Seleziona la forma d'onda dell'oscillatore modulatore FM. |

### Inviluppi (ADSR)

| # | Nome a Schermo | Intervallo | Funzione |
| :--- | :--- | :--- | :--- |
| **7** | `SELADSRS` | `0 - 3` | Seleziona quale inviluppo viene modificato dai controlli da 8 a 11 *(vedi tabella sotto)*. |
| **8** | `ATTACK` | `0.1 - 1.0` | Tempo di attacco (Attack). |
| **9** | `DECAY` | `0.1 - 1.0` | Tempo di decadimento (Decay). |
| **10** | `SUSTAIN` | `0.1 - 1.0` | Livello di sostegno (Sustain). |
| **11** | `RELEASE` | `0.1 - 1.0` | Tempo di rilascio al termine della nota (Release). |

### Oscillatori e Sintesi FM/PWM

| # | Nome a Schermo | Intervallo | Funzione |
| :--- | :--- | :--- | :--- |
| **12** | `WF1` | `0 - 5` | Forma d'onda dell'Oscillatore 1 (`0=Off, 1=Sine, 2=Tri, 3=Saw, 4=Pulse`). |
| **13** | `WF2` | `0 - 5` | Forma d'onda dell'Oscillatore 2. |
| **14** | `WVFORM3` | `0 - 5` | Forma d'onda dell'Oscillatore 3. |
| **15** | `WVFORM4` | `0 - 5` | Forma d'onda dell'Oscillatore 4. |
| **16** | `OCT1` | `-36 a +36` | Intonazione in semitoni dell'Oscillatore 1. |
| **17** | `OCT2` | `-36 a +36` | Intonazione in semitoni dell'Oscillatore 2 *(+0,15 semitoni di detune fisso)*. |
| **18** | `OCTAVE3` | `-36 a +36` | Intonazione in semitoni dell'Oscillatore 3 *(-0,12 semitoni di detune fisso)*. |
| **19** | `OCTAVE4` | `-36 a +36` | Intonazione in semitoni dell'Oscillatore 4 *(+0,22 semitoni di detune fisso)*. |
| **20** | `FMFREQ` | `0.0 - 1.0` | Frequenza dell'oscillatore modulatore FM. |
| **21** | `FMDEPTH` | `0.0 - 1.0` | Profondità di modulazione FM. |
| **22** | `FMGAIN` | `0.0 - 1.0` | Guadagno d'uscita della sezione FM. |
| **23** | `PWM` | `0.0 - 1.0` | Modulazione di larghezza d'impulso (Pulse Width Modulation). |

---

## 🧭 Guide di Riferimento Rapido

### Selettore Inviluppi (`7. SELADSRS`)
* **`0`:** Modifica esclusivamente l'inviluppo di **Ampiezza (AMP)**.
* **`1`:** Modifica esclusivamente l'inviluppo del **Filtro (FILTER)**.
* **`2`:** Modifica **entrambi gli inviluppi (AMP + FILTER)** contemporaneamente.

### Matrice di Destinazione (`5. MACROSEL`)
Usa il parametro `MACROSEL` per scegliere quale livello interno modificare con la manopola `MACRO`:
* **`0`:** Guadagno Master / Uscita generale (`MAIN GAIN`)
* **`1` - `4`:** Mix individuale degli oscillatori (`OSC 1`, `OSC 2`, `OSC 3`, `OSC 4`)
* **`5`:** Livello del segnale diretto (`DRY LEVEL`)
* **`6` - `13`:** Mandate individuali alla sezione PWM (`PWM OSC 1` - `OSC 4`)
* **`14` - `20`:** Mandate individuali alla sezione FM (`FM OSC 1` - `OSC 4`) e livello effetto (`WET LEVEL`)

---

## 📥 Installazione su Korg drumlogue

1. Scarica il file **`monopolic.drmlgunit`** dalla sezione [Releases](../../releases) di questo repository.
2. Collega il tuo Korg drumlogue al computer tramite cavo USB.
3. Accendi il drumlogue tenendo premuto il tasto **[PLAY]** per avviarlo in **USB Storage Mode**.
4. Copia il file `monopolic.drmlgunit` all'interno della cartella:
   ```text
   /Units/Synths/
   ```
5. Espelli l'unità in modo sicuro dal sistema operativo e riavvia il drumlogue.
6. Seleziona la traccia **USER**, scegli il motore **SYNTH** e carica **Monopolic**.

## 🛠️ Compilazione dal Codice Sorgente

Se desideri esplorare o modificare la patch originale in Pure Data:

1. Installa [Plugdata](https://plugdata.org), [hvcc](https://github.com) e il [Korg logue-sdk](https://github.com).
2. Apri il file sorgente `.pd` in Plugdata e compila per la piattaforma `drumlogue`, oppure esegui:
   ```bash
   hvcc monopolic.pd -o ./build -n monopolic -g drumlogue
   ```

## 📄 Licenza

Distribuito sotto licenza **MIT**. Consulta il file [LICENSE](LICENSE) per maggiori dettagli.

---
Sviluppato con ❤️ da **CrystalMatrix** | Basato su **Plugdata** & **hvcc**.
