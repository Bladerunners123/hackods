# Proyecto Bladerunners | HackODS UNAM 2026

Tablero Quarto sobre abandono escolar en media superior, vulnerabilidad educativa y priorización territorial en México.

## Reproducibilidad con `uv`

Desde la raíz del repositorio:

```powershell
uv sync
uv run quarto render dashboard/index.qmd
```

El render esperado genera `docs/index.html`.

## Estructura relevante

```text
hackatonods/
├── pyproject.toml
├── dashboard/
│   ├── _quarto.yml
│   ├── custom.scss
│   ├── index.qmd
│   └── mexico_states.geojson
├── datos/
│   ├── metadata.md
│   └── processed/
│       ├── datos_estados.csv
│       ├── serie_temporal.csv
│       ├── brecha_genero_estados.csv
│       ├── coeficientes_modelo.csv
│       └── zonas_criticas.csv
└── docs/
    ├── index.html
    └── metadata.md
```

## Fuentes

- INEGI / SEP, abandono escolar en media superior por entidad y sexo, ciclo 2022-2023.
- CONEVAL, pobreza multidimensional y rezago educativo, 2022.
- ENDUTIH, acceso a internet en hogares, 2023.

## Hallazgo principal

Los estados con mayor pobreza y menor conectividad no siempre son los que registran hoy la tasa más alta de abandono, pero sí concentran el mayor riesgo estructural de exclusión educativa. El tablero usa el Índice de Vulnerabilidad Educativa (IVE) para visibilizar esa diferencia y priorizar territorio.
