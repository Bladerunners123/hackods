# Proyecto Bladerunners — HackODS UNAM 2026

## Equipo

| Integrante | Rol |
|---|---|
| Luis Fernando Martínez Moreno | Análisis estadístico y modelado |
| Guadalupe Herrera Barragán | Visualización y diseño del tablero |
| Ana Lydia Herrera Macías | Integración de fuentes y narrativa |

---

## ODS elegidos

| ODS | Descripción | Rol en el proyecto |
|---|---|---|
| **ODS 4** | Educación de Calidad | Principal — tasa de abandono escolar en media superior |
| **ODS 1** | Fin de la Pobreza | Predictor estructural asociado a vulnerabilidad social |
| **ODS 5** | Igualdad de Género | Brecha entre hombres y mujeres en abandono escolar |
| **ODS 10** | Reducción de las Desigualdades | Disparidad territorial en vulnerabilidad educativa |

---

## Pregunta central

> **¿En qué medida la brecha de conectividad y el índice de pobreza predicen la tasa de abandono escolar en el nivel medio superior, y cómo varía este impacto por género en México?**

La deserción escolar no se interpreta en este proyecto como una decisión individual aislada, sino como un síntoma de desigualdades estructurales vinculadas con pobreza, rezago educativo y acceso desigual a internet.

---

## Objetivo general

Analizar la relación entre abandono escolar, pobreza, rezago educativo y conectividad digital en México, con énfasis en la educación media superior, para identificar patrones territoriales de vulnerabilidad y su vínculo con los Objetivos de Desarrollo Sostenible.

### Objetivos específicos

1. Construir un dataset estatal consolidado a partir de fuentes oficiales.
2. Estimar correlaciones entre abandono escolar y variables estructurales.
3. Ajustar modelos de regresión para evaluar el peso explicativo de pobreza, conectividad y rezago educativo.
4. Analizar la brecha de género en abandono escolar.
5. Identificar entidades con mayor vulnerabilidad educativa para su visualización en el tablero.

---

## Datos reales utilizados

| Dataset | Fuente | Año | Nivel | Uso en el proyecto |
|---|---|---|---|---|
| Tasa de abandono por entidad federativa | INEGI / SEP | 2022-2023 | Estatal | Variable objetivo principal |
| Pobreza multidimensional | CONEVAL | 2022 | Estatal | Predictor estructural |
| Rezago educativo | CONEVAL | 2022 | Estatal | Variable complementaria |
| Hogares con acceso a internet (ENDUTIH) | INEGI / IFT | 2023 | Estatal | Proxy de conectividad |
| Metas ODS 4 | UNESCO UIS | 2023 | Nacional | Marco de contextualización |

### Cifras nacionales verificadas

- **Abandono en media superior:** 11.2 %
- **Abandono hombres:** 13.5 %
- **Abandono mujeres:** 9.1 %
- **Brecha de género:** 4.4 puntos porcentuales
- **Pobreza nacional:** 36.3 %
- **Hogares con internet:** 71.7 %
- **Acceso a internet rural:** 66.0 %
- **Acceso a internet urbano:** 85.5 %

---

## Justificación de la selección de datos

Se eligieron fuentes oficiales y metodológicamente sólidas para garantizar la validez y reproducibilidad del análisis:

- **CONEVAL** aporta la medición multidimensional de pobreza y rezago educativo con desagregación por entidad federativa.
- **INEGI / SEP** proporcionan la tasa de abandono escolar por sexo, nivel educativo y entidad, indispensable para analizar desigualdad educativa.
- **ENDUTIH 2023** ofrece una medida confiable del acceso a internet en los hogares, variable clave para aproximar la brecha digital.
- **UNESCO UIS** permite contextualizar el fenómeno dentro del marco internacional del ODS 4.

La combinación de estas fuentes permite construir un modelo explicativo y un **Índice de Vulnerabilidad Educativa**, útil para identificar territorios prioritarios de intervención.

---

## Metodología general

El proyecto se desarrolló en dos rutas complementarias:

### 1. Pipeline original en R
Se generó un dataset consolidado con valores oficiales por entidad y posteriormente se realizaron análisis estadísticos exploratorios e inferenciales.

### 2. Notebook de apoyo en Python
Se integró un notebook reproducible en Python para documentar de forma clara el flujo analítico, facilitar la revisión del jurado y permitir una ejecución alternativa del pipeline fuera de R.

---

## Notebook documentado: `01_pipeline_bladerunners_python.ipynb`

El archivo **`01_pipeline_bladerunners_python.ipynb`** concentra en un solo flujo de trabajo la lógica del proyecto en Python.

### Contenido del notebook

1. **Configuración del entorno**
   - Importación de librerías.
   - Definición de rutas de trabajo.
   - Creación de carpetas de salida si no existen.

2. **Construcción del dataset**
   - Carga manual de los valores estatales oficiales.
   - Creación del dataframe principal.
   - Cálculo de variables derivadas:
     - `brecha_genero`
     - `brecha_internet`
     - `indice_vulnerabilidad`
     - `zona_critica`
     - `contexto`

3. **Serie temporal nacional**
   - Integración de la serie histórica de abandono escolar por ciclo escolar.
   - Exportación de la serie para uso posterior en el tablero.

4. **Análisis estadístico**
   - Matriz de correlaciones con `abandono_total`.
   - Regresiones lineales múltiples.
   - Prueba de correlación entre pobreza e internet.
   - Resumen de brecha de género.
   - Identificación de zonas críticas.

5. **Exportación de resultados**
   - `datos/processed/datos_estados.csv`
   - `datos/processed/serie_temporal.csv`
   - `datos/processed/coeficientes_modelo.csv`

### Propósito del notebook

Este notebook no sustituye la interpretación del equipo; su función es:

- hacer transparente el proceso analítico,
- documentar cada transformación de datos,
- facilitar la reproducibilidad,
- y servir como respaldo técnico del proyecto.

---

## Estructura del repositorio

```text
hackatonods/
│
├── dashboard_files/
├── datos/
│   ├── raw/
│   └── processed/
│       ├── datos_estados.csv
│       ├── serie_temporal.csv
│       └── coeficientes_modelo.csv
│
├── 01_datos_reales.R
├── 02_analisis.R
├── 01_pipeline_bladerunners_python.ipynb
├── custom.scss
├── dashboard.html
├── dashboard.qmd
├── declaratoria_IA.md
├── Fuentes.txt
├── metadata.md
├── README.md
├── LICENSE
├── .RData
└── .Rhistory