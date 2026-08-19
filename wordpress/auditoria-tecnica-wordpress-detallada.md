# Auditoría Técnica WordPress — Versión Detallada (Escaneo en Vivo)

**Sitio:** defensordelcontribuyente.cl (dominio principal, servicios., diagnostico.)
**Fecha:** 19 de agosto de 2026
**Versión:** v2 — profundiza [`auditoria-tecnica-wordpress-plugins-seguridad.md`](auditoria-tecnica-wordpress-plugins-seguridad.md) (v1, solo documental) con escaneo en vivo section-by-section, form-by-form, button-by-button de la home, las 10 páginas de servicio y los 7 posts de blog en canibalización, más el cruce contra los checklists de [`Guía 360° de Marketing Digital para Pymes`](../estrategia-360/guia-marketing-digital-360-pyme.md).
**Método:** descarga directa de HTML crudo vía HTTP GET (curl, sin ejecutar JavaScript, sin autenticación, sin pentesting) sobre 21 URLs públicas (home + 10 páginas de servicio + 7 posts de blog + 3 verificaciones de contenido no publicado). **Limitación de método:** al no ejecutar JavaScript, cualquier script inyectado en tiempo de ejecución por Google Tag Manager (incluido un eventual Meta Pixel disparado desde un tag de GTM) no aparece en este HTML aunque exista en producción real — se señala explícitamente en cada hallazgo donde esto es relevante.

v1 sigue vigente como línea base documental (inventario de plugins, panel de Wordfence, contenido del WXR). Este documento v2 no la reemplaza — la complementa con lo que solo un escaneo en vivo puede confirmar.

---

## 1. Home — section-by-section, form-by-form, button-by-button

**13 secciones**, en orden: header sticky → hero (H1 único: "Abogado tributario") → "Queremos que seas un EMPRESARIO exitoso" → "Efectos de un Problema Tributario" (6 riesgos) → "Las Claves para superar un Problema Tributario" → "Tienes DOS OPCIONES" → "Defensor del Contribuyente Contigo" → "Defensa Tributaria en Todo Chile" (carrusel de 12 ciudades) → "Entregamos Servicios adaptados a tus Necesidades" (carrusel de 6 servicios) → "Trabajamos para responder a tu CONFIANZA" (carrusel de 6 testimonios) → proceso de 3 pasos → banner final → footer. **No hay sección FAQ en la home.**

Además hay **9 popups de Elementor** en el DOM (invisibles hasta activarse): 2 formularios de contacto, 1 embed de Calendly, 6 popups de video-testimonio individuales, y **un popup ("Agendar Diagnóstico", id 2879, imagen `prueb-popups.webp`) restringido solo a usuarios logueados con rol administrator/editor/author/contributor** — invisible para cualquier visitante público, código muerto en producción (→ TASK-076).

### Formularios (4)

| Formulario | Disparador | Campos | RUT obligatorio |
|---|---|---|---|
| `emailForm` (post 2101) | Botón hero | Nombre, **RUT con deuda**, email, teléfono, mensaje, checkbox | **Sí** |
| `wsForm` (post 1995) | Botón/tooltip WhatsApp | Nombre, **RUT con deuda**, celular, email, mensaje, checkbox | **Sí** |
| `emailForm` (post 7791) | Popup adicional | Nombre, **RUT**, email, teléfono, consulta, checkbox | **Sí** |
| `floatForm` (post 7574) | Otro popup de chat | Nombre, WhatsApp, email, mensaje, checkbox | No (única excepción) |

Los 3 primeros piden RUT como campo obligatorio **en el primer contacto**, antes de cualquier evaluación del caso — contradice directamente el checklist de la Guía 360 ("Formulario de captación simplificado para tráfico frío, 2-3 campos máx.", Sección 4) y la propia recomendación ya escrita en el Alcance Técnico Landing (formulario corto sin RUT). El campo RUT es texto libre **sin validación de formato** (`type="text"`, sin `pattern`), a diferencia del teléfono que sí lo tiene.

Los 4 formularios llevan campos ocultos UTM (`utm_source/medium/campaign/content/keyword`) y `landing` — arquitectura de atribución vía **Elementor Pro Forms nativo**, no Cool FormKit (contradice ligeramente la expectativa inicial del inventario de plugins; Cool FormKit puede estar en uso en otras páginas, ver sección 2).

**Hallazgo de flujo**: el botón "WhatsApp" no es un link directo — el formulario `wsForm` se envía primero (5 campos + RUT + checkbox) y solo entonces un script arma la URL `wa.me/56957062518` y la abre. Es un formulario-filtro completo, no un atajo.

### Botones/CTA (23)

Patrón de nombres similares con destinos distintos: "Necesito ayuda para crecer" (hero) abre el formulario propio; "Necesito ayuda para Crecer" (sección Contigo) y "Agenda tu Diagnóstico" (banner final) tienen clase `agenda-general` y son interceptados por jQuery para abrir un **widget de Calendly** (`calendly.com/defensordelcontribuyente/reunion-diagnostico-tributario`) — un canal de agendamiento no documentado en ninguna auditoría anterior, que coexiste con los formularios de Elementor.

### Tracking (grep literal sobre HTML crudo)

| Cadena | Ocurrencias |
|---|---|
| `GTM-N7BQZZW` | 2 |
| `GTM-MQC692WV` | 2 |
| `gtag(` / `AW-593050363` | 3 / 2 |
| `fbq(`, `facebook.com/tr`, `connect.facebook.net`, ID `524558258682248`, "pixel" | **0 — todas** |

**Confirma la duplicidad de GTM ya conocida. Cero rastro de Meta Pixel en el HTML crudo** — ni el fbq(), ni el dominio, ni el ID. Sin plugin dedicado ni código hardcodeado visible, si el pixel dispara solo puede ser vía uno de los 2 contenedores GTM en tiempo de ejecución del navegador (no verificable con fetch estático) → **TASK-066**.

Tracker adicional confirmado: **Metricool** (`tracker.metricool.com/resources/be.js`), consistente con el plugin ya inventariado.

### Imágenes y H1

66 `&lt;img&gt;` en el HTML (WP Rocket duplica cada imagen entre placeholder lazy-load y `&lt;noscript&gt;`, ~33-34 imágenes únicas reales): **38 con `alt=""` vacío, 28 con alt no vacío**. **1 solo H1**: "Abogado tributario".

### Otros hallazgos de la home

- Enlace roto: tarjeta "Mario Fatigante" apunta a `http://ente.cl/...` (dominio ajeno) → **TASK-074**.
- Typo: "Recibimos tu **mensale**" en el popup de confirmación → **TASK-075**.
- Teléfono fijo del footer (`227121756`) y número de WhatsApp (`56957062518`) son distintos, sin explicación visible → **TASK-077**.
- `og:locale="es_ES"` en vez de `es_CL` pese a ser contenido 100% chileno.
- WordPress 6.8.8, Elementor 4.1.4/Pro 4.1.2 confirmados sin cambios (visibles en `?ver=` de los assets).

---

## 2. Las 10 páginas de servicio — inventario profundo

Metodología: BeautifulSoup + grep sobre HTML crudo de cada URL (más confiable que un fetch que convierte a Markdown, porque preserva atributos exactos).

### Hallazgo central: un tercer sistema de tracking no documentado, exclusivo de servicios.

| Subdominio | GTM-N7BQZZW | GTM-MQC692WV | AW-593050363 | **GT-NCHTQWQT (Site Kit)** | **facebook-domain-verification** |
|---|---|---|---|---|---|
| Dominio principal (7 páginas) | Sí | Sí | Sí | No | No |
| **servicios.** (2 páginas) | Sí | **No** | Sí (vía Site Kit) | **Sí** | **Sí** |
| **diagnostico.** (1 página) | **No** | **No** | **No** | No | No |

`GT-NCHTQWQT` es un Google tag unificado (formato GA4/Ads moderno) inyectado por el plugin **"Site Kit by Google 1.185.0"**, junto con `wp-consent-api` — ninguno de los dos aparece en el inventario de 21 plugins ya auditado, porque ese inventario cubrió solo el WordPress del dominio principal; `servicios.` corre una instalación de WordPress separada (ya sabíamos por DOC-09 que es WordPress 7.0.4, distinto de 6.8.8) con su propio set de plugins, nunca inventariado hasta ahora. La meta tag `facebook-domain-verification` (`content="iimhlddwy5nwohfw704lr32wysuez1"`) confirma una conexión real a Meta Business Manager a nivel de dominio — **no es lo mismo que un pixel disparando PageView**, pero es la primera evidencia técnica dura de alguna conexión Meta fuera del propio Ads Manager. Ninguna auditoría previa había detectado esto → **TASK-071**.

`diagnostico.` sigue confirmado con **cero tracking de cualquier tipo** — ni GTM, ni Google Ads, ni Meta, ni Site Kit. No aparece "Code Snippets"/"code-snippets" inyectando nada visible en el `head`/`body` renderizado de ninguna de las 10 páginas.

### Formularios por página (detalle, no solo conteo)

| # | URL | Formularios | Nota |
|---|---|---|---|
| 1 | `/cobranza-fiscal/` | 4 (2× emailForm con RUT, floatForm, emailForm con RUT) | Patrón estándar |
| 2 | `/prescripcion-tributaria/` | 4, mismo patrón | — |
| 3 | `/fiscalizacion-tributaria-citaciones-sii/` | 4, mismo patrón | — |
| 4 | `servicios./convenios-condonaciones/` | 3 | **7 campos** en el principal, con **2 campos de teléfono duplicados** (`telefono` y `field_4d5adf2`, mismo placeholder) → **TASK-078** |
| 5 | `/preguntas-frecuentes-prescripcion-tributaria/` | 4 (qaForm + floatForm + 2× emailForm) | 2 H1 en la página |
| 6 | `/preguntas-frecuentes-cobranza-fiscal/` | 4, mismo patrón | 2 H1; FAQ duplica contenido de `/cobranza-fiscal/` |
| 7 | `servicios./faq-convenios-condonaciones/` | 2 (la más liviana) | 2 H1 |
| 8 | `/casos-exito-tributario/` | 3 | 7 testimonios (H3), 2 H1 |
| 9 | `/casos-de-exito/` | 4, incluye `wsForm` con campo `rutWE` | 8 testimonios — **dos páginas de casos de éxito con contenido distinto compitiendo por el mismo tema** → **TASK-068** |
| 10 | `diagnostico.` (home) | **1**, único sin RUT | Ver detalle abajo |

Todos los formularios de contacto estándar (excepto `diagnostico.` y algunos `floatForm`) piden RUT obligatorio — mismo patrón que la home, refuerza **TASK-072**.

### `diagnostico.defensordelcontribuyente.cl` — el subdominio de mayor intención

Único formulario del ecosistema con **campo de carga de archivos** (`input type="file"`, `name="form_fields[documentos][]"`, requerido, acepta múltiples documentos) — nombre opcional, email requerido, sin RUT. Página con **equipo del estudio nombrado** (8 personas: Víctor San Martín, Álvaro Véjar, Claudia Torres, Patricio Ordenes, Francisco Daher, Renato Mateluna, Vanessa Montoya, Fabiana Arias) y 7 botones de video-testimonio.

**Sin H1** en toda la página (usa H3 como título principal: "El Diagnóstico de tu Deuda Comienza Aquí") → **TASK-079**. **Sin botón de WhatsApp.** **53 de 53 imágenes sin `alt` (100%)** → **TASK-070**, coherente con la ausencia total de tracking ya reportada — es, con distancia, la página menos cuidada técnicamente de todo el ecosistema pese a ser el punto de conversión de mayor intención (carga de documentos tributarios).

### Otros hallazgos transversales de las 10 páginas

- **Doble H1** confirmado en páginas 5, 6, 7, 8, 9 (bloque "Reunión ✅ [Servicio]" marcado como H1) → **TASK-069**, ya priorizado en DOC-09 pero nunca convertido en tarea de backlog hasta ahora.
- Imágenes sin `alt`: 45% (pág. 1), 42% (pág. 2), 46% (pág. 3), 27% (pág. 4, la mejor), 40-44% (FAQ), **75% (pág. 8, casos-exito-tributario)**, 23% (pág. 9), **100% (pág. 10, diagnostico.)** → **TASK-070**.
- Typo "profesinalismo" en un testimonio de `/casos-exito-tributario/` → **TASK-075**.
- Inconsistencia de capitalización de CTA ("Tu defensa aquí" / "Tu Defensa Aquí") en la página 3.
- Videos testimoniales de `diagnostico.` alojados indistintamente en `diagnostico.defensordelcontribuyente.cl/wp-content/...` y `defensordelcontribuyente.cl/wp-content/...` — sin patrón claro de por qué unos están en un dominio y otros en el otro.

---

## 3. Blog — canibalización confirmada en vivo, con datos que el WXR no tenía

### Grupo 1 — "Auditoría Tributaria del SII" (veredicto: canibalización confirmada)

Los 3 posts (1913/2021, 9505/2025, 9019/2026) recorren el mismo camino — qué es la auditoría → citación/requerimiento → cómo responder → plazos → consecuencias. El post 2026 (9019) se diferencia solo en formato (caso narrativo "Juan" + FAQ), no en tema. **Adyacencia confirmada en el índice del blog**: los posts 9019 y 9505 aparecen **consecutivos, en las posiciones 5 y 6 de 9**, en la primera pantalla de `/blog/` sin necesidad de clic — cualquier visitante los ve uno junto al otro, haciendo la duplicación evidente a simple vista.

### Grupo 2 — "Prescripción Tributaria" (veredicto: el caso más flagrante del sitio)

El post 7745 (2025) es **prácticamente un refrito del post 1302** (2020, el de mayor tráfico histórico real del sitio): mismo H1 casi literal ("¿Prescriben las Deudas Fiscales... en Chile?"), mismos H2 palabra por palabra ("Errores comunes que bloquean la prescripción", "¿Un diagnóstico de Prescripción reactiva la Cobranza Fiscal?"). Los posts 8302 y 9042 aportan algo más de diferenciación (guía de requisitos / Art. 200 específico) pero resuelven la misma intención de búsqueda. En el índice del blog, solo el post 1302 aparece en la carga inicial (carrusel "Lo más visto", posición #1); los otros 3 quedan tras el botón "Cargar más" (AJAX, no verificable por fetch estático) — la duplicación es menos visible a simple vista que en el Grupo 1, pero igual de real para Google, que indexa por URL, no por posición visual.

### Bug de Yoast (post 9097) — confirmado parcialmente corregido, no resuelto

| Campo | Valor real hoy | ¿Correcto? |
|---|---|---|
| `&lt;title&gt;` (lo que usa Google y la pestaña del navegador) | "Variable tributaria en operaciones..." | ❌ **Sigue incorrecto** |
| `og:title` (preview social) | "Cumplimiento tributario y contabilidad..." | ✅ Ya corregido |
| JSON-LD `headline` | "Cumplimiento tributario y contabilidad..." | ✅ Ya corregido |
| `&lt;h1&gt;` visible | "Cumplimiento tributario y contabilidad..." | ✅ Correcto |

Alguien corrigió el campo social (og:title) y el schema, pero **no el "SEO title" de Yoast**, que es exactamente el que Google usa en el snippet de búsqueda. WP-04 sigue siendo la tarea correcta, pero ahora se sabe con precisión qué campo específico falta tocar.

### Hallazgo nuevo no solicitado: meta description duplicada e inválida en los 7 posts

**Los 7 posts auditados tienen una segunda etiqueta `&lt;meta name="description"&gt;`** (HTML inválido — solo debe existir una), inyectada justo antes del generador de Elementor. En 3 de los 7 (posts 9505, 9019, 9042) esa segunda etiqueta contiene literalmente el texto del post 8302 ("La prescripción de deuda tributaria en Chile es un tema fundamental...") **pegado en posts de tema distinto** (dos de Auditoría SII, uno de Prescripción Art. 200) — señal de que estos posts se crearon duplicando una plantilla o post base sin limpiar el campo, probablemente la misma causa raíz que llevó a la canibalización de contenido en primer lugar → **TASK-073**.

### Verificación de contenido no público

Los 3 posts que no deberían ser públicos (`?p=9383` borrador, `?p=9452` y `?p=9668` en papelera) devuelven **404 directo sin redirección**, verificado con `curl -L`. No hay filtración de contenido no publicado.

---

## 4. Cruce contra la Guía 360° de Marketing Digital para Pymes

| Checklist de la guía (Sección 1 y 4) | Estado real confirmado hoy |
|---|---|
| "Un solo contenedor de Google Tag Manager (sin duplicados)" — Crítica | ❌ 2 contenedores confirmados en 8 de 11 páginas escaneadas |
| "Meta Pixel instalado en todo el sitio + evento Lead" — Crítica | ❌ Cero rastro en 11 páginas; solo una `facebook-domain-verification` en servicios. |
| "Formulario de captación simplificado para tráfico frío (2-3 campos máx.)" — Alta | ❌ RUT obligatorio de entrada en la mayoría de los formularios; 6-7 campos es lo estándar |
| "Un CTA principal, repetido 2-3 veces, con texto específico" — Alta | ⚠️ Parcial: hay variación de texto, pero destinos inconsistentes (mismo texto casi idéntico → destinos distintos: formulario vs. Calendly) |
| "Prueba social visible (testimonios con nombre/foto/resultado)" — Alta | ✅ Cumple — 6 testimonios en home, 7-8 en páginas de casos de éxito, varios en video |
| "Un solo `&lt;h1&gt;` por página, jerarquía sin saltos" — Alta (SEO) | ❌ Doble H1 en 5+ páginas; cero H1 en diagnostico. |
| "Datos estructurados (LocalBusiness, Service, FAQPage) sin errores" — Alta | ❌ Ausentes, ya priorizado en el Alcance SEO |

El patrón que más resalta del cruce: **el punto de mayor fricción de conversión (RUT obligatorio) es exactamente lo opuesto a lo que la propia guía interna recomienda como mejor práctica 2026**, y es sistemático en todo el ecosistema, no un detalle aislado de una sola página.

---

## 5. Matriz de riesgos — actualizada con hallazgos v2

Ver v1 (`auditoria-tecnica-wordpress-plugins-seguridad.md`, sección 7) para WPR-1 a WPR-8, todos vigentes sin cambios. Hallazgos nuevos de esta versión:

| ID | Hallazgo | Severidad | Confianza | Tarea |
|---|---|---|---|---|
| WPR-9 | Tercer sistema de tracking (Site Kit/GT-NCHTQWQT) no documentado en servicios. | Alto | Alta (confirmado en vivo) | TASK-071 |
| WPR-10 | RUT obligatorio en primer contacto, sistemático en todo el sitio | Medio-Alto | Alta | TASK-072 |
| WPR-11 | Meta description duplicada e inválida en 7/7 posts revisados, con contaminación cruzada de contenido en 3 | Medio | Alta | TASK-073 |
| WPR-12 | Bug de título Yoast (WP-04) solo parcialmente corregido — el campo SEO title sigue mal | Alto | Alta (confirmado en vivo) | WP-04 (revisar) |
| WPR-13 | Cero H1 en diagnostico., doble H1 en 5+ páginas | Medio | Alta | TASK-069, TASK-079 |
| WPR-14 | 100% imágenes sin alt en diagnostico. (53/53) | Medio | Alta | TASK-070 |
| WPR-15 | Dos páginas de casos de éxito con contenido distinto sobre el mismo tema | Bajo-Medio | Alta | TASK-068 |

## 6. Limitaciones de este escaneo

- Sin ejecución de JavaScript: cualquier tag inyectado dinámicamente por GTM (incluido un eventual Meta Pixel) no es detectable por este método — solo confirma su ausencia en el HTML servido, no en el navegador tras ejecutar scripts.
- No se auditó el listado completo de plugins de `servicios.` ni `diagnostico.` (WordPress separados) — solo se detectó tracking vía grep de HTML, no un inventario de plugins como el del dominio principal.
- La paginación AJAX del blog ("Cargar más") impide confirmar la posición exacta de los posts 1913, 7745, 8302 y 9042 en el índice más allá de la carga inicial.
- No se investigaron vulnerabilidades (CVE) — sigue pendiente de autorización expresa, sin cambios respecto a v1.
