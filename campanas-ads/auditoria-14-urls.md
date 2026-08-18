# Auditoría técnica — 14 URL de campañas y recursos de conversión

**Sitio:** defensordelcontribuyente.cl (dominio principal, servicios. y diagnostico.)
**Fecha:** 17 de agosto de 2026
**Alcance:** páginas de servicio, FAQ, casos de éxito, blog y herramienta de diagnóstico usadas en campañas de Google Ads y otros canales.

## Resumen ejecutivo

Se auditaron **14 URL** en cuatro categorías (servicios, FAQ, casos de éxito, blog) más la herramienta de diagnóstico. Las 14 responden HTTP 200 — no hay enlaces rotos. El problema no es de disponibilidad: es de **medición** (Meta Pixel ausente en todas, tracking duplicado en 8, la herramienta de mayor intención sin ningún tracking) y de **fragmentación técnica** (tres versiones distintas de WordPress conviviendo en tres subdominios).

## Hallazgos transversales

**[CRÍTICO] Meta Pixel ausente en las 14 URL, sin excepción.**  
No se encontró fbq(), facebook.com/tr ni connect.facebook.net en ninguna de las páginas analizadas. Si alguna de estas URL recibe o va a recibir tráfico de Meta Ads, hoy no hay forma de medir conversiones ni construir públicos de remarketing.

**[CRÍTICO] La herramienta de diagnóstico (diagnostico.defensordelcontribuyente.cl) no tiene ningún tracking.**  
Es el punto de conversión de mayor intención del ecosistema — un formulario con carga de documentos tributarios — y no tiene contenedor de Google Tag Manager, tag de conversión de Google Ads, ni Meta Pixel. Cualquier campaña que la use como destino no está midiendo su resultado más importante.

**[CRÍTICO] Tres instalaciones de WordPress distintas, en tres versiones distintas.**  
Dominio principal (defensordelcontribuyente.cl): WordPress 6.8.8. Subdominio servicios.: WordPress 7.0.4. Subdominio diagnostico.: WordPress 6.7.5. Son sitios separados que se actualizan y mantienen de forma independiente — una corrección aplicada en uno no se propaga a los otros dos.

**[ALTO] Google Tag Manager duplicado en las 8 URL del dominio principal.**  
Mismo hallazgo que la auditoría de la home (GTM-N7BQZZW y GTM-MQC692WV activos a la vez), confirmado ahora en cobranza-fiscal, prescripcion-tributaria, fiscalizacion-tributaria-citaciones-sii, ambas FAQ del dominio principal, ambas páginas de casos de éxito y el post de blog del dominio principal. El subdominio servicios. no presenta esta duplicidad — corre un solo contenedor (GTM-N7BQZZW).

**[ALTO] Dos de las 14 URL están bloqueadas para buscadores (noindex, nofollow).**  
La FAQ de convenios y condonaciones (servicios.defensordelcontribuyente.cl/faq-convenios-condonaciones/) y la herramienta de diagnóstico. Ninguna de las dos apareció en las búsquedas de verificación en Google, consistente con el bloqueo. El de la herramienta puede ser intencional; el de la FAQ probablemente no debería estarlo si se espera que capture tráfico orgánico de búsquedas de preguntas frecuentes.

**[ALTO] Encabezado H1 duplicado en 8 de las 14 URL.**  
Un segundo H1 con el texto "Reunión ✅ [Servicio]" — que corresponde al bloque de agendamiento de reunión — aparece marcado como H1 además del título principal de la página. Debería bajar a H2 o H3; tener dos H1 diluye la señal de tema principal para buscadores.

**[MEDIO] Ninguna de las 3 páginas de preguntas frecuentes usa schema FAQPage.**  
Se pierde la posibilidad de que Google muestre un acordeón expandible de preguntas y respuestas directamente en el resultado de búsqueda — uno de los rich snippets más simples de implementar y con mejor tasa de clics para contenido de FAQ.

**[MEDIO] Las páginas de casos de éxito no usan schema Review ni AggregateRating.**  
Con testimonios reales disponibles (incluyendo los videos ya identificados en la home), agregar este schema es una oportunidad de mostrar estrellas de valoración directamente en el resultado de búsqueda.

**[MEDIO] Fragmentación de CSS confirmada en todo el sitio, no solo en la home.**  
Entre 37 y 46 hojas de estilo cargadas por separado en cada una de las páginas del dominio principal y de servicios. — mismo hallazgo de la auditoría SEO original, ahora verificado a nivel de sitio completo.

**[MEDIO] Imágenes sin texto alternativo: entre 29% y 100% según la página.**  
El promedio del grupo analizado es peor que el de la home (58%). Los casos más severos: la herramienta de diagnóstico (53 de 53 imágenes, 100% sin alt) y el post de blog sobre prescripción de deudas (73%).

**[INFO] El subdominio servicios. tiene una experiencia de conversión más limitada que el dominio principal.**  
Ninguna de sus 5 páginas analizadas tiene botón de WhatsApp, y sus formularios tienen menos variantes/campos (48-77 elementos de formulario) que las páginas equivalentes del dominio principal (100-102 elementos). Vale la pena confirmar si esto es una decisión deliberada o una brecha de implementación.

**[INFO] Dos posts de blog usan una URL de campaña con `?preview_id`, que no cambia el contenido pero cuesta ~14x en velocidad.**  
ml-condonaciones-convenios y perdonazo-tributario-2022 cargan en 1.5s con ese parámetro en la URL, frente a 0.1s de la versión limpia — el contenido servido es idéntico (mismo title, canonical, meta robots y H1), así que es un cambio de URL sin riesgo y de alto impacto en velocidad de carga por cada clic pagado.

## Detalle por URL

### 1. Servicio — campaña Ads

**URL:** https://defensordelcontribuyente.cl/cobranza-fiscal/

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | https://defensordelcontribuyente.cl/cobranza-fiscal/ |
| Google Tag Manager | GTM-MQC692WV, GTM-N7BQZZW |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |
| Title (60 car.) | Cobranza Fiscal ✅ Soluciones Legales para Deudas Tributarias |
| Meta description (122 car.) | Cobranza Fiscal: evita embargos y soluciona tus deudas con Tesorería. Recibe asesoría legal experta. Evalúa tu caso ahora. |
| H1 | 1 encontrado(s): Cobranza Fiscal: Soluciones para Deudas con Tesorería. |
| Schema encontrado | BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite |
| Formularios en la página | 4 |
| WhatsApp | Sí |
| Teléfono | 227121756 |
| Palabras (contenido visible) | 429 |
| Hojas de estilo CSS | 46 |
| Imágenes sin alt | 12 de 24 |
| WordPress | WordPress 6.8.8 |

**Notas específicas:**
- H1 único y correcto — no presenta el problema de doble H1 de otras páginas del sitio.
- Sin schema Service específico para este servicio (solo Organization/WebPage genérico).
- 50% de las imágenes (12 de 24) sin alt descriptivo.

### 2. Servicio — campaña Ads

**URL:** https://defensordelcontribuyente.cl/prescripcion-tributaria/

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | https://defensordelcontribuyente.cl/prescripcion-tributaria/ |
| Google Tag Manager | GTM-MQC692WV, GTM-N7BQZZW |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |
| Title (67 car.) | Prescripción tributaria en Chile: Evaluación legal y Representación |
| Meta description (132 car.) | Evaluación de deudas fiscales legalmente con ayuda de abogados tributarios. Consulta gratis con expertos en prescripción tributaria. |
| H1 | 1 encontrado(s): Prescripción Tributaria: Evaluación Legal y Representación Experta |
| Schema encontrado | BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite |
| Formularios en la página | 4 |
| WhatsApp | Sí |
| Teléfono | 227121756 |
| Palabras (contenido visible) | 482 |
| Hojas de estilo CSS | 46 |
| Imágenes sin alt | 12 de 26 |
| WordPress | WordPress 6.8.8 |

**Notas específicas:**
- H1 único y correcto.
- Sin schema Service específico.
- 46% de las imágenes (12 de 26) sin alt descriptivo.

### 3. Servicio — campaña Ads

**URL:** https://defensordelcontribuyente.cl/fiscalizacion-tributaria-citaciones-sii/

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | https://defensordelcontribuyente.cl/fiscalizacion-tributaria-citaciones-sii/ |
| Google Tag Manager | GTM-MQC692WV, GTM-N7BQZZW |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |
| Title (58 car.) | Fiscalización Tributaria y Citaciones del SII ✅ Defiéndete |
| Meta description (146 car.) | ¿Te notificó el SII? Aprende cómo enfrentar una Fiscalización Tributaria y responder citaciones sin multas ni sanciones. ¡Consulta con un experto! |
| H1 | 1 encontrado(s): Fiscalización Tributaria y Citaciones del SII. |
| Schema encontrado | BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite |
| Formularios en la página | 4 |
| WhatsApp | Sí |
| Teléfono | 227121756 |
| Palabras (contenido visible) | 745 |
| Hojas de estilo CSS | 45 |
| Imágenes sin alt | 18 de 37 |
| WordPress | WordPress 6.8.8 |

**Notas específicas:**
- H1 único y correcto.
- Es la página de servicio con más contenido (745 palabras) — coherente con ser el servicio más consultado en momentos de urgencia (citación del SII).
- 49% de las imágenes (18 de 37) sin alt descriptivo — la de mayor cantidad de imágenes del grupo de servicios.

### 4. Servicio — campaña Ads (subdominio servicios.)

**URL:** https://servicios.defensordelcontribuyente.cl/convenios-condonaciones/

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | https://servicios.defensordelcontribuyente.cl/convenios-condonaciones/ |
| Google Tag Manager | GTM-N7BQZZW |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |
| Title (61 car.) | Condonación de Deuda Fiscal | Reduce tu deuda con Tesorería ✅ |
| Meta description (125 car.) | Condonación de Deuda Fiscal: accede a facilidades de pago y reduce tu deuda con Tesorería. Evalúa tu caso con asesoría legal. |
| H1 | 1 encontrado(s): Condonación de Deuda Fiscal: Alivia tu carga tributaria |
| Schema encontrado | BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite |
| Formularios en la página | 3 |
| WhatsApp | No |
| Teléfono | 227121756 |
| Palabras (contenido visible) | 751 |
| Hojas de estilo CSS | 46 |
| Imágenes sin alt | 8 de 24 |
| WordPress | WordPress 7.0.4 |

**Notas específicas:**
- Corre sobre WordPress 7.0.4 — versión distinta a la del dominio principal (6.8.8). Instalación separada.
- Sin botón de WhatsApp — a diferencia de todas las páginas del dominio principal.
- Solo 1 contenedor de Google Tag Manager (GTM-N7BQZZW) — no presenta la duplicidad que sí afecta al dominio principal.
- 33% de las imágenes (8 de 24) sin alt — el mejor porcentaje de accesibilidad de imágenes de las 14 URL.

### 5. FAQ

**URL:** https://defensordelcontribuyente.cl/preguntas-frecuentes-prescripcion-tributaria/

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | https://defensordelcontribuyente.cl/preguntas-frecuentes-prescripcion-tributaria/ |
| Google Tag Manager | GTM-MQC692WV, GTM-N7BQZZW |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |
| Title (61 car.) | Preguntas Frecuentes sobre Prescripción Tributaria en Chile ✅ |
| Meta description (117 car.) | Resuelve tus dudas sobre cómo opera la prescripción tributaria en Chile: requisitos, plazos y procedimientos legales. |
| H1 | 2 encontrado(s) — duplicado: Preguntas Frecuentes sobre la Prescripción Tributaria en Chile / Reunión ✅ Prescripción Tributaria |
| Schema encontrado | BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite |
| Formularios en la página | 4 |
| WhatsApp | Sí |
| Teléfono | 227121756 |
| Palabras (contenido visible) | 696 |
| Hojas de estilo CSS | 39 |
| Imágenes sin alt | 6 de 12 |
| WordPress | WordPress 6.8.8 |

**Notas específicas:**
- Doble H1 en la página: el segundo ("Reunión ✅ Prescripción Tributaria") corresponde al bloque de agendamiento y debería bajar a H2 o H3.
- Sin schema FAQPage pese a ser una página de preguntas frecuentes — se pierde la posibilidad de aparecer con acordeón expandible en Google.
- 50% de las imágenes (6 de 12) sin alt.

### 6. FAQ

**URL:** https://defensordelcontribuyente.cl/preguntas-frecuentes-cobranza-fiscal/

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | https://defensordelcontribuyente.cl/preguntas-frecuentes-cobranza-fiscal/ |
| Google Tag Manager | GTM-MQC692WV, GTM-N7BQZZW |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |
| Title (53 car.) | Preguntas Frecuentes sobre Cobranza Fiscal en Chile ✅ |
| Meta description (136 car.) | Conoce las respuestas a las dudas más comunes sobre cobranza fiscal en Chile. Descubre qué hacer ante notificaciones o procesos del SII. |
| H1 | 2 encontrado(s) — duplicado: Preguntas Frecuentes sobre Cobranza Fiscal en Chile / Reunión ✅ Cobranza Fiscal |
| Schema encontrado | BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite |
| Formularios en la página | 4 |
| WhatsApp | Sí |
| Teléfono | 227121756 |
| Palabras (contenido visible) | 603 |
| Hojas de estilo CSS | 39 |
| Imágenes sin alt | 6 de 11 |
| WordPress | WordPress 6.8.8 |

**Notas específicas:**
- Mismo problema de doble H1 que la FAQ de prescripción.
- Sin schema FAQPage.
- 55% de las imágenes (6 de 11) sin alt.

### 7. FAQ (subdominio servicios.)

**URL:** https://servicios.defensordelcontribuyente.cl/faq-convenios-condonaciones/

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | NO (noindex, nofollow) |
| Canonical | Sin canonical |
| Google Tag Manager | GTM-N7BQZZW |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |
| Title (50 car.) | Resuelve tus dudas sobre Convenios y Condonaciones |
| Meta description (136 car.) | Conoce las dudas más comunes de personas que al igual que tú, quieren pagar sus deudas fiscales, pero sienten que merecen pagar lo justo |
| H1 | 2 encontrado(s) — duplicado: Preguntas Frecuentes / Reunión ✅ Convenios y Condonaciones |
| Schema encontrado | BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite |
| Formularios en la página | 2 |
| WhatsApp | No |
| Teléfono | 227121756 |
| Palabras (contenido visible) | 580 |
| Hojas de estilo CSS | 40 |
| Imágenes sin alt | 6 de 10 |
| WordPress | WordPress 7.0.4 |

**Notas específicas:**
- **Bloqueada para buscadores: `noindex, nofollow`, sin etiqueta canonical.** Es la única FAQ de las tres que no puede aparecer en Google — no se confirmó en las búsquedas de verificación, consistente con el bloqueo.
- Corre sobre WordPress 7.0.4 (instalación distinta al dominio principal).
- Sin botón de WhatsApp.
- Sin schema FAQPage (aplica igual que a las otras dos FAQ, aunque en este caso es secundario frente al noindex).
- 60% de las imágenes (6 de 10) sin alt.

### 8. Casos de éxito

**URL:** https://defensordelcontribuyente.cl/casos-exito-tributario/

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | https://defensordelcontribuyente.cl/casos-exito-tributario/ |
| Google Tag Manager | GTM-MQC692WV, GTM-N7BQZZW |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |
| Title (62 car.) | Casos de Éxito Tributario en Chile | Prescripción y Cobranza ✅ |
| Meta description (136 car.) | Testimonios reales sobre prescripción tributaria y cobranza fiscal en Chile. Conoce cómo asesorías profesionales marcaron la diferencia. |
| H1 | 2 encontrado(s) — duplicado: Clientes Felices  Comparten su Experiencia / Reunión ✅ Diagnóstico Tributario |
| Schema encontrado | BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite |
| Formularios en la página | 3 |
| WhatsApp | Sí |
| Teléfono | 227121756 |
| Palabras (contenido visible) | 650 |
| Hojas de estilo CSS | 37 |
| Imágenes sin alt | 20 de 26 |
| WordPress | WordPress 6.8.8 |

**Notas específicas:**
- Doble H1 (mismo patrón del bloque de agendamiento).
- Sin schema Review ni AggregateRating pese a ser una página de testimonios — oportunidad de rich snippet con estrellas en el resultado de búsqueda.
- 77% de las imágenes (20 de 26) sin alt — el peor porcentaje de accesibilidad entre las páginas de contenido (sin contar la herramienta de diagnóstico).

### 9. Casos de éxito

**URL:** https://defensordelcontribuyente.cl/casos-de-exito/

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | https://defensordelcontribuyente.cl/casos-de-exito/ |
| Google Tag Manager | GTM-MQC692WV, GTM-N7BQZZW |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |
| Title (45 car.) | Casos de éxito del Defensor del Contribuyente |
| Meta description (126 car.) | Descubre los casos de éxito del Defensor del Contribuyente y cómo nuestros clientes han logrado superar desafíos tributarios ✅ |
| H1 | 1 encontrado(s): Nuestros Casos de Éxito |
| Schema encontrado | BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite |
| Formularios en la página | 4 |
| WhatsApp | Sí |
| Teléfono | 227121756 |
| Palabras (contenido visible) | 410 |
| Hojas de estilo CSS | 44 |
| Imágenes sin alt | 8 de 28 |
| WordPress | WordPress 6.8.8 |

**Notas específicas:**
- H1 único y correcto.
- **Existen dos páginas de "casos de éxito" distintas y activas** (esta y casos-exito-tributario/) con títulos, meta description y estructura diferentes, apuntando al mismo tema. Vale la pena confirmar si ambas están en uso deliberado (ej. una para Ads y otra para SEO orgánico) o si una quedó duplicada por error — de no ser intencional, compiten entre sí por las mismas búsquedas.
- Sin schema Review/AggregateRating, igual que la otra página de casos de éxito.
- 29% de las imágenes (8 de 28) sin alt — buen porcentaje relativo.

### 10. Blog — recurso de campaña

**URL:** https://defensordelcontribuyente.cl/blog/prescriben-deudas-fiscales-chile/

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | https://defensordelcontribuyente.cl/blog/prescriben-deudas-fiscales-chile/ |
| Google Tag Manager | GTM-MQC692WV, GTM-N7BQZZW |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |
| Title (67 car.) | ¿Prescriben las Deudas Fiscales en Chile? | Prescripción Tributaria |
| Meta description (133 car.) | Conoce cómo funciona la prescripción tributaria en Chile, cuándo aplica y qué condiciones deben cumplirse según la normativa vigente. |
| H1 | 2 encontrado(s) — duplicado: ¿Prescriben las Deudas Fiscales en Chile? Conoce cómo funciona la Prescripción Tributaria / Reunión ✅ Prescripción Tributaria |
| Schema encontrado | Article, BreadcrumbList, CommentAction, EntryPoint, ImageObject, ListItem, Organization, Person, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite |
| Formularios en la página | 3 |
| WhatsApp | Sí |
| Teléfono | 227121756 |
| Palabras (contenido visible) | 1383 |
| Hojas de estilo CSS | 39 |
| Imágenes sin alt | 22 de 30 |
| WordPress | WordPress 6.8.8 |

**Notas específicas:**
- La URL de campaña incluye parámetros de tracking (`_gcl_au`, `_ga`, `_ga_V3QV7MTY5Q`) — confirma que este enlace ya se ha usado en clics reales de campañas pagadas o de Analytics.
- Doble H1 (mismo bloque de agendamiento).
- Correctamente usa schema Article y Person — el único grupo de URLs con esta cobertura (esperable, es contenido de blog).
- 73% de las imágenes (22 de 30) sin alt — la peor proporción de accesibilidad de imágenes del sitio.
- Es el contenido con el objetivo de búsqueda más directo ("¿prescriben las deudas fiscales?") frente a la keyword de interés del negocio.

### 11. Blog — recurso de campaña (subdominio servicios.)

**URL:** https://servicios.defensordelcontribuyente.cl/blog/ml-deudas-fiscales-cobranza-tesoreria/

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | https://servicios.defensordelcontribuyente.cl/blog/ml-deudas-fiscales-cobranza-tesoreria/ |
| Google Tag Manager | GTM-N7BQZZW |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |
| Title (54 car.) | ¿Deudas Fiscales? Aprende sobre la Cobranza Tributaria |
| Meta description (130 car.) | La cobranza fiscal se inicia con la notificación, requerimiento de pago y embargo realizado por la TGR. ✅ Conoce sus alcances Aquí |
| H1 | 2 encontrado(s) — duplicado: ¿Deudas Fiscales? Principales alcances a la cobranza realizada por la Tesorería General de la República / Reunión ✅ Cobranza Fiscal |
| Schema encontrado | Article, BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, Person, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite |
| Formularios en la página | 2 |
| WhatsApp | No |
| Teléfono | 227121756 |
| Palabras (contenido visible) | 1766 |
| Hojas de estilo CSS | 40 |
| Imágenes sin alt | 12 de 16 |
| WordPress | WordPress 7.0.4 |

**Notas específicas:**
- Corre sobre WordPress 7.0.4 (instalación distinta).
- Sin botón de WhatsApp.
- El contenido de mayor extensión de las 14 URL (1.766 palabras) — sólido en profundidad.
- 75% de las imágenes (12 de 16) sin alt.

### 12. Blog — recurso de campaña (subdominio servicios.)

**URL:** https://servicios.defensordelcontribuyente.cl/blog/ml-condonaciones-convenios/

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | https://servicios.defensordelcontribuyente.cl/blog/ml-condonaciones-convenios/ |
| Google Tag Manager | GTM-N7BQZZW |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |
| Title (57 car.) | Condonaciones de Intereses y Multas en Materia Tributaria |
| Meta description (128 car.) | Una simple mora o postergación en el pago de un impuesto pueda convertirse en una verdadera pesadilla. Conoce las Condonaciones. |
| H1 | 2 encontrado(s) — duplicado: Alcances a las Condonaciones de Intereses y Multas aplicables a impuestos en mora / Reunión ✅ Convenios y Condonaciones |
| Schema encontrado | Article, BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, Person, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite |
| Formularios en la página | 2 |
| WhatsApp | No |
| Teléfono | 227121756 |
| Palabras (contenido visible) | 1206 |
| Hojas de estilo CSS | 40 |
| Imágenes sin alt | 20 de 32 |
| WordPress | WordPress 7.0.4 |

**Notas específicas:**
- **La URL usada en la campaña lleva el parámetro `?preview_id` (sin valor).** El contenido es idéntico al de la URL limpia (mismo title, meta robots, canonical y H1) — no hay riesgo de mostrar contenido no publicado — pero al llevar ese parámetro, WordPress no sirve la página desde caché: **1.51s de carga frente a 0.11s de la URL limpia, ~14 veces más lenta en cada clic pagado.** Cambiar la URL de la campaña a la versión sin parámetros es la corrección de mayor impacto de este análisis.
- Corre sobre WordPress 7.0.4.
- Sin botón de WhatsApp.
- 63% de las imágenes (20 de 32) sin alt.

### 13. Blog — recurso de campaña (subdominio servicios.)

**URL:** https://servicios.defensordelcontribuyente.cl/blog/perdonazo-tributario-2022/

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | https://servicios.defensordelcontribuyente.cl/blog/perdonazo-tributario-2022/ |
| Google Tag Manager | GTM-N7BQZZW |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |
| Title (56 car.) | Perdonazo Tributario 2022 ¿Es para ti? 🤔 Descúbrelo aquí |
| Meta description (114 car.) | Conoce las claves para acceder al Perdonazo Tributario 2022. Te contamos cómo funciona y a quienes está dirigido ✅ |
| H1 | 2 encontrado(s) — duplicado: Nuevo &#8220;Perdonazo&#8221; Tributario 2022. Proyecto de Ley Boletín N° 15239-03. / Reunión ✅ Convenios y Condonaciones |
| Schema encontrado | Article, BreadcrumbList, CommentAction, EntryPoint, ImageObject, ListItem, Organization, Person, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite |
| Formularios en la página | 2 |
| WhatsApp | No |
| Teléfono | 227121756 |
| Palabras (contenido visible) | 1097 |
| Hojas de estilo CSS | 39 |
| Imágenes sin alt | 10 de 14 |
| WordPress | WordPress 7.0.4 |

**Notas específicas:**
- Mismo problema que el anterior: la URL de campaña lleva `?preview_id` y pierde el caché — 1.53s frente a 0.12s de la versión limpia.
- El título hace referencia a "2022" y a un Boletín de ley específico — vale la pena confirmar con el equipo legal si esa normativa sigue vigente tal cual está descrita; si cambió, es contenido desactualizado que un anuncio activo estaría promoviendo.
- 71% de las imágenes (10 de 14) sin alt.

### 14. Herramienta de diagnóstico y evaluación

**URL:** https://diagnostico.defensordelcontribuyente.cl/

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | NO (noindex, nofollow) |
| Canonical | Sin canonical |
| Google Tag Manager | Ninguno |
| Conversión Google Ads | No |
| Meta Pixel | No |
| Title (64 car.) | Diagnóstico Tributario por Expertos - Defensor del Contribuyente |
| Meta description (133 car.) | Es hora de conocer tus opciones y tomar el control de tu futuro. Descarga y envía tu información fiscal para que analicemos tu deuda. |
| H1 | 0 encontrado(s) — falta: — |
| Schema encontrado | BreadcrumbList, EntryPoint, ImageObject, ListItem, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite |
| Formularios en la página | 1 |
| WhatsApp | No |
| Teléfono | 227121756 |
| Palabras (contenido visible) | 1002 |
| Hojas de estilo CSS | 20 |
| Imágenes sin alt | 53 de 53 |
| WordPress | WordPress 6.7.5 |

**Notas específicas:**
- **Sin ningún tracking: cero contenedores de Google Tag Manager, sin tag de conversión de Google Ads, sin Meta Pixel.** Es la herramienta central de captación (formulario con carga de documentos: nombre, email, mensaje, dos campos de archivo y aceptación de términos) y hoy no queda registro de una sola conversión completada.
- **`noindex, nofollow`, sin canonical** — no se encontró en las búsquedas de verificación, consistente con el bloqueo. Puede ser intencional al ser una herramienta y no contenido, pero vale la pena confirmarlo explícitamente.
- **Sin ningún H1 en la página** — 0 encontrados. Rompe la jerarquía de encabezados que si tiene el resto del sitio.
- **Las 53 imágenes de la página tienen el atributo alt vacío — 0% con texto descriptivo.** El peor resultado de accesibilidad de las 14 URL analizadas.
- Corre sobre WordPress 6.7.5 — la tercera versión de WordPress distinta encontrada en el ecosistema (dominio principal 6.8.8, servicios. 7.0.4, diagnóstico. 6.7.5).
- Es la página más pesada del análisis (329 KB) y con más hojas de estilo después de los servicios (20 archivos CSS separados).

## Metodología y limitaciones

- Datos obtenidos por descarga directa del HTML público de cada URL (sin autenticación) y verificación cruzada de indexación mediante búsqueda web.
- La verificación de indexación en Google es orientativa (no equivale a una consulta directa a Google Search Console); se usa como señal adicional, no como fuente única.
- No se tuvo acceso a Google Search Console, Google Analytics ni al Administrador de Eventos de Meta — por lo tanto no se reportan cifras de tráfico real, solo la presencia o ausencia de la instrumentación necesaria para medirlo.
- El conteo de palabras es aproximado (texto visible, sin scripts ni estilos).
