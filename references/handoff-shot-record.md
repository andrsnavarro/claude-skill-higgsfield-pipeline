# Handoff, de archivos del proyecto a un shot record

No pidas "haz el prompt" en aislamiento. Dale a Claude el registro de producción
primero, y que devuelva **un** record estructurado por shot.

## Los tres tipos de archivo del workflow
- **`.md`**, texto plano (Markdown). Notas, instrucciones y skills.
- **Skill (`SKILL.md`)**, carpeta de instrucciones `.md` con las reglas de un
  tema; Claude la abre cuando la tarea encaja y trabaja a ese estándar. No todo
  `.md` es un skill; a veces es solo un system prompt.
- **`.jsx`**, técnicamente código, pero lo usamos como **shotlist**: contenedor
  estructurado de datos de shot (número, descripción, timing, prompts) del que
  Claude lee los campos.

## Qué entregar a Claude (autoridad explícita)
| Input | Aporta |
|---|---|
| Scene brief `.md` | Beat de historia e intención del shot |
| Referencias aprobadas + nombres `@` exactos de Elements | Identidad de character, location y prop |
| `SKILL.md` relevante | Reglas para este tipo de prompt |
| Shotlist `.jsx` actual | Número de shot, timing y continuidad |

La memoria ayuda a recordar el proyecto, pero **no elige el brief más reciente por
ti**, dile a Claude cuáles archivos son autoritativos.

## El request (reemplaza lo entre corchetes)
```
Use the scene brief, approved reference images, relevant SKILL.md, and current
.jsx shotlist in this project.
Prepare shot [number] only. Preserve the story beat, continuity, and approved
Element names. If a missing decision would change the shot, ask before writing.
Do not invent an Element.
Return one record with exactly this structure and no preamble:
{
shot: "[number]",
description: "[one-sentence action and framing]",
duration: "[seconds]",
elements: ["[@name]", "[@name]"],
prompt: "[one complete, standalone Cinema Studio prompt]"
}
```

## Después del record
Revisa el record en Claude, guárdalo en el `.jsx` shotlist. Cinema Studio **no**
ingiere ese archivo entero: abre el proyecto y la carpeta correctos, pega el valor
`prompt` en el Prompt Box, y selecciona cada entrada de `elements` por el `@`
picker. Para video, lleva también `duration`. Antes de generar, los tags `@`
visibles deben calzar con el record exactamente.

---

# Método de prompt (fallback si Leera no está)

Cuando el skill `leera` está disponible, **delega en él** para prompts de
ubicación (corre el método 4-D con su decision log). Este resumen es el fallback.

## Seis decisiones, luego un prompt
No hay fórmula universal de oración. Hay un pase de decisiones fiable: separa
**subject, action, setting, light, camera/motion, constraints**, y ensambla las
seis respuestas en un párrafo. Un pensamiento crudo insinúa un slot sin
resolverlo ("hot summer day" no dice nada sobre dirección de luz ni forma de
sombra). El párrafo final no es mejor por ser más largo: cada cláusula tiene un
trabajo. Si Claude agrega un prop/estilo/clima/movimiento no elegido, pregunta
qué ambigüedad resuelve, luego apruébalo, reemplázalo o quítalo.

## El método 4-D de Leera (resumen)
1. **DECONSTRUCT**, cita las palabras útiles del brief y mapéalas a los seis
   slots (+ camera motion si el target es video). Marca cada slot como explícito,
   implícito o faltante.
2. **DIAGNOSE**, audita gaps y ambigüedad. Chequea lógica: un solo sol, puertas y
   ventanas creíbles, sombras que caen lejos de la fuente declarada. Por cada gap,
   pregunta o etiqueta el default propuesto. Nunca agregues clima/props/estilo/
   movimiento en silencio.
3. **DEVELOP**, construye desde decisiones aprobadas: un subject y action
   claros, el setting alrededor, un **objeto ancla nombrado** (sofá, umbral,
   banner) para colocar al character después, luz explícita (fuentes suaves en
   interiores, rayos duros visibles suelen slopear), paleta tonal con falloff
   suave sin sombras aplastadas, y ángulo de cámara (default 3/4 para profundidad
   si no das ángulo). Movimiento solo para video. Sustantivos concretos sobre
   palabras de calidad ("weathered wood siding", nunca "beautiful").
4. **DELIVER**, el prompt optimizado como un párrafo en inglés, luego un decision
   log: por cada detalle agregado o reescrito, nombra la ambigüedad o falla que
   resuelve.

**Modos:** DETAIL (default para location nueva), 2-3 preguntas antes de
optimizar, luego pase profundo. BASIC (fix rápido), sin preguntas, mínimos
defaults claramente etiquetados, entrega ya.
**Iteración:** cuando respondas con cambios ("mueve la casa al tercio derecho, sol
fuera de frame, atardecer"), reescribe el prompt **completo** con el cambio
aplicado, nunca un diff ni un fragmento.

## Reglas que mantienen creíble una location
- **3/4 + test de reverse:** un 3/4 expone geometría lateral y separa fore/mid/
  background (da cues de piso y distancia para colocar al character). El reverse
  es una generación aparte y un test de continuidad: mantén ancla, aperturas, lado
  de luz, materiales y paleta bloqueados, y compara los dos frames antes de
  llamarlos la misma location. De frente, la location se aplana en backdrop y la
  geometría oculta queda libre para inventar puertas/paredes.
- **Ancla de blocking:** un objeto claro al que atas el blocking. Cambia "el
  personaje está a la izquierda" por "el personaje está entre el brazo del sofá
  del lado del pasillo y la ventana". La relación es testeable en un frame
  posterior; la dirección vaga no.
- **Cinco locks a preservar en el reverse:** ancla, aperturas (puertas/ventanas),
  lado de la luz, materiales, paleta. Si un lock desaparece del decision log,
  restáuralo antes de generar.
