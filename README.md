# Visualizador Hidrodinámico: Dispersión de Gas en Biorreactor

Plataforma interactiva para el análisis comparativo del comportamiento hidrodinámico y los regímenes de dispersión de gas (inundación, carga y dispersión completa) bajo un diseño experimental factorial $3^3$.

---

## Contexto del Diseño Experimental

El estudio evalúa el impacto de la velocidad de agitación, el caudal de aireación y el volumen de líquido sobre la distribución del tamaño de burbujas, retención gaseosa (*gas hold-up*) y patrones de mezclado en un biorreactor de tanque agitado:

* **Volúmenes de trabajo ($V$):** 35 L, 38 L y 40 L
* **Tasa de aireación específica:** 0.45, 0.75 y 1.10 $\text{min}^{-1}$ (VVM)
* **Velocidad de agitación ($N$):** 0, 150 y 300 RPM
* **Total de corridas:** 27 condiciones experimentales

---

## Funcionalidades de la Plataforma

* **Matriz Operativa 3x3:** Visualización simultánea desacoplada por nivel de volumen para evaluar la transición entre agitación (filas) y aireación (columnas).
* **Filtro Comparativo Cruzado:** Selector multi-variable para aislar condiciones específicas (ej. comparar el efecto de la altura de columna manteniendo constantes RPM y VVM).
* **Comparador Simultáneo Lado a Lado:** Selección manual de 2 o más corridas con reproducción sincronizada y control de velocidad (0.5x / 1.0x).
* **Descarga de Datos:**
  * Descarga individual con nomenclatura estandarizada por corrida.
  * Exportación masiva de los 27 videos empaquetados en formato `.ZIP`.

---

## Matriz de Corridas Experimentales

| Corrida | Volumen (L) | VVM ($\text{min}^{-1}$) | Flujo Volumétrico (L/min) | Flujo Másico (g/min) | Agitación (RPM) |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1 | 35 | 0.45 | 15.75 | 16.51 | 0 |
| 2 | 35 | 0.45 | 15.75 | 16.51 | 150 |
| 3 | 35 | 0.45 | 15.75 | 16.51 | 300 |
| 4 | 35 | 0.75 | 26.25 | 27.51 | 0 |
| 5 | 35 | 0.75 | 26.25 | 27.51 | 150 |
| 6 | 35 | 0.75 | 26.25 | 27.51 | 300 |
| 7 | 35 | 1.10 | 38.50 | 40.35 | 0 |
| 8 | 35 | 1.10 | 38.50 | 40.35 | 150 |
| 9 | 35 | 1.10 | 38.50 | 40.35 | 300 |
| 10 | 38 | 0.45 | 17.10 | 17.92 | 0 |
| 11 | 38 | 0.45 | 17.10 | 17.92 | 150 |
| 12 | 38 | 0.45 | 17.10 | 17.92 | 300 |
| 13 | 38 | 0.75 | 28.50 | 29.87 | 0 |
| 14 | 38 | 0.75 | 28.50 | 29.87 | 150 |
| 15 | 38 | 0.75 | 28.50 | 29.87 | 300 |
| 16 | 38 | 1.10 | 41.80 | 43.81 | 0 |
| 17 | 38 | 1.10 | 41.80 | 43.81 | 150 |
| 18 | 38 | 1.10 | 41.80 | 43.81 | 300 |
| 19 | 40 | 0.45 | 18.00 | 18.86 | 0 |
| 20 | 40 | 0.45 | 18.00 | 18.86 | 150 |
| 21 | 40 | 0.45 | 18.00 | 18.86 | 300 |
| 22 | 40 | 0.75 | 30.00 | 31.44 | 0 |
| 23 | 40 | 0.75 | 30.00 | 31.44 | 150 |
| 24 | 40 | 0.75 | 30.00 | 31.44 | 300 |
| 25 | 40 | 1.10 | 44.00 | 46.11 | 0 |
| 26 | 40 | 1.10 | 44.00 | 46.11 | 150 |
| 27 | 40 | 1.10 | 44.00 | 46.11 | 300 |

---

## Arquitectura Técnica

* **Frontend:** HTML5, CSS3 nativo y JavaScript vanilla (sin frameworks pesados para garantizar compatibilidad móvil y de escritorio).
* **Empaquetado en cliente:** `JSZip` vía CDN para compilar descargas `.zip` de forma asíncrona en memoria.
* **Alojamiento web:** GitHub Pages.
* **Almacenamiento de medios:** Cloudflare R2 (Object Storage) con entrega vía CDN bajo protocolo HTTPS.
* **Formato de video:** MP4 (H.264/AAC, codificación estandarizada para reproducción fluida multi-panel).

---

## Criterios de Evaluación Hidrodinámica

Al inspeccionar los paneles visuales, los regímenes observados corresponden a:

1. **Inundación (*Flooding* - Predominante a 0 RPM):** Ausencia de dispersión radial; el gas asciende por boyamiento vertical en forma de columna central con coalescencia severa[cite: 1].
2. **Carga (*Loading* - Típico a 150 RPM):** El gas es proyectado hacia la periferia por el impulsor, pero la energía disipada es insuficiente para arrastrar burbujas por debajo del plano del agitador[cite: 1].
3. **Dispersión Completa y Recirculación (300 RPM):** Ruptura eficiente, formación de microburbujas homogéneas y arrastre en todo el volumen útil del tanque[cite: 1].
