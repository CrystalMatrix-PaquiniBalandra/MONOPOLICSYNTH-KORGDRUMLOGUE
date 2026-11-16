# MONOPOLICSYNTH - KORG DRUMLOGUE

**FREE - MONOPOLICSYNTH - KORG DRUMLOGUE**  
**Monopolic - Korg drumlogue**

![Version](https://shields.io)
![Author](https://shields.io)
![Platform](https://shields.io)
![Built with](https://shields.io)

**MONOPOLIC** ist ein User-Synthesizer für den **Korg drumlogue**, entwickelt von **CrystalMatrix (aka Paquini Balandra)**. Er ist inspiriert von der klassischen 4-Oszillator-Architektur des legendären analogen Synthesizers **Korg Mono/Poly (1981)**.

Visuell in **Plugdata** mit der **Heavylib**-Bibliothek entwickelt und über **hvcc (Heavy Compiler Collection)** in nativen C++-Code kompiliert, bringt Monopolic die Vielseitigkeit von 4 VCOs mit Cross-Modulation (FM), Pulsweitenmodulation (PWM) und resonantem Filter direkt auf den **USER**-Track des drumlogue.

---

## 🎛️ Hauptmerkmale

* **4-Oszillator-Architektur (`OSC 1` bis `OSC 4`):**
  * Getreu dem Geist des originalen Mono/Poly verfügt der Synthesizer über 4 unabhängige Oszillatoren mit wählbaren Wellenformen (*Off, Sinus, Dreieck, Sägezahn und Puls*) samt **PolyBLEP**-Anti-Aliasing.
  * Individuelle Stimmung im Bereich von **±3 Oktaven (`-36` bis `+36` Halbtöne)** mit subtilen internen analogen Verstimmungen (*festes Detune* bei OSC 2, 3 und 4) für druckvolle Bässe, fette Leads und Unison-ähnliche Texturen.
* **Modulationssektion (`FM & PWM`):**
  * Dedizierter Modulator-Oszillator (`FMWAVE`, `FMFREQ`, `FMDEPTH`, `FMGAIN`) für metallische Klänge, perkussive Sounds und Cross-Modulation-Effekte.
  * In Echtzeit steuerbare Pulsweitenmodulation (`PWM`).
* **Resonantes Tiefpassfilter (ca. 24 dB/Okt.):**
  * Zweistufiges `vcf~`-Filter in Reihenschaltung mit Cutoff-Regler (`CUTOFF` von 20 Hz bis 16 kHz), Resonanz (`RES0`) und dedizierter Hüllkurve (`F.ENV`).
* **Dynamische Hüllkurven (`SELADSRS`):**
  * Ein einziger Reglerblock (`ATTACK`, `DECAY`, `SUSTAIN`, `RELEASE`), mit dem über einen Wahlschalter sowohl die Lautstärkehüllkurve (VCA) als auch die Filterhüllkurve (VCF) bearbeitet werden können, ohne die Menüseiten zu überladen.
* **Intelligente Routing-Matrix (`MACROSEL`):**
  * Zentrales Steuerungssystem über einen Master-Regler (`MACRO`) und einen 22-stufigen Wahlschalter (`MACROSEL`) zum Mischen der einzelnen Oszillatorpegel und ihrer Modulations-Sends.

---

## 🎚️ Parameter-Mapping (`@hv_param`)

Monopolic stellt **23 Parameter** bereit, die übersichtlich auf dem OLED-Display des Korg drumlogue angeordnet sind:

### Filter & Makro-Steuerung

| # | Display-Name | Bereich | Funktion |
| :--- | :--- | :--- | :--- |
| **1** | `CUTOFF` | `0.0 - 1.0` | Grenzfrequenz des Tiefpassfilters (exponentielle Kurve). |
| **2** | `RES0` | `0.0 - 1.0` | Resonanz des zweistufigen `vcf~`-Filters. |
| **3** | `F.ENV` | `0.0 - 1.0` | Modulationsintensität der Hüllkurve auf den Filter-Cutoff. |
| **4** | `MACRO` | `0.0 - 1.0` | Regelt den Pegel oder die Intensität des unter `MACROSEL` gewählten Ziels. |
| **5** | `MACROSEL` | `0 - 21` | Wählt den internen Parameter aus, der mit dem `MACRO`-Regler gesteuert wird *(siehe Tabelle unten)*. |
| **6** | `FMWAVE` | `0 - 5` | Wählt die Wellenform des FM-Modulator-Oszillators. |

### Hüllkurven (ADSR)

| # | Display-Name | Bereich | Funktion |
| :--- | :--- | :--- | :--- |
| **7** | `SELADSRS` | `0 - 3` | Wählt aus, welche Hüllkurve mit den Reglern 8 bis 11 bearbeitet wird *(siehe Tabelle unten)*. |
| **8** | `ATTACK` | `0.1 - 1.0` | Einschwingzeit (Attack). |
| **9** | `DECAY` | `0.1 - 1.0` | Abklingzeit (Decay). |
| **10** | `SUSTAIN` | `0.1 - 1.0` | Haltepegel (Sustain). |
| **11** | `RELEASE` | `0.1 - 1.0` | Ausklingzeit nach dem Loslassen der Note (Release). |

### Oszillatoren & FM/PWM-Synthese

| # | Display-Name | Bereich | Funktion |
| :--- | :--- | :--- | :--- |
| **12** | `WF1` | `0 - 5` | Wellenform von Oszillator 1 (`0=Off, 1=Sine, 2=Tri, 3=Saw, 4=Pulse`). |
| **13** | `WF2` | `0 - 5` | Wellenform von Oszillator 2. |
| **14** | `WVFORM3` | `0 - 5` | Wellenform von Oszillator 3. |
| **15** | `WVFORM4` | `0 - 5` | Wellenform von Oszillator 4. |
| **16** | `OCT1` | `-36 bis +36` | Stimmung von Oszillator 1 in Halbtönen. |
| **17** | `OCT2` | `-36 bis +36` | Stimmung von Oszillator 2 in Halbtönen *(+0,15 Halbtöne festes Detune)*. |
| **18** | `OCTAVE3` | `-36 bis +36` | Stimmung von Oszillator 3 in Halbtönen *(-0,12 Halbtöne festes Detune)*. |
| **19** | `OCTAVE4` | `-36 bis +36` | Stimmung von Oszillator 4 in Halbtönen *(+0,22 Halbtöne festes Detune)*. |
| **20** | `FMFREQ` | `0.0 - 1.0` | Frequenz des FM-Modulator-Oszillators. |
| **21** | `FMDEPTH` | `0.0 - 1.0` | Modulationstiefe der FM-Synthese. |
| **22** | `FMGAIN` | `0.0 - 1.0` | Ausgangspegel der FM-Sektion. |
| **23** | `PWM` | `0.0 - 1.0` | Pulsweitenmodulation (Pulse Width Modulation). |

---

## 🧭 Kurzreferenz

### Hüllkurven-Wahlschalter (`7. SELADSRS`)
* **`0`:** Bearbeitet ausschließlich die **Lautstärkehüllkurve (AMP)**.
* **`1`:** Bearbeitet ausschließlich die **Filterhüllkurve (FILTER)**.
* **`2`:** Bearbeitet **beide Hüllkurven (AMP + FILTER)** gleichzeitig.

### Ziel-Matrix (`5. MACROSEL`)
Verwende den Parameter `MACROSEL`, um festzulegen, welchen internen Pegel du mit dem Regler `MACRO` steuern möchtest:
* **`0`:** Master-Gain / Gesamtausgang (`MAIN GAIN`)
* **`1` - `4`:** Einzelne Oszillator-Pegel (`OSC 1`, `OSC 2`, `OSC 3`, `OSC 4`)
* **`5`:** Direktsignal-Pegel (`DRY LEVEL`)
* **`6` - `13`:** Individuelle Sends an die PWM-Sektion (`PWM OSC 1` bis `OSC 4`)
* **`14` - `20`:** Individuelle Sends an die FM-Sektion (`FM OSC 1` bis `OSC 4`) und Effektanteil (`WET LEVEL`)

---

## 📥 Installation auf dem Korg drumlogue

1. Lade die Datei **`monopolic.drmlgunit`** aus dem Bereich [Releases](../../releases) dieses Repositorys herunter.
2. Verbinde deinen Korg drumlogue per USB-Kabel mit deinem Computer.
3. Schalte den drumlogue ein, während du die **[PLAY]**-Taste gedrückt hältst, um den **USB Storage Mode** zu starten.
4. Kopiere die Datei `monopolic.drmlgunit` in folgenden Ordner:
   ```text
   /Units/Synths/
   ```
5. Wirf das Laufwerk sicher über dein Betriebssystem aus und starte den drumlogue neu.
6. Wähle den **USER**-Track aus, stelle die Engine auf **SYNTH** und lade **Monopolic**.

## 🛠️ Kompilieren aus dem Quellcode

Wenn du den ursprünglichen Patch in Pure Data ansehen oder anpassen möchtest:

1. Installiere [Plugdata](https://plugdata.org), [hvcc](https://github.com) und das [Korg logue-sdk](https://github.com).
2. Öffne die `.pd`-Quelldatei in Plugdata und kompiliere sie für die Plattform `drumlogue`, oder führe folgenden Befehl aus:
   ```bash
   hvcc monopolic.pd -o ./build -n monopolic -g drumlogue
   ```

## 📄 Lizenz

Veröffentlicht unter der **MIT**-Lizenz. Weitere Informationen findest du in der Datei [LICENSE](LICENSE).

---
Entwickelt mit ❤️ von **CrystalMatrix** | Powered by **Plugdata** & **hvcc**.
