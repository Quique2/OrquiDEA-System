# Investigación — paper IEEE (documento completo)

Documento de investigación del gemelo digital Schneider, **redactado y
verificado contra el código** el 2026-08-18 (auditoría con lectores por
subsistema: gateway RPi, frontend web, SCADA+IA y arquitecturas). La
bibliografía fue verificada entrada por entrada contra Crossref, IEEE,
Springer, modbus.org, IEC e ISO — ya no quedan marcas `VERIFICAR`.

## Compilar en Overleaf (recomendado)

1. Crear proyecto nuevo en overleaf.com → **Upload Project** → subir el ZIP
   `investigacion_overleaf.zip` (o la carpeta completa `investigacion/`).
2. Compilador: **pdfLaTeX** (Menu → Compiler). Documento raíz: `main.tex`.
3. Compilar dos veces (Overleaf corre BibTeX automáticamente).

Local: `latexmk -pdf main.tex` (TeX Live / MiKTeX).

## Estructura

- `main.tex` — documento completo (IEEEtran conference, en español):
  resumen, introducción, marco teórico, contexto del reto, las dos
  arquitecturas (tabla comparativa), gateway IIoT (mapa Modbus verificado),
  gemelo web, visión, SCADA 4.0 + IA, resultados con etiquetado de
  fidelidad, discusión y conclusiones. Incluye 2 diagramas TikZ
  (arquitectura de capas y ciclo de 32 pasos) que compilan sin archivos
  externos.
- `referencias.bib` — 17 entradas **verificadas** (académicas, normas
  IEC/ISO vigentes 2025, software y fichas oficiales de hardware).
- `figuras/`
  - `camara_cafi_template.png` — captura REAL de la cámara Datalogic P15
    (usada en la Fig. de inspección; ya referenciada en `main.tex`).
  - `diagrama_cableado.svg` — diagrama de cableado (fuente SVG, generado
    del DXF). Para usarlo en el paper: exportarlo a PDF (Inkscape:
    `inkscape diagrama_cableado.svg --export-type=pdf`) y añadir un
    `\includegraphics`.
  - `hmi_operador.svg` — panel HMI del operador (misma conversión si se
    quiere incluir).

## Capturas pendientes (opcionales, ya hay huecos comentados en main.tex)

1. `captura_visor3d.png` — pestaña "Cobot en Vivo" del gemelo
   (`npm start` en `SchneiderProjectWeb_DigitalTwin/`).
2. `captura_scada.png` — panel SCADA 4.0 con los 5 pilares.

Descomentar los bloques `\begin{figure}` correspondientes en la sección de
Resultados de `main.tex` tras colocar los PNG en `figuras/`.

## Reglas editoriales aplicadas (mantener al editar)

1. Ninguna cita sin verificar. Si se añade una referencia nueva, confirmar
   título/autores/año/DOI contra la fuente antes de citarla.
2. La fidelidad de cada dato está etiquetada (telemetría real / derivado /
   simulación local / DEMO) — ver Tabla de fidelidad en Resultados. No
   presentar datos simulados como mediciones.
3. Sin datos sensibles: el subdominio del túnel ngrok, las URLs de deploy y
   las credenciales hardcodeadas NO aparecen en el texto. Mantenerlo así.
4. El remachado es un ciclo simulado de 30 s (restricción del reto) y así
   se declara en el texto — no convertirlo en "remachado real" al editar.
