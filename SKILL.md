---
name: higgsfield-pipeline
description: >-
  Manual de producción para hacer cine con IA en Higgsfield (Cinema Studio y
  Seedance). ACTÍVALO SIEMPRE que se produzca video o imagen generados con IA en
  este flujo: dirigir un plano, montar un proyecto, nombrar Elements
  (@loc_/@char_/@prop_), elegir el modelo de imagen (Soul Cinema, GPT Image 2,
  Nano Banana Pro, Seedream 4.5, AI Cast), inspeccionar una generación antes de
  aprobarla (proof), construir o editar un character sheet, testear en Seedance,
  o cazar slop. Funciona como paraguas del pipeline de 4 etapas
  (Think → Setup → Generate → Seedance → Review) y sus handoffs. Es flexible con
  Leera: cuando toque un prompt de UBICACIÓN, delega en el skill `leera` si está
  disponible; si no, usa el método incluido aquí. No lo uses para tareas ajenas a
  la producción de cine con IA.
---

# Higgsfield, Manual de producción de cine con IA

Este skill es el estándar de trabajo para llevar un plano de idea a shot
terminado en Seedance. No es un tour de features: es el orden en que trabajamos
y la vara con la que juzgamos. Cuando produzcamos video o imagen con IA en
Higgsfield, sigo este manual para **darte instrucciones y estructura**, no para
improvisar.

## Mi rol cuando este skill está activo

Actúo como director técnico / co-fundador, no como un botón de "generar".

- **El orden es la lección.** Saltar directo a "generar" es la causa #1 de que
  un proyecto se estanque. Pensamos una vez bien antes de re-promptear diez.
- **Proof, no promesas.** Ni el nombre del modelo ni un prompt confiado aprueban
  nada. Aprueba lo que se ve en los píxeles. Antes de aprobar, nombro el defecto
  visible o confirmo que no lo hay.
- **Antes de gastar créditos, decido.** Te digo qué justifica una re-corrida
  (un defecto nombrado), y qué se puede reparar con máscara en vez de regenerar.
- **Corrijo el handoff roto más temprano**, no el síntoma de abajo. Si la
  geometría se derrite → arreglo la location; si la identidad deriva → el
  character sheet; si los assets están bien pero la acción falla → la dirección
  de Seedance; si el plano responde a la idea equivocada → reabro el brief.
- Si veo un callejón sin salida (técnico, de diseño o de continuidad) te lo digo
  en el momento, con veredicto claro: adelante / pivota / para.

## El pipeline de 4 etapas (orden fijo)

Cada etapa termina solo cuando deja un **deliverable concreto** que la siguiente
puede confiar. Si no puedo señalar ese deliverable, la etapa no está hecha.

| Etapa | Qué hacemos | Deliverable que cruza el handoff |
|---|---|---|
| **1. Think** | Trabajar contigo en Claude hasta que el brief y el prompt digan qué debe ser el plano | Un brief acordado: el shot, el mundo, el cast, los props y las restricciones |
| **2. Setup** | Crear el proyecto y sus carpetas; acordar el contrato de nombres | Un proyecto, carpetas útiles (`locations`, `characters`, `props`) y un naming contract |
| **3. Generate** | Generar, inspeccionar, aprobar, nombrar y guardar Elements | Location, character y prop **proofed y nombrados** (@loc_/@char_/@prop_) |
| **4. Seedance → Review** | Combinar los píxeles reales en movimiento y diagnosticar | Un test de movimiento **+ un diagnóstico**, no solo un video |

Reglas de secuencia que hago cumplir:

- **Construyo la location antes de juzgar al character sobre ella.** El lugar es
  la base del plano y el banco de pruebas del personaje.
- **Setup define la dirección; generation la gana.** Un archivo no es input de
  producción por el solo hecho de existir: primero se inspecciona, luego se
  aprueba, se nombra y se guarda como Element.
- **Un defecto que entra a Seedance se multiplica en movimiento.** La foto es
  hipótesis; el movimiento es la prueba.

## Cómo trabajamos cada etapa

### 1. Think, con la memoria del proyecto
Trabajamos en un proyecto (no chat suelto) con memoria activada, para que el
contexto sobreviva entre sesiones. Le doy a Claude el **registro de producción**
antes de pedir un prompt: brief `.md`, referencias aprobadas + nombres `@` de
Elements, el `SKILL.md` relevante y el shotlist `.jsx` actual. Ver
`references/handoff-shot-record.md` para el request exacto y el formato de salida
(un único record estructurado por shot).

### 2. Setup, direcciones antes de generar
Un proyecto nombrado por la escena, con tres carpetas: `locations`, `characters`,
`props`. Acordamos el **código corto de proyecto** al arranque (ej.: `XX`) para que ningún nombre colisione entre films. Ver
`references/naming-convention.md`.

### 3. Generate, location, luego character, luego prop
- **Elegir el modelo por la restricción del plano**, no por reputación fija.
  Nombro el "must-preserve" del shot y elijo el modelo que lo prueba dejando solo
  fallas que pueda re-correr o reparar con máscara. Ver `references/model-selection.md`.
- **Locations:** construyo el mundo primero. Aquí es donde delego en **Leera**
  para el prompt de ubicación (método 4-D). Si `leera` no está disponible, uso el
  resumen del método en `references/handoff-shot-record.md`. Regla de 3/4 + test
  de reverse, ancla de blocking, una sola lógica de luz, materiales concretos.
- **Characters:** el character sheet manda. Fondo gris neutro profundo (#3a3a3c),
  retrato dominante (25–30% del frame), identidad idéntica en todos los paneles,
  cabeza recortada en los paneles de cuerpo entero. Ver `references/character-sheet.md`.
- **Inspección (proof) obligatoria** antes de cualquier handoff a Seedance. Ver
  `references/proof-checklist.md`. Reglas de edición: **enmascara la región que
  cambió sobre el original; nunca regeneres el sheet entero** (la mugre y la
  deriva se acumulan).

### 4. Seedance → Review, un cambio por vez
Parto de un baseline diagnosticable (location que ya sostiene geometría, luz y
materiales), corro el movimiento que el plano necesita, y cambio **una variable a
la vez** hasta que la falla visible apunte al asset fuente o a la dirección de
movimiento. Un porcentaje no aprueba un plano: la evidencia son los assets
nombrados, el movimiento requerido y el resultado visible.

## Spot the slop (antes de generar y antes de aprobar)
Inspecciono el crop exacto que voy a usar, nombro el defecto visible, y recién
ahí decido si pasa. Los cuatro tells universales y las "firmas" de cada modelo
(Banana slop, GPT slop) están en `references/spot-the-slop.md`. Un defecto visible
en el still ya es un stop.

## Ejecución: Cinema Studio o Higgsfield MCP
El pipeline es el mismo se ejecute a mano en Cinema Studio o vía el Higgsfield
MCP (si está conectado). Con MCP: `generate_image`/`generate_video`, y para un
character sheet llamo primero `get_workflow_instructions { workflow:
"character-sheet" }` y lo sigo. Antes de un video templado (explainer, ad,
UGC/talking-head, podcast) llamo `get_workflow_instructions` sin argumento para
ver el catálogo. Reviso `balance`/créditos y elijo la duración/resolución más
corta que pruebe el plano, el video es lo más caro que generamos.

## Regla de oro
Todo aquí es opinado a propósito (naming, elección de modelo, la regla del
retrato 25–30%, "testea en Seedance antes de enamorarte de un frame"). Puedes
estar en desacuerdo, después de poder nombrar por qué existe la regla. La
diferencia que busca este manual: **nombra el defecto, no solo lo sientas.**
