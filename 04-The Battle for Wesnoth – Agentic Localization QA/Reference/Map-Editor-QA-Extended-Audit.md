# Auditoría extendida de calidad — Wesnoth Map Editor

## Resumen ejecutivo

Se revisaron sistemáticamente las **112 entradas vigentes que no estaban en el piloto** del catálogo `wesnoth-editor`. Se confirmaron **cinco defectos nuevos** (ME-004 a ME-008); ME-008 agrupa el mismo problema ortográfico en cuatro cadenas de ayuda. Dos cadenas quedan pendientes de criterio lingüístico humano. Las otras 102 entradas no presentaron un defecto identificable. Sumados a ME-001–ME-003, previamente validados, hay **ocho defectos confirmados** en total. Se agotó el catálogo fuera del piloto sin llegar a la meta de siete defectos nuevos; no se forzó ningún hallazgo.

## Alcance, versión e inventario

- **Juego/versión:** *The Battle for Wesnoth* 1.19.29.
- **Commit:** [`0e0c7174265d120d09455adfbcc4b0fd62a80433`](https://github.com/wesnoth/wesnoth/commit/0e0c7174265d120d09455adfbcc4b0fd62a80433).
- **Dominio/dirección:** solo `wesnoth-editor`, inglés → español (`es`).
- **Archivos de catálogo:** [`po/wesnoth-editor/es.po`](https://github.com/wesnoth/wesnoth/blob/0e0c7174265d120d09455adfbcc4b0fd62a80433/po/wesnoth-editor/es.po) y [`po/wesnoth-editor/wesnoth-editor.pot`](https://github.com/wesnoth/wesnoth/blob/0e0c7174265d120d09455adfbcc4b0fd62a80433/po/wesnoth-editor/wesnoth-editor.pot).

| Conteo | `es.po` | POT |
|---|---:|---:|
| Líneas físicas | 747 | 587 |
| Entradas vigentes, sin cabecera | 122 | 122 |
| Total de entradas del archivo (vigentes + obsoletas; sin cabecera) | 161 | 122 |
| Traducidas | 122 | No aplica (plantilla) |
| Vacías | 0 | 122 `msgstr` vacíos, como corresponde a una plantilla |
| `fuzzy` vigentes | 0 | 0 |
| Obsoletas | 39 | 0 |
| Obsoletas con marca `fuzzy` | 3 | 0 |
| Entradas del piloto previamente revisadas | 10 | — |
| Entradas únicas disponibles para la revisión nueva | 112 | — |

Las diez entradas del piloto se identificaron y excluyeron de la revisión nueva. Todas están entre las 122 entradas vigentes; quedan 112 únicas para esta fase. Las obsoletas se separaron de las vigentes; las tres obsoletas con marca `fuzzy` no se contaron como entradas traducidas o pendientes vigentes.

## Método y criterios

Se analizaron las entradas PO/POT respetando continuaciones de cadenas entrecomilladas y secuencias de escape; la cabecera no se contó como entrada. Para `es.po`, se consideró traducida una entrada vigente no `fuzzy` con valor `msgstr` no vacío. También se cotejaron placeholders, etiquetas de marcado y saltos de línea; las diferencias que requerían contexto se contrastaron con el código fuente del mismo commit. Se registraron las 112 entradas nuevas, incluidas las que no presentaron defectos. Las traducciones y los originales se reproducen literalmente en el registro.

ME-001, ME-002 y ME-003 se conservan como antecedentes ya validados y no se vuelven a contar como hallazgos nuevos. Para ME-002 queda adoptado `time schedule` → `planificación de fases horarias`.

## Nuevos defectos confirmados

### ME-004 — Terminología de `time-of-day`

- **Categoría/confianza:** terminología; alta.
- **Original:** `No editor time-of-day found.`
- **Traducción:** `No se encontraron datos de la «hora del día» para el editor.`
- **Ubicación:** [`po/wesnoth-editor/es.po:310–312`](https://github.com/wesnoth/wesnoth/blob/0e0c7174265d120d09455adfbcc4b0fd62a80433/po/wesnoth-editor/es.po#L310-L312); [`src/editor/controller/editor_controller.cpp:252–256`](https://github.com/wesnoth/wesnoth/blob/0e0c7174265d120d09455adfbcc4b0fd62a80433/src/editor/controller/editor_controller.cpp#L252-L256).
- **Evidencia e impacto:** el mensaje se muestra cuando `tods_` está vacío en el selector de tiempos del día del editor. La guía de español del proyecto fija `Time of Day` como `Tiempo del día`, mientras la traducción usa `hora del día`; eso puede confundirse con una hora del reloj. [Guía de traducción al español de Wesnoth](https://wiki.wesnoth.org/SpanishTranslation).
- **Corrección recomendada:** `El editor no tiene definido ningún tiempo del día.`
- **Incertidumbre:** la guía fija el término; la redacción propuesta conserva el sentido de la condición de código.

### ME-005 — Placeholder añadido en una etiqueta

- **Categoría/confianza:** integridad de placeholder; alta.
- **Original:** `Loaded referenced map file:`
- **Traducción:** `Archivo de mapa referenciado cargado:\n$new`
- **Ubicación:** [`po/wesnoth-editor/es.po:462–466`](https://github.com/wesnoth/wesnoth/blob/0e0c7174265d120d09455adfbcc4b0fd62a80433/po/wesnoth-editor/es.po#L462-L466); [`src/editor/map/context_manager.cpp:958–960`](https://github.com/wesnoth/wesnoth/blob/0e0c7174265d120d09455adfbcc4b0fd62a80433/src/editor/map/context_manager.cpp#L958-L960).
- **Evidencia e impacto:** el `msgid` no contiene `$new`; el código concatena explícitamente un salto de línea y el nombre real del archivo después de la etiqueta. El `msgstr` introduce `$new` sin valor asociado, por lo que puede mostrarse como texto literal y separar innecesariamente la ruta.
- **Corrección recomendada:** `Archivo de mapa referenciado cargado:`. El código añade la ruta por separado.
- **Incertidumbre:** ninguna sobre el placeholder; no se ejecutó el juego para comprobar la presentación visual final.

### ME-006 — Coma antes de la conjunción final

- **Categoría/confianza:** puntuación; alta.
- **Original:** `File does not have .map, .cfg, or .mask extension`
- **Traducción:** `El archivo no tiene extensión .map, .cfg, o .mask`
- **Ubicación:** [`po/wesnoth-editor/es.po:485–487`](https://github.com/wesnoth/wesnoth/blob/0e0c7174265d120d09455adfbcc4b0fd62a80433/po/wesnoth-editor/es.po#L485-L487); [`src/editor/map/map_context.cpp:199–205`](https://github.com/wesnoth/wesnoth/blob/0e0c7174265d120d09455adfbcc4b0fd62a80433/src/editor/map/map_context.cpp#L199-L205).
- **Evidencia e impacto:** es una enumeración simple de tres extensiones que se presenta al rechazar un archivo. La ortografía académica indica que normalmente no se escribe coma ante la conjunción que cierra una enumeración. [RAE, regla 4.2.1.3](https://www.rae.es/diccionario-estudiante/docs/ortografia.pdf).
- **Corrección recomendada:** `El archivo no tiene extensión .map, .cfg o .mask`.
- **Incertidumbre:** ninguna relevante; no hay incisos que justifiquen la coma.

### ME-007 — Concordancia de género en el identificador

- **Categoría/confianza:** gramática y claridad; alta.
- **Original:** `Invalid location id`
- **Traducción:** `Id de posición no válida`
- **Ubicación:** [`po/wesnoth-editor/es.po:566–568`](https://github.com/wesnoth/wesnoth/blob/0e0c7174265d120d09455adfbcc4b0fd62a80433/po/wesnoth-editor/es.po#L566-L568); [`src/editor/palette/location_palette.cpp:254–268`](https://github.com/wesnoth/wesnoth/blob/0e0c7174265d120d09455adfbcc4b0fd62a80433/src/editor/palette/location_palette.cpp#L254-L268). El catálogo emplea además el masculino en `Cambiar el ID de la unidad` ([líneas 322–328](https://github.com/wesnoth/wesnoth/blob/0e0c7174265d120d09455adfbcc4b0fd62a80433/po/wesnoth-editor/es.po#L322-L328)).
- **Evidencia e impacto:** el código muestra el mensaje cuando el identificador introducido para una posición del mapa no cumple el patrón admitido. El núcleo es `ID`/`identificador`, masculino; `no válida` concuerda con `posición` y desplaza la lectura hacia una posición inválida.
- **Corrección recomendada:** `ID de posición no válido` (o `Identificador de posición no válido`).
- **Incertidumbre:** ninguna relevante para el género del núcleo.

### ME-008 — Guion improcedente en `clic izquierdo`

- **Categoría/confianza:** ortografía y consistencia terminológica; alta.
- **Originales afectados:** `Left-click: `; `Right-click: `; `Shift + left-click: paint overlay layer only`; `Shift + left-click: paint base layer only`.
- **Traducciones existentes:** `Clic-izquierdo: `; `Clic-derecho: `; `Mayúsculas + clic-izquierdo: solo dibuja una capa superpuesta`; `Mayúsculas + clic-izquierdo: solo dibuja una capa base`.
- **Ubicación:** [`po/wesnoth-editor/es.po:574–591`](https://github.com/wesnoth/wesnoth/blob/0e0c7174265d120d09455adfbcc4b0fd62a80433/po/wesnoth-editor/es.po#L574-L591); [`src/editor/palette/terrain_palettes.cpp:221–232`](https://github.com/wesnoth/wesnoth/blob/0e0c7174265d120d09455adfbcc4b0fd62a80433/src/editor/palette/terrain_palettes.cpp#L221-L232).
- **Evidencia e impacto:** el código concatena estas cadenas en las instrucciones de ayuda de la paleta de terreno. La locución se escribe como grupo nominal `clic izquierdo/derecho`, sin guion; el mismo dominio ya usa `Clic izquierdo` y `Clic derecho` en la entrada del piloto, excluida de esta nueva revisión ([`es.po:551–552`](https://github.com/wesnoth/wesnoth/blob/0e0c7174265d120d09455adfbcc4b0fd62a80433/po/wesnoth-editor/es.po#L551-L552)). El guion en las cuatro cadenas rompe esa consistencia y ofrece una forma ortográfica no estándar.
- **Corrección recomendada:** `Clic izquierdo: `, `Clic derecho: ` y `Mayúsculas + clic izquierdo: ...`.
- **Incertidumbre:** ninguna sobre la forma coherente con el uso existente; no se evaluó el diseño visual en ejecución.

## Casos pendientes de criterio humano

| Registro | Entrada y ubicación | Motivo para no contarla como defecto confirmado |
|---|---|---|
| 031 | `Load Recent` → `Cargar reciente`; `es.po:186–189`, `data/themes/editor.cfg:72` | Es el título de un submenú con archivos recientes; la forma elíptica puede ser intencional en una etiqueta breve. Un revisor puede decidir si conviene explicitar «archivos». |
| 087 | `Map loaded from scenario` → `Mapa cargado desde escenario`; `es.po:457–460`, `src/editor/map/context_manager.cpp:957–960` | El título de estado omite el artículo antes de «escenario». Puede ser elipsis de interfaz; se deja a criterio lingüístico humano y no se contabiliza. |

## Registro completo de entradas nuevas revisadas

Las referencias de código son las incluidas en el catálogo del commit indicado. Cada fila corresponde a una entrada vigente distinta; las diez del piloto están excluidas.

| N.º | Ubicación PO | Referencia de fuente | Original (`msgid`) | Traducción (`msgstr`) | Resultado y explicación breve |
|---:|---|---|---|---|---|
| 001 | `es.po:28–31` | `data/core/editor/brushes.cfg:6` | `Single Hex` | `Un hexágono` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 002 | `es.po:33–36` | `data/core/editor/brushes.cfg:16` | `Radius 1 Hex` | `Hexágonos en radio 1` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 003 | `es.po:38–41` | `data/core/editor/brushes.cfg:26` | `Radius 2 Hex` | `Hexágonos en radio 2` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 004 | `es.po:48–51` | `data/core/editor/brushes.cfg:63` | `Hex Line SW-NE` | `Línea de hexágonos SO–NE` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 005 | `es.po:53–56` | `data/core/editor/terrain-groups.cfg:11` | `all` | `todo` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 006 | `es.po:58–61` | `data/core/editor/terrain-groups.cfg:17` | `water` | `agua` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 007 | `es.po:63–66` | `data/core/editor/terrain-groups.cfg:24` | `flat` | `llano` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 008 | `es.po:68–71` | `data/core/editor/terrain-groups.cfg:31` | `desert` | `desierto` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 009 | `es.po:73–76` | `data/core/editor/terrain-groups.cfg:38` | `embellishments` | `adornos` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 010 | `es.po:78–81` | `data/core/editor/terrain-groups.cfg:45` | `forest` | `bosque` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 011 | `es.po:83–86` | `data/core/editor/terrain-groups.cfg:52` | `fall` | `otoño` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 012 | `es.po:88–91` | `data/core/editor/terrain-groups.cfg:59` | `frozen` | `congelado` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 013 | `es.po:93–96` | `data/core/editor/terrain-groups.cfg:66` | `rough` | `abrupto` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 014 | `es.po:98–101` | `data/core/editor/terrain-groups.cfg:73` | `cave` | `caverna` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 015 | `es.po:103–106` | `data/core/editor/terrain-groups.cfg:80` | `obstacle` | `obstáculo` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 016 | `es.po:108–111` | `data/core/editor/terrain-groups.cfg:87` | `village` | `aldea` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 017 | `es.po:113–116` | `data/core/editor/terrain-groups.cfg:94` | `castle` | `castillo` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 018 | `es.po:118–121` | `data/core/editor/terrain-groups.cfg:101` | `bridge` | `puente` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 019 | `es.po:123–126` | `data/core/editor/terrain-groups.cfg:108` | `special` | `especial` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 020 | `es.po:128–131` | `data/core/editor/terrain-groups.cfg:115` | `elevation` | `elevación` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 021 | `es.po:133–137` | `data/core/editor/time-of-day.cfg:6` | `time of day^None` | `Ninguna` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 022 | `es.po:139–143` | `data/core/editor/time-of-day.cfg:11` | `Test` | `Experimental` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 023 | `es.po:145–148` | `data/core/editor/time-of-day.cfg:22` | `Default` | `Predeterminado` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 024 | `es.po:150–153` | `data/core/editor/time-of-day.cfg:28` | `Summer` | `Verano` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 025 | `es.po:155–158` | `data/core/editor/time-of-day.cfg:34` | `Winter` | `Invierno` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 026 | `es.po:160–163` | `data/core/editor/time-of-day.cfg:60` | `24 Hour Schedule` | `Horario de 24 horas` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 027 | `es.po:165–169` | `data/core/editor/time-of-day.cfg:66` | `After the Fall` | `Después de la Caída` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 028 | `es.po:171–174` | `data/internal/Urban_Jungle/terrain-groups.cfg:5` | `Urban Jungle (Internal)` | `Jungla urbana (interna)` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 029 | `es.po:176–179` | `data/themes/editor.cfg:11` | `theme^Editor` | `Editor` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 030 | `es.po:181–184` | `data/themes/editor.cfg:61` | `File` | `Archivo` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 031 | `es.po:186–189` | `data/themes/editor.cfg:72` | `Load Recent` | `Cargar reciente` | Pendiente — La etiqueta abre una lista de archivos recientes; `Cargar reciente` es elíptico y puede requerir decisión humana sobre si conviene explicitar el objeto o usar plural. |
| 032 | `es.po:191–194` | `data/themes/editor.cfg:80` | `Map` | `Mapa` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 033 | `es.po:196–199` | `data/themes/editor.cfg:88` | `Unit Facing` | `Orientación de la unidad` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 034 | `es.po:201–204` | `data/themes/editor.cfg:94` | `Transition Update` | `Actualización de transición` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 035 | `es.po:206–209` | `data/themes/editor.cfg:101` | `Window` | `Ventana` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 036 | `es.po:211–214` | `data/themes/editor.cfg:110` | `Add-on` | `Complemento` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 037 | `es.po:216–219` | `data/themes/editor.cfg:119` | `Areas` | `Áreas` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 038 | `es.po:221–224` | `data/themes/editor.cfg:127` | `Assign Local Time` | `Asignar fase horaria local` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 039 | `es.po:226–229` | `data/themes/editor.cfg:133` | `Assign Local Time Schedule` | `Asignar planificación de las fases horarias locales` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 040 | `es.po:231–234` | `data/themes/editor.cfg:141` | `Unit` | `Unidad` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 041 | `es.po:236–239` | `data/themes/editor.cfg:151` | `Side` | `Bando` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 042 | `es.po:241–244` | `data/themes/editor.cfg:168` | `villages` | `aldeas` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 043 | `es.po:246–249` | `data/themes/editor.cfg:184` | `units` | `unidades` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 044 | `es.po:251–254` | `data/themes/editor.cfg:479` | `Time Schedule Menu` | `Menú de planificación de fases horarias` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 045 | `es.po:256–259` | `data/themes/editor.cfg:489` | `Playlist` | `Lista de reproducción` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 046 | `es.po:261–264` | `data/themes/editor.cfg:495` | `Assign Time Schedule` | `Asignar la planificación de fases horarias` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 047 | `es.po:266–268` | `src/editor/action/mouse/mouse_action_unit.cpp:58` | `Identifier: ` | `Identificador: ` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 048 | `es.po:270–272` | `src/editor/action/mouse/mouse_action_unit.cpp:60` | `Name: ` | `Nombre: ` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 049 | `es.po:274–276` | `src/editor/action/mouse/mouse_action_unit.cpp:62` | `Type: ` | `Tipo: ` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 050 | `es.po:278–280` | `src/editor/action/mouse/mouse_action_unit.cpp:63` | `Level: ` | `Nivel: ` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 051 | `es.po:282–284` | `src/editor/action/mouse/mouse_action_unit.cpp:64` | `Cost: ` | `Coste: ` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 052 | `es.po:286–288` | `src/editor/controller/editor_controller.cpp:204` | `Fatal error` | `Error grave` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 053 | `es.po:290–292` | `src/editor/controller/editor_controller.cpp:234` | `Do you really want to quit?` | `¿Realmente desea salir?` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 054 | `es.po:294–300` | `src/editor/controller/editor_controller.cpp:236` | `Do you really want to quit? Changes to this map since the last save will be lost.` | `¿Realmente desea salir? Se perderán los cambios realizados en el mapa desde la última vez que guardó.` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 055 | `es.po:302–308` | `src/editor/controller/editor_controller.cpp:238` | `Do you really want to quit? The following maps were modified and all changes since the last save will be lost:` | `¿Realmente desea salir? Se perderán los cambios realizados en los siguientes mapas desde la última vez que los guardó:` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 056 | `es.po:310–312` | `src/editor/controller/editor_controller.cpp:255` | `No editor time-of-day found.` | `No se encontraron datos de la «hora del día» para el editor.` | Defecto confirmado (ME-004): la traducción no sigue el término del glosario del proyecto. |
| 057 | `es.po:314–316` | `src/editor/controller/editor_controller.cpp:886` | `Add-on Files` | `Archivos del complemento` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 058 | `es.po:318–320` | `src/editor/controller/editor_controller.cpp:899` | `Opening files is not supported, contact your packager` | `Abrir archivos no está soportado, contacte con su proveedor` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 059 | `es.po:322–324` | `src/editor/controller/editor_controller.cpp:1343` | `Change Unit ID` | `Cambiar el ID de la unidad` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 060 | `es.po:326–328` | `src/editor/controller/editor_controller.cpp:1344` | `ID:` | `ID:` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 061 | `es.po:330–332` | `src/editor/controller/editor_controller.cpp:1360` | `Rename Unit` | `Renombrar unidad` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 062 | `es.po:334–336` | `src/editor/controller/editor_controller.cpp:1361` | `Name:` | `Nombre:` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 063 | `es.po:342–344` | `src/editor/editor_display.cpp:172` | `<span color='red'><span face='DejaVuSans'>✘</span> $msg</span>` | `<span color='red'><span face='DejaVuSans'>✘</span> $msg</span>` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 064 | `es.po:346–348` | `src/editor/map/context_manager.cpp:217` | `Load Map or Scenario` | `Cargar mapa o escenario` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 065 | `es.po:350–352` | `src/editor/map/context_manager.cpp:313`<br>`src/editor/map/map_context.cpp:1141` | `New Map` | `Nuevo mapa` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 066 | `es.po:354–356` | `src/editor/map/context_manager.cpp:326`<br>`src/editor/map/map_context.cpp:1141` | `New Scenario` | `Nuevo escenario` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 067 | `es.po:358–360` | `src/editor/map/context_manager.cpp:371` | `No Recent Files` | `Sin archivos recientes` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 068 | `es.po:362–364` | `src/editor/map/context_manager.cpp:399` | `Unnamed Area` | `Área sin nombre` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 069 | `es.po:366–368` | `src/editor/map/context_manager.cpp:422` | `New Side` | `Nuevo bando` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 070 | `es.po:370–372` | `src/editor/map/context_manager.cpp:461` | `Apply Mask` | `Aplicar máscara` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 071 | `es.po:374–376` | `src/editor/map/context_manager.cpp:470` | `Error loading mask` | `Error al cargar la máscara` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 072 | `es.po:378–380` | `src/editor/map/context_manager.cpp:490` | `Identifier:` | `Identificador:` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 073 | `es.po:382–384` | `src/editor/map/context_manager.cpp:490` | `Rename Area` | `Renombrar área` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 074 | `es.po:386–388` | `src/editor/map/context_manager.cpp:504` | `Choose Target Map` | `Seleccionar mapa de destino` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 075 | `es.po:390–393` | `src/editor/map/context_manager.cpp:513`<br>`src/editor/map/context_manager.cpp:964` | `Error loading map` | `Error al cargar el mapa` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 076 | `es.po:399–403` | `src/editor/map/context_manager.cpp:704`<br>`src/editor/map/context_manager.cpp:753`<br>`src/editor/map/map_context.cpp:228`<br>`src/editor/palette/location_palette.cpp:263` | `Error` | `Error` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 077 | `es.po:405–407` | `src/editor/map/context_manager.cpp:705` | `Do you really want to save a map in the scenarios folder?` | `¿Realmente desea guardar un mapa en la carpeta de escenarios?` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 078 | `es.po:409–412` | `src/editor/map/context_manager.cpp:713`<br>`src/editor/map/context_manager.cpp:905` | `This map is already open.` | `Este mapa ya se encuentra abierto.` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 079 | `es.po:414–416` | `src/editor/map/context_manager.cpp:736` | `Save Scenario As` | `Guardar escenario como` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 080 | `es.po:422–424` | `src/editor/map/context_manager.cpp:762` | `This scenario is already open.` | `Este escenario ya se encuentra abierto.` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 081 | `es.po:426–428` | `src/editor/map/context_manager.cpp:779` | `No random map generators found.` | `No se encontraron generadores de mapas aleatorios.` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 082 | `es.po:430–433` | `src/editor/map/context_manager.cpp:792`<br>`src/editor/map/context_manager.cpp:797` | `Map creation failed.` | `Falló la creación del mapa.` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 083 | `es.po:435–437` | `src/editor/map/context_manager.cpp:812` | `Unsaved Changes` | `Cambios sin guardar` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 084 | `es.po:439–443` | `src/editor/map/context_manager.cpp:813` | `Do you want to discard all changes made to the map since the last save?` | `¿Desea descartar todos los cambios efectuados en el mapa desde que guardó por última vez?` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 085 | `es.po:445–447` | `src/editor/map/context_manager.cpp:866` | `Scenario saved.` | `Escenario guardado.` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 086 | `es.po:449–451` | `src/editor/map/context_manager.cpp:881` | `Map saved` | `Mapa guardado.` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 087 | `es.po:457–460` | `src/editor/map/context_manager.cpp:957`<br>`src/editor/map/context_manager.cpp:960` | `Map loaded from scenario` | `Mapa cargado desde escenario` | Pendiente — Título de estado: `desde escenario` omite el artículo que normalmente llevaría la frase en español; el contexto breve de interfaz deja margen para una forma elíptica. |
| 088 | `es.po:462–466` | `src/editor/map/context_manager.cpp:960` | `Loaded referenced map file:` | `Archivo de mapa referenciado cargado:\n$new` | Defecto confirmado (ME-005): añade un placeholder sin correspondencia ni valor. |
| 089 | `es.po:473–475` | `src/editor/map/editor_map.cpp:266` | `The size of the target map is different from the current map` | `El tamaño del mapa de destino difiere del mapa actual` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 090 | `es.po:477–479` | `src/editor/map/map_context.cpp:188` | `File not found` | `Archivo no encontrado` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 091 | `es.po:481–483` | `src/editor/map/map_context.cpp:195` | `Empty file` | `Archivo vacío` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 092 | `es.po:485–487` | `src/editor/map/map_context.cpp:204` | `File does not have .map, .cfg, or .mask extension` | `El archivo no tiene extensión .map, .cfg, o .mask` | Defecto confirmado (ME-006): coma innecesaria antes de «o» en enumeración simple. |
| 093 | `es.po:498–504` | `src/editor/map/map_context.cpp:253` | `The file looks like a scenario, but the map_data attribute does not point to an existing file` | `El archivo parece un escenario, pero el atributo map_data no apunta a un archivo existente.` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 094 | `es.po:506–512` | `src/editor/map/map_context.cpp:268` | `The file looks like a scenario, but the map_file attribute does not point to an existing file` | `El archivo parece un escenario, pero el atributo map_file no apunta a un archivo existente.` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 095 | `es.po:514–516` | `src/editor/map/map_context.cpp:448` | `Confirm` | `Confirmar` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 096 | `es.po:522–524` | `src/editor/map/map_context.cpp:869` | `Time schedule saved.` | `Fase horaria guardada.` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 097 | `es.po:526–528` | `src/editor/map/map_context.cpp:915` | `Could not save the scenario: $msg` | `No se pudo guardar el escenario: $msg` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 098 | `es.po:530–532` | `src/editor/map/map_context.cpp:946` | `Could not save into scenario` | `No se pudo guardar en el escenario` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 099 | `es.po:534–536` | `src/editor/map/map_context.cpp:956` | `Could not save the map: $msg` | `No se pudo guardar el mapa: $msg` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 100 | `es.po:538–540` | `src/editor/palette/editor_palettes.cpp:47` | `(Unknown Group)` | `(Grupo desconocido)` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 101 | `es.po:542–544` | `src/editor/palette/editor_palettes.cpp:300` | `(non-core)` | `(no principal)` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 102 | `es.po:546–548` | `src/editor/palette/editor_palettes.cpp:301` | `Will not work in game without extra care.` | `No funcionará en un juego sin atención adicional.` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 103 | `es.po:554–556` | `src/editor/palette/location_palette.cpp:247` | `Go To` | `Ir a` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 104 | `es.po:558–560` | `src/editor/palette/location_palette.cpp:254` | `Add` | `Añadir` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 105 | `es.po:562–564` | `src/editor/palette/location_palette.cpp:256` | `New Location Identifier` | `Nuevo identificador de posición` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 106 | `es.po:566–568` | `src/editor/palette/location_palette.cpp:264` | `Invalid location id` | `Id de posición no válida` | Defecto confirmado (ME-007): el adjetivo concuerda con «posición» y no con el núcleo `ID`. |
| 107 | `es.po:570–572` | `src/editor/palette/location_palette.cpp:271` | `Delete` | `Borrar` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |
| 108 | `es.po:574–576` | `src/editor/palette/terrain_palettes.cpp:224` | `Left-click: ` | `Clic-izquierdo: ` | Defecto confirmado (ME-008): guion no estándar frente a `clic izquierdo` en el uso del proyecto. |
| 109 | `es.po:578–580` | `src/editor/palette/terrain_palettes.cpp:225` | `Right-click: ` | `Clic-derecho: ` | Defecto confirmado (ME-008): guion no estándar frente a `clic derecho` en el uso del proyecto. |
| 110 | `es.po:582–587` | `src/editor/palette/terrain_palettes.cpp:230` | `Shift + left-click: paint overlay layer only` | `Mayúsculas + clic-izquierdo: solo dibuja una capa superpuesta` | Defecto confirmado (ME-008): mismo guion no estándar en `clic izquierdo`. |
| 111 | `es.po:589–591` | `src/editor/palette/terrain_palettes.cpp:232` | `Shift + left-click: paint base layer only` | `Mayúsculas + clic-izquierdo: solo dibuja una capa base` | Defecto confirmado (ME-008): mismo guion no estándar en `clic izquierdo`. |
| 112 | `es.po:593–595` | `src/editor/palette/terrain_palettes.cpp:235` | `Cmd + click: copy terrain` | `Cmd + clic: copia terreno` | Sin defecto identificado tras cotejar sentido, gramática y elementos técnicos. |

## Limitaciones y conclusión

La revisión fue estática: no se compiló ni ejecutó el juego, así que no se validaron recortes, disposición visual ni comportamiento en pantalla. El catálogo PO/POT está presente en el commit, pero sus fechas de metadatos son anteriores al snapshot (PO: 2026-03-04; POT: 2026-06-22); no se puede inferir que no haya habido cambios adicionales de traducción después de esas fechas. El código y las entradas revisadas se limitaron a `wesnoth-editor`; no se examinó ningún otro dominio.

Se completó la revisión de las 112 entradas restantes: cinco defectos nuevos confirmados y dos casos pendientes, para ocho defectos confirmados acumulados contando los tres antecedentes. La meta de siete defectos nuevos no se alcanzó y no debe suplirse artificialmente. Recomendación: someter ME-004–ME-008 y los dos pendientes a revisión humana de español y luego comprobar las correcciones propuestas en contexto de interfaz antes de autorizar otra fase.
