# Character sheets, construir uno que Seedance no rompa

Un character vive o muere por su character sheet: la imagen de referencia que
Seedance lee para saber quién es. **Seedance lo lee literalmente**, así que cada
falla en el sheet se vuelve falla en cada shot.

## El pipeline del character (siempre en este orden)
1. **Prompt** en el Prompt Box, descripción que Claude escribe (moodboard +
   descripción primero, luego una sola production prompt que empaca todos los
   ángulos en una generación).
2. **Generate**, un sheet: front completo, back completo, y retrato close-up
   dominante.
3. **Inspect**, revisa antes de que nada downstream lo toque (un rim light
   perdido, una cara que no calza, o piel plástica aquí sangra en cada shot).
4. **Edit enmascarado sobre el original**, arregla fallas con máscaras de
   Photoshop compuestas sobre el sheet original. **Nunca regeneres el sheet
   entero**, o deriva y mugre se acumulan.
5. **Test en Seedance** sobre una buena location, el test es la meta, no la
   generación.

## Qué modelo
- **Soul Cinema**, primera opción para generar characters.
- **Seedream 4.5**, también sirve; corre en paralelo.
- **AI Cast (Cinema Studio)**, herramienta de casting fuerte.
- **Nano Banana Pro**, solo para **editar** un sheet terminado, nunca generar.
- **GPT Image 2**, creatures y add-ons precisos; en piel humana oversharpea y
  slopea → mantenlo a un parche pequeño.

## Las reglas que hacen un sheet Seedance-proof
- **Fondo gris neutro profundo** (#3a3a3c). El blanco sangra y lava la location;
  el negro se come el detalle. Gris es el punto medio de oro.
- **Retrato dominante (25–30% del frame).** Sin un panel de cara autoritativo,
  Seedance carece de evidencia facial y la inventa distinta shot a shot.
- **Ángula el retrato:** ligeramente off-frontal lee el volumen de la cabeza al
  instante; o agrega un retrato 3/4 separado más chico.
- **Ojos nunca negros:** el color del iris debe leerse. Ojos crushed-black no dan
  info de luz → los tonos derivan entre generaciones.
- **Catchlight o ojos muertos:** siempre un glint en el ojo, como en un shoot.
- **Rompe la simetría:** las caras reales son simétricas pero nunca perfectas. El
  espejo perfecto lee como IA.
- **Sin look de 3D-game-render:** Seedance reconoce el mood de game model y anima
  al personaje como footage de juego.
- **Recorta la cabeza en los paneles de cuerpo entero:** en cuerpo entero la cara
  siempre distorsiona y deriva del retrato. Recórtala y Seedance se ve forzado a
  tomar la cara del panel retrato, donde están los píxeles y la precisión.
- **Identidad idéntica en todos los paneles:** misma cara, misma luz, mismo
  grading. Dos identidades en el sheet = deriva en el video.

## Plantilla de production (funciona en cualquier modelo)
Dos cosas nunca cambian: el fondo gris neutro profundo y el split en columnas con
un retrato dominante (agrega columnas si el personaje las necesita). El bloque
CHARACTER se reescribe con Claude para tu personaje. El prompt va en inglés.

```
Character reference sheet of a single consistent [female] character, presented
on a pure clean deep neutral grey (#3a3a3c) seamless studio background, clean
editorial layout arranged in three vertical sections, horizontal landscape
composition read left to right, identical character identity, lighting and color
grading across every panel for perfect consistency:
, COLUMN 1 (largest, leftmost): chest-up portrait, front view, head and upper
chest in frame, sharp focus on the eyes, soft catchlights in both eyes.
, COLUMN 2: full-body front view, standing relaxed neutral A-pose, arms slightly
away from the body, weight evenly distributed, full figure head-to-toe inside
the frame with even margins.
, COLUMN 3 (rightmost): full-body back view, same standing pose mirrored,
showing hair fall, back posture, garment fit and shoe heels.
CHARACTER (must remain identical in all panels): [woman, mid-20s, height ~175cm,
elegant proportions, oval face, sharp high cheekbones, defined but soft jawline,
straight nose, full natural lips, light scattered freckles across the nose and
cheeks, clear fair skin with realistic natural texture and subtle imperfections,
grey-green eyes with detailed iris, well-groomed natural brows, straight auburn
hair with a center part falling just past the shoulders with a soft natural
sheen, neutral calm relaxed expression].
LIGHTING & RENDER: clean soft even studio lighting, large diffused key light
with gentle fill, soft natural shadows, no harsh highlights, true-to-life skin
tones, neutral white balance, minimal high-fashion editorial presentation,
polished modern professional model sheet aesthetic, shot on full-frame camera
with an 85mm lens look, shallow yet controlled depth of field, crisp tack-sharp
detail, high dynamic range, 8k.
```
> Nota: en los paneles de cuerpo entero, recorta la cabeza después de generar
> (Photoshop) para forzar a Seedance a leer la cara desde el retrato.

## Cómo se ve un SLOP sheet (rechazar)
- **Dirty sheet:** plate mottled/sucia (de regenerar el sheet entero una y otra
  vez) + cara de cuerpo entero que no calza con el retrato → dos identidades.
- **Game render:** texturas plásticas de game model + rim light naranja horneado
  + retrato demasiado chico (lejos del 25–30%).
- **Nano Banana slop:** cara mirror-simétrica + piel soapy/waxy + seis tiles casi
  iguales sin retrato dominante.

En todos: **enmascara reparaciones sobre el original y vuelve a auditar.**

## Editar characters = cirugía
Cada cambio de Seedream/GPT Image 2/Nano Banana Pro va sobre el sheet original
con máscara: cambia solo la región que cambió, deja el original intacto en todo
lo demás. El archivo limpio queda como master; nada regenera encima.
