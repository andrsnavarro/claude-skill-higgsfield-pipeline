# Naming, Element addresses

An approved asset only pays off if you can retrieve it later. A fixed pattern gives Claude the exact address to load into a shot record, and gives you a predictable name to select with Cinema Studio's `@` picker.

## What an asset is
Any approved piece you will reuse across shots, such as a location plate, a character sheet or a prop. Uploading its file from the project folder creates the reusable **Element** in Higgsfield. The local file and the Element are different things, and a later prompt calls the Element by its saved `@` name.

## The pattern
`@<type>_<project>_<description>`

| Prefix | Names | Example |
|---|---|---|
| `@loc_` | Locations | `@loc_XX_house_front` |
| `@char_` | Characters | `@char_XX_hero` |
| `@prop_` | Props | `@prop_XX_phone` |

- The middle tag is the **project code** (`XX` here is an example). **Agree your short code at kickoff** so names do not collide between films.
- The description uses `snake_case`, joining words with underscores (`house_front`), never spaces or hyphens.
- The final address includes the `@`. Cinema Studio adds it when creating the Element. Use the full address when referring to or selecting the Element later.

## Why it matters
Without the standard, Claude may reference the wrong asset while you search by hand in the Elements picker or re-attach media. The type and project segments make retrieval reliable.
