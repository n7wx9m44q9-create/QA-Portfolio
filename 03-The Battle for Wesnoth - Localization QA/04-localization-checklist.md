# Localization QA Checklist — The Battle for Wesnoth

## 1. Información del proyecto

- [ ] Producto: The Battle for Wesnoth
- [ ] Área bajo prueba: Campaña Tutorial
- [ ] Idioma origen: English
- [ ] Idioma destino: Spanish
- [ ] Versión del juego registrada
- [ ] Sistema operativo registrado
- [ ] Plataforma registrada
- [ ] Configuración inicial registrada

---

# 2. Configuración y persistencia del idioma

## Selección del idioma

- [ ] El juego permite seleccionar Español.
- [ ] La interfaz cambia correctamente al seleccionar Español.
- [ ] No quedan elementos inesperados en inglés después del cambio.
- [ ] Los textos principales del menú aparecen en español.

## Persistencia

- [ ] El idioma seleccionado permanece después de cerrar el juego.
- [ ] El idioma seleccionado permanece después de volver a iniciar el juego.
- [ ] El juego no revierte inesperadamente al idioma anterior.

## Cambio de idioma durante una sesión

- [ ] Es posible determinar si el idioma puede cambiarse durante una sesión.
- [ ] Cambiar de English → Spanish actualiza correctamente la interfaz.
- [ ] Cambiar de Spanish → English actualiza correctamente la interfaz.
- [ ] No quedan elementos de la interfaz en el idioma anterior.
- [ ] No quedan diálogos o textos previamente cargados en el idioma anterior.
- [ ] El cambio de idioma no provoca errores visuales.
- [ ] El cambio de idioma no provoca pérdida de progreso.
- [ ] El cambio de idioma no provoca comportamientos inesperados.

> Nota: estos puntos deben validarse primero de forma exploratoria.
> No asumir el comportamiento esperado hasta observar cómo funciona la versión bajo prueba.

---

# 3. Exploratory Testing — English

## Objetivo

Comprender el funcionamiento del Tutorial antes de evaluar su traducción.

- [ ] Identificar cómo se accede al Tutorial.
- [ ] Identificar el flujo completo del Tutorial.
- [ ] Identificar los escenarios incluidos.
- [ ] Identificar los personajes principales.
- [ ] Identificar las unidades introducidas.
- [ ] Identificar las mecánicas explicadas.
- [ ] Identificar los objetivos de cada escenario.
- [ ] Identificar las instrucciones mostradas al jugador.
- [ ] Identificar los diálogos.
- [ ] Identificar mensajes del sistema.
- [ ] Identificar ventanas y elementos de UI relacionados con el Tutorial.
- [ ] Identificar botones utilizados durante el Tutorial.
- [ ] Registrar eventos relevantes que modifiquen el flujo.
- [ ] Registrar qué comportamiento espera el juego después de cada instrucción.

## Registro de comportamiento

Para cada escenario:

- [ ] Registrar objetivo.
- [ ] Registrar acciones requeridas.
- [ ] Registrar unidades relevantes.
- [ ] Registrar instrucciones.
- [ ] Registrar diálogos.
- [ ] Registrar cambios de estado importantes.
- [ ] Registrar resultado esperado de las acciones.
- [ ] Registrar cualquier comportamiento que pueda ser relevante para validar la traducción.

---

# 4. Exploratory Testing — Spanish

Repetir el flujo observado durante la exploración en inglés.

- [ ] El Tutorial puede iniciarse correctamente en español.
- [ ] El flujo general coincide con el observado en inglés.
- [ ] Las instrucciones aparecen en los mismos momentos.
- [ ] Los diálogos aparecen en los mismos momentos.
- [ ] Los objetivos corresponden con los observados en inglés.
- [ ] Las acciones solicitadas corresponden con el comportamiento observado en inglés.
- [ ] No aparecen textos inesperadamente en inglés.
- [ ] No faltan textos presentes en inglés.
- [ ] No aparecen textos adicionales sin justificación.
- [ ] No existen diferencias funcionales aparentemente provocadas por la localización.

---

# 5. Exactitud de la traducción

Para cada texto relevante:

- [ ] El texto español transmite el significado del original.
- [ ] No existe pérdida de información.
- [ ] No existe información adicional no presente en el original.
- [ ] No se modifica el significado.
- [ ] No existen falsos amigos.
- [ ] No existen traducciones incorrectas de términos.
- [ ] Las referencias a personajes son correctas.
- [ ] Las referencias a unidades son correctas.
- [ ] Las referencias a lugares son correctas.
- [ ] Las instrucciones mantienen la intención original.

---

# 6. Gramática y ortografía

- [ ] Ortografía correcta.
- [ ] Tildes correctas.
- [ ] Concordancia de género correcta.
- [ ] Concordancia de número correcta.
- [ ] Concordancia verbal correcta.
- [ ] Uso correcto de artículos.
- [ ] Uso correcto de preposiciones.
- [ ] Tiempos verbales adecuados.
- [ ] Puntuación correcta.
- [ ] Signos de interrogación correctos.
- [ ] Signos de exclamación correctos.
- [ ] Uso correcto de mayúsculas.
- [ ] No existen errores tipográficos.

---

# 7. Registro y tratamiento del jugador

- [ ] El tratamiento del jugador es consistente.
- [ ] Se mantiene el uso de "tú" o "usted" según el criterio establecido.
- [ ] No existen cambios injustificados entre "tú" y "usted".
- [ ] Los posesivos son consistentes ("tu", "su", etc.).
- [ ] El tono de los diálogos es consistente.
- [ ] El tono de las instrucciones es consistente.
- [ ] El registro lingüístico corresponde al contexto del juego.

> Un cambio de "tú" a "usted" no se marcará automáticamente como bug.
> Primero se comprobará el contexto y el criterio utilizado en otros textos.

---

# 8. Consistencia terminológica

- [ ] Un mismo concepto mantiene la misma traducción cuando corresponde.
- [ ] Los nombres de unidades son consistentes.
- [ ] Los nombres de personajes son consistentes.
- [ ] Los nombres de lugares son consistentes.
- [ ] Los nombres de facciones son consistentes.
- [ ] Los términos relacionados con las mecánicas son consistentes.
- [ ] Los términos militares son consistentes.
- [ ] Los términos utilizados en instrucciones coinciden con los utilizados en la UI.
- [ ] Los nombres utilizados en diálogos coinciden con los nombres mostrados en la interfaz.
- [ ] No existen traducciones diferentes para un mismo concepto sin una justificación contextual.

---

# 9. Contexto de la traducción

- [ ] La traducción tiene sentido dentro del contexto del escenario.
- [ ] Las instrucciones corresponden con la situación del jugador.
- [ ] Las referencias espaciales son correctas.
- [ ] Las referencias temporales son correctas.
- [ ] Las referencias a unidades son correctas.
- [ ] Las referencias a acciones del jugador son correctas.
- [ ] Las referencias a elementos de la interfaz son correctas.
- [ ] La traducción permite comprender qué debe hacer el jugador.

---

# 10. UI Localization

- [ ] Todo el texto es visible.
- [ ] No existe texto truncado.
- [ ] No existe texto fuera de los contenedores.
- [ ] No existe superposición entre elementos.
- [ ] Los botones muestran el texto completo.
- [ ] Las etiquetas muestran el texto completo.
- [ ] Los cuadros de diálogo muestran el texto completo.
- [ ] Los saltos de línea son adecuados.
- [ ] No existen espacios excesivos o insuficientes provocados por la traducción.
- [ ] El texto mantiene una alineación adecuada.
- [ ] El tamaño del texto es adecuado.
- [ ] Los caracteres especiales se muestran correctamente.
- [ ] Las letras acentuadas se muestran correctamente.
- [ ] No aparecen caracteres corruptos.
- [ ] No aparecen símbolos inesperados.
- [ ] El texto no oculta información importante.
- [ ] La longitud del español no provoca problemas visuales.

---

# 11. Comparación English → Spanish

Para cada elemento relevante:

- [ ] Se identificó el texto original en inglés.
- [ ] Se identificó la traducción española.
- [ ] Se verificó el significado.
- [ ] Se verificó el contexto.
- [ ] Se verificó la terminología.
- [ ] Se verificó la consistencia con otras apariciones.
- [ ] Se verificó la presentación visual.
- [ ] Se determinó si la diferencia constituye un defecto o una preferencia lingüística.

---

# 12. Reproducibilidad

Antes de reportar un defecto:

- [ ] El problema puede reproducirse.
- [ ] Se conoce el escenario donde ocurre.
- [ ] Se conoce la secuencia de acciones necesaria.
- [ ] Se conoce el texto exacto que provoca o demuestra el problema.
- [ ] Se puede identificar el texto original en inglés.
- [ ] Se puede identificar el texto traducido al español.
- [ ] Se dispone de evidencia visual cuando sea relevante.
- [ ] Se verificó que el problema no es un evento aleatorio.
- [ ] Se verificó el problema al menos una segunda vez cuando sea posible.

---

# 13. Clasificación de hallazgos

## Translation

- [ ] Traducción incorrecta.
- [ ] Significado alterado.
- [ ] Información omitida.
- [ ] Información añadida.
- [ ] Traducción literal que altera el significado.

## Grammar / Linguistic

- [ ] Error gramatical.
- [ ] Error ortográfico.
- [ ] Error de puntuación.
- [ ] Error de concordancia.
- [ ] Uso inconsistente de registro.

## Consistency

- [ ] Terminología inconsistente.
- [ ] Nombre inconsistente.
- [ ] Tratamiento del jugador inconsistente.
- [ ] Traducción inconsistente del mismo concepto.

## UI Localization

- [ ] Texto truncado.
- [ ] Overflow.
- [ ] Superposición.
- [ ] Texto ilegible.
- [ ] Caracteres incorrectos.
- [ ] Problema de longitud.
- [ ] Problema de salto de línea.

## Context

- [ ] Traducción incorrecta según el contexto.
- [ ] Instrucción ambigua.
- [ ] Instrucción que no corresponde con la acción esperada.
- [ ] Referencia incorrecta a un elemento del juego.

---

# 14. Criterios para reportar un bug

Un hallazgo debe tener evidencia suficiente para demostrar que existe un defecto.

- [ ] El problema es objetivo y no solamente una preferencia personal.
- [ ] Existe una diferencia verificable entre comportamiento esperado y actual.
- [ ] El texto original proporciona contexto suficiente.
- [ ] La traducción puede compararse con el original.
- [ ] El problema puede reproducirse.
- [ ] Los pasos de reproducción están documentados.
- [ ] El resultado actual está documentado.
- [ ] El resultado esperado está documentado.
- [ ] Se dispone de captura cuando aporta evidencia.
- [ ] La severidad está justificada.

---

# 15. Elementos fuera del alcance

No incluir en la ejecución principal:

- [ ] Consejos aleatorios mostrados al iniciar el juego.
- [ ] Otras campañas.
- [ ] Multijugador.
- [ ] Editor de mapas.
- [ ] Add-ons.
- [ ] Contenido creado por usuarios.
- [ ] Otras plataformas.
- [ ] Otros idiomas.

Los hallazgos encontrados fuera del alcance pueden conservarse como
**observaciones exploratorias**, pero no forman parte del conjunto principal
de pruebas del proyecto.
