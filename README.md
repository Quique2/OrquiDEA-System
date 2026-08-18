# Investigación — paper IEEE "Sistema OrquiDEA" (documento completo)

Documento de investigación del gemelo digital Schneider (Sistema OrquiDEA),
**redactado y verificado contra el código** el 2026-08-18 (auditoría con
lectores por subsistema: gateway RPi, frontend web, SCADA+IA y
arquitecturas) y **enriquecido con los datos medidos del informe técnico
final** (corrida real: 181.9 s promedio / 80.8 % idle; simulación
optimizada: 138.8 s / 22.0 %). La bibliografía fue verificada entrada por
entrada contra Crossref, IEEE, Springer, modbus.org, IEC e ISO.

## Versiones e idiomas

- `main.tex` + `referencias.bib` — versión en **español** (repo
  `OrquiDEA-System`, proyecto Overleaf original).
- `english/main.tex` + `english/referencias.bib` — versión en **inglés**
  (repo `OrquiDEA-System-Copy-`, proyecto Overleaf copia).
- Autores: E. A. González Hernández (A01178473), S. Ordóñez Ramírez
  (A01769810), D. Becerra Fuentes (A00838679) y el profesor asesor
  Alexandro Ortiz. R. Díaz Arrigunaga se acredita en los agradecimientos y
  como coautor del informe técnico citado.

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

## Capturas de la app (LISTAS — tomadas el 2026-08-18 del deploy en Railway
con Playwright + Chrome headless, sesión sembrada, sin credenciales visibles)

1. `captura_visor3d.png` — pestaña "Celda 3D" con la FSM corriendo
   (RUNNING, 2 CAFIs en fixtures, remachado activo). [Simulación local.]
2. `captura_scadasim.png` — SCADA SIM alimentado por BroadcastChannel,
   corrida activa con 3 piezas en proceso. [Simulación local.]
3. `captura_scada_offline.png` — SCADA real con el gateway fuera de línea:
   ilustra la política real-only (todo N/D en vez de valores inventados).

Las tres ya están referenciadas en `main.tex` con leyendas que declaran su
fidelidad. Si algún día se captura la vista "Cobot en Vivo" con el gateway
encendido (telemetría real), puede añadirse como figura adicional.

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
