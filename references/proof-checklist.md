# Proof, no promesas, checklist de inspección

No apruebes una generación por el nombre del modelo ni por el prompt. Apruébala
por lo que se ve: qué cambió, qué se mantuvo, qué está roto. Un modelo fuerte
igual puede producir un resultado que no está listo.

## La vara (misma cada vez)
Antes de que algo llegue a Seedance, la fuente debe pasar:

- **Luz coherente:** una sola fuente creíble, sombras que caen consistentes en la
  dirección de la luz declarada. En interiores, fuentes suaves, los rayos duros
  visibles suelen ser slop.
- **Tonalidad con falloff suave:** sin sombras aplastadas (crushed) ni altas
  quemadas. Transición tonal real.
- **Material real:** superficies que leen como el material que dicen ser. Nada de
  textura aceitosa/soapy (nada a lo que agarrarse → se derrite en movimiento).
- **Profundidad / haze:** el haze atmosférico dice al ojo que un fondo está lejos.
  Sin él, todo lee con la misma nitidez → plano, slop inmediato.
- **Objetos completos:** nada medio formado, torcido o smeared (postes doblados,
  signage smeared, storefronts derretidos).

## Regla de comparación en edits
Todo lo que un edit cambia se **compara contra el original**:

1. ¿La **identidad** se sostiene? (silueta, anatomía, cara)
2. ¿Todas las **vistas concuerdan** (front/back/portrait)?
3. ¿El **cambio pedido** es consistente en todas partes?
4. ¿Cambió algo que **no** pediste? (layout, posición de figuras, un crop que se
   volvió dos, tinte global). Eso solo ya es motivo de HOLD.

## El veredicto depende del uso downstream
La misma imagen puede aprobarse o retenerse según lo que venga después. Ej.: un
sheet con armor coherente pero casco que tapa la cara → **procede** si solo
necesitas el diseño de armor; **hold** si tiene que llevar la cara al Seedance.
Siempre pregunto/defino para qué es el plano antes de dar el veredicto.

## Atajo del master wide (b-roll)
Cuando ningún corte depende de geometría exacta fuera de frame (b-roll, montaje,
cobertura de acción), una sola plate wide puede bastar. Mediums y close-ups
pueden inventar lo que la plate nunca mostró, usa el atajo solo cuando esa
invención no puede romper blocking ni continuidad.
