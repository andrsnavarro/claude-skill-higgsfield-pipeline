# Elegir el modelo de imagen

No hay un "mejor" modelo permanente. Trata estos como los candidatos de hoy y
elige por el **no-negociable del plano**. Si el roster cambia, repite el test de
evidencia sobre el shot, no arrastres el ranking de hoy.

## La regla de decisión
Antes de cada pase de location o character, **nombra un requisito must-preserve**.
Inspecciona la salida en su crop real:
- Location → atmósfera, textura de material, objetos ancla.
- Character → identidad, piel, pose, gradientes.

Elige el modelo que **prueba** el must-preserve y deja solo fallas que puedas
re-correr o reparar con máscara.

## Candidatos

**Soul Cinema**, candidato *from-scratch* cuando la textura y atmósfera
cinemática importan más que el control exacto de objetos.
- A favor: luz lateral rasante que mantiene materiales táctiles; haze que crea
  profundidad; ángulos/color/luz creativos para exploración de locations; piel y
  ropa realistas para character sheets desde cero; maneja prompts cortos y largos.
- Puede descartarlo: variación creativa → una composición exacta puede tomar
  varias corridas; props/monstruos/creatures son fit más débil; puede reelaborar
  una imagen pero **no** adjuntar múltiples referencias ni editar una imagen
  terminada.
- Primera opción también para **generar characters**.

**GPT Image 2**, candidato de *control*: texto legible, geometría de props,
detalle fino, reverse angles y edits guiados por referencia.
- A favor: mantiene geometría de cuerpo/objeto consistente entre vistas (pasa el
  reverse-angle test); stickers y labels legibles y bien ubicados; detalle
  mecánico complejo con escala/proporción consistente; desgaste de material
  convincente.
- Puede descartarlo: **oversharpen en piel humana → slop** (es el modelo de
  *creatures*, no de humanos); halos duros en bordes, todo en foco sin
  separación de planos, balance de blancos cálido/amarillo, materiales plásticos.
- Úsalo para una **adición precisa** sobre un character existente (parche
  pequeño), texto, o geometría exacta.

**Nano Banana Pro**, candidato de *edit* cuando una imagen terminada necesita un
cambio audaz de vestuario/cara/objeto y aterrizar el cambio importa más que todo.
- A favor: un re-dress amplio aterriza coherente entre vistas; sirve también para
  monstruos/creatures; puede adjuntar una imagen terminada para editar.
- Puede descartarlo: los edits pueden tintar toda la imagen y dañar gradientes
  (**enmascara solo la región cambiada** sobre el original); caras descubiertas
  quedan simétricas y sin vida; locations from-scratch salen centradas y stock.
  **Nunca para arrancar una location o un hero character desde cero.**

**Seedream 4.5**, candidato de *edit de character sheet* cuando preservar textura
de piel y ropa importa más que la pose exacta o aterrizar cada detalle pedido.
- A favor: mantiene detalle fino de armor/ropa entre vistas; sobreviven pecas,
  poros y detalle de ojos; evita el look "banana" u oversharpen.
- Puede descartarlo: puede shiftear pose/ángulo (requiere mask-and-composite más
  largo); puede preservar textura pero **perder parte del cambio pedido**.
  Compáralo con Nano Banana Pro cuando aterrizar cada cambio es el mayor riesgo.
- Corre en batches paralelos y toma el resultado más limpio.

**AI Cast (Cinema Studio)**, herramienta de casting fuerte, vale explorarla para
characters.

## Edición: corre modelos en paralelo
Para editar (locations o characters) no eliges uno: corres GPT Image 2 / Nano
Banana Pro / Seedream 4.5 en paralelo y tomas el mejor resultado por cambio.
Todo edit se **compone sobre el original con máscara de Photoshop**, solo la
región que cambió; el resto intacto. Cada edit re-renderiza toda la imagen, así
que regenerar el sheet entero acumula deriva y mugre.
