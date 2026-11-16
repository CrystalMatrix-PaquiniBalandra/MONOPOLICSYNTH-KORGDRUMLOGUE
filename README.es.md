# MONOPOLICSYNTH-KORGDRUMLOGUE
FREE-MONOPOLICSYNTH-KORG DRUMLOGUE
# Monopolic - Korg drumlogue

![Version](https://shields.io)
![Author](https://shields.io)
![Platform](https://shields.io)
![Built with](https://shields.io)

**MONOPOLIC** Es un sintetizador de usuario para el **Korg drumlogue** creado por **CrystalMatrix aka Paquini Balandra**, inspirado en la arquitectura clásica de 4 osciladores del legendario sintetizador analógico **Korg Mono/Poly (1981)**.

Desarrollado visualmente en **Plugdata y con la libreria Heavylib** y compilado a C++ nativo mediante **hvcc (Heavy Compiler Collection)**, Monopolic lleva la versatilidad de los 4 VCOs con modulación cruzada (FM), modulación por ancho de pulso (PWM) y filtrado resonante directamente a la pista **USER** del drumlogue.

---

## 🎛️ Características Principales

* **Arquitectura de 4 Osciladores (`OSC 1` a `OSC 4`):**
  * Fiel al espíritu del Mono/Poly original, cuenta con 4 osciladores independientes con formas de onda seleccionables (*Off, Senoidal, Triangular, Diente de Sierra y Pulso*.
  * Afinación individual en un rango de **±3 octavas (`-36` a `+36` semitonos)** con ligeras desafinaciones analógicas internas (*detune* fijo en OSC 2, 3 y 4) para lograr bajos masivos, leads gruesos y texturas tipo *unison*.
* **Sección de Modulación (FM & PWM):**
  * Oscilador modulador dedicado (`FMWAVE`, `FMFREQ`, `FMDEPTH`, `FMGAIN`) para crear timbres metálicos, percusivos y efectos de modulación cruzada.
  * Modulación por ancho de pulso (`PWM`) ajustable en tiempo real.
* **Filtro Paso Bajo Resonante (24dB/oct aprox.):**
  * Doble etapa de filtros `vcf~` en serie con control de corte (`CUTOFF` de 20 Hz a 16 kHz), resonancia (`RES0`) y envolvente dedicada (`F.ENV`).
* **Envolventes Dinámicas (`SELADSRS`):**
  * Un único bloque de 4 controles (`ATTACK`, `DECAY`, `SUSTAIN`, `RELEASE`) que permite editar tanto la envolvente de amplitud (VCA) como la del filtro (VCF) sin saturar las páginas de menú.
* **Matriz de Enrutamiento Inteligente (`MACROSEL`):**
  * Sistema de control centralizado mediante una perilla maestra (`MACRO`) y un selector de 22 posiciones (`MACROSEL`) para mezclar niveles individuales de cada oscilador y sus envíos de modulación.

---

## 🎚️ Mapeo de Parámetros (`@hv_param`)

Monopolic expone **23 parámetros** organizados en la pantalla OLED del Korg drumlogue:

### Filtro y Control Macro

| # | Nombre en Pantalla | Rango | Función |
| :--- | :--- | :--- | :--- |
| **1** | `CUTOFF` | `0.0 - 1.0` | Frecuencia de corte del filtro paso bajo (curva exponencial). |
| **2** | `RES0` | `0.0 - 1.0` | Resonancia del doble filtro `vcf~`. |
| **3** | `F.ENV` | `0.0 - 1.0` | Cantidad de modulación de la envolvente sobre el corte del filtro. |
| **4** | `MACRO` | `0.0 - 1.0` | Ajusta el nivel o intensidad del destino seleccionado en `MACROSEL`. |
| **5** | `MACROSEL` | `0 - 21` | Selecciona el parámetro interno que controla la perilla `MACRO` *(ver tabla abajo)*. |
| **6** | `FMWAVE` | `0 - 5` | Selecciona la forma de onda del oscilador modulador FM. |

### Envolventes (ADSR)

| # | Nombre en Pantalla | Rango | Función |
| :--- | :--- | :--- | :--- |
| **7** | `SELADSRS` | `0 - 3` | Selecciona qué envolvente editan los controles 8 al 11 *(ver tabla abajo)*. |
| **8** | `ATTACK` | `0.1 - 1.0` | Tiempo de ataque (Attack). |
| **9** | `DECAY` | `0.1 - 1.0` | Tiempo de decaimiento (Decay). |
| **10** | `SUSTAIN` | `0.1 - 1.0` | Nivel de sostenimiento (Sustain). |
| **11** | `RELEASE` | `0.1 - 1.0` | Tiempo de relajación al soltar la nota (Release). |

### Osciladores y Síntesis FM/PWM

| # | Nombre en Pantalla | Rango | Función |
| :--- | :--- | :--- | :--- |
| **12** | `WF1` | `0 - 5` | Forma de onda del Oscilador 1 (`0=Off, 1=Sine, 2=Tri, 3=Saw, 4=Pulse`). |
| **13** | `WF2` | `0 - 5` | Forma de onda del Oscilador 2. |
| **14** | `WVFORM3` | `0 - 5` | Forma de onda del Oscilador 3. |
| **15** | `WVFORM4` | `0 - 5` | Forma de onda del Oscilador 4. |
| **16** | `OCT1` | `-36 a +36` | Afinación en semitonos del Oscilador 1. |
| **17** | `OCT2` | `-36 a +36` | Afinación en semitonos del Oscilador 2 *(+0.15 semi detune fijo)*. |
| **18** | `OCTAVE3` | `-36 a +36` | Afinación en semitonos del Oscilador 3 *(-0.12 semi detune fijo)*. |
| **19** | `OCTAVE4` | `-36 a +36` | Afinación en semitonos del Oscilador 4 *(+0.22 semi detune fijo)*. |
| **20** | `FMFREQ` | `0.0 - 1.0` | Frecuencia del oscilador modulador FM. |
| **21** | `FMDEPTH` | `0.0 - 1.0` | Profundidad de modulación FM. |
| **22** | `FMGAIN` | `0.0 - 1.0` | Ganancia de salida de la sección FM. |
| **23** | `PWM` | `0.0 - 1.0` | Modulación de ancho de pulso (Pulse Width). |

---

## 🧭 Guías de Referencia Rápida

### Selector de Envolventes (`7. SELADSRS`)
* **`0`:** Edita únicamente la envolvente de **Amplitud (AMP)**.
* **`1`:** Edita únicamente la envolvente del **Filtro (FILTER)**.
* **`2`:** Edita **Ambas envolventes (AMP + FILTER)** simultáneamente.

### Matriz de Destinos (`5. MACROSEL`)
Usa el parámetro `MACROSEL` para elegir qué nivel interno deseas modificar con la perilla `MACRO`:
* **`0`:** Ganancia Master / Salida general (`MAIN GAIN`)
* **`1` - `4`:** Mezcla individual de osciladores (`OSC 1`, `OSC 2`, `OSC 3`, `OSC 4`)
* **`5`:** Nivel de señal directa (`DRY LEVEL`)
* **`6` - `13`:** Envíos individuales a la sección PWM (`PWM OSC 1` a `OSC 4`)
* **`14` - `20`:** Envíos individuales a la sección FM (`FM OSC 1` a `OSC 4`) y nivel Wet (`WET LEVEL`)

---

## 📥 Instalación en el Korg drumlogue

1. Descarga el archivo **`monopolic.drmlgunit`** desde la sección de [Releases](../../releases) de este repositorio.
2. Conecta tu Korg drumlogue a tu computadora mediante un cable USB.
3. Enciende el drumlogue manteniendo presionado el botón **[PLAY]** para iniciar en **USB Storage Mode**.
4. Copia el archivo `monopolic.drmlgunit` dentro de la carpeta:
   ```text
   /Units/Synths/
   ```
5. Expulsa la unidad de forma segura desde tu sistema operativo y reinicia el drumlogue.
6. Selecciona la pista **USER**, elige el motor **SYNTH** y busca **Monopolic**.

## 🛠️ Compilación desde el Código Fuente

Si deseas explorar o modificar el patch original en Pure Data:

1. Instala [Plugdata](https://plugdata.org), [hvcc](https://github.com) y el [Korg logue-sdk](https://github.com).
2. Abre el archivo fuente `.pd` en Plugdata y compila para la plataforma `drumlogue`, o ejecuta:
   ```bash
   hvcc monopolic.pd -o ./build -n monopolic -g drumlogue
   ```

## 📄 Licencia

Distribuido bajo la licencia **MIT**. Consulta el archivo [LICENSE](LICENSE) para más detalles.

---
Desarrollado con ❤️ por **CrystalMatrix** | Impulsado por **Plugdata** & **hvcc**.
