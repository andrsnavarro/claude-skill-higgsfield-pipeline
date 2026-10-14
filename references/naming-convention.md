# Naming, direcciones de Element

Un asset aprobado solo paga si lo puedes recuperar después. Un patrón fijo le da
a Claude la dirección exacta para cargar en un shot record, y a ti un nombre
predecible para seleccionar con el `@` picker de Cinema Studio.

## Qué es un asset
Cualquier pieza aprobada que reusarás entre planos: una location plate, un
character sheet, un prop. Subir su archivo desde la carpeta del proyecto
Claude crea el **Element** reusable en Higgsfield. El archivo local y el Element
son cosas distintas: un prompt posterior llama al Element por su nombre `@`
guardado.

## El patrón
`@<tipo>_<proyecto>_<descripción>`

| Prefijo | Nombra | Ejemplo |
|---|---|---|
| `@loc_` | Locations | `@loc_XX_house_front` |
| `@char_` | Characters | `@char_XX_hero` |
| `@prop_` | Props | `@prop_XX_phone` |

- El tag del medio es el **código de proyecto** (aquí `XX` es un ejemplo).
  **Acuerda tu código corto al kickoff** para que los nombres no colisionen entre
  films.
- La descripción va en `snake_case`: une palabras con guion bajo
  (`house_front`), nunca espacios ni guiones.
- La dirección final incluye `@`. Cinema Studio lo agrega al crear el Element;
  usa la dirección completa al referirte o seleccionar el Element después.

## Por qué importa
Sin el estándar, Claude puede referenciar el asset equivocado mientras tú buscas
a mano en el Elements picker o re-adjuntas media. Los segmentos de tipo y
proyecto hacen la recuperación confiable.
