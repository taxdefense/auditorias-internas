# Auditoría Técnica Completa — 14 URL de Campañas y Recursos de Conversión

**Sitio:** defensordelcontribuyente.cl (dominio principal, servicios. y diagnostico.)  
**Fecha auditoría técnica base:** 17 de agosto de 2026  
**Fecha complemento Lighthouse:** 18 de agosto de 2026  
**Alcance:** páginas de servicio, FAQ, casos de éxito, blog y herramienta de diagnóstico usadas en campañas de Google Ads y otros canales, complementadas con auditoría Lighthouse (rendimiento, accesibilidad, buenas prácticas, SEO, visibilidad para IA) por cada URL.

## Resumen ejecutivo

Se auditaron 14 URL en cuatro categorías (servicios, FAQ, casos de éxito, blog) más la herramienta de diagnóstico. Las 14 responden HTTP 200 — no hay enlaces rotos. El problema no es de disponibilidad: es de medición (Meta Pixel ausente en todas, tracking duplicado en 8, la herramienta de mayor intención sin ningún tracking), de fragmentación técnica (tres versiones distintas de WordPress conviviendo en tres subdominios) y, según el complemento Lighthouse, de **rendimiento real de carga** en varias páginas de servicio y en la herramienta de diagnóstico.

**Promedios Lighthouse del grupo (14 URL):**

| Categoría | Promedio |
|---|---|
| Rendimiento | 75/100 |
| Accesibilidad | 87/100 |
| Buenas prácticas | 84/100 |
| SEO | 95/100 |
| Visibilidad IA | 42/100 |

**Peor rendimiento de carga (top 3, más urgente para campañas pagadas):**
- https://defensordelcontribuyente.cl/preguntas-frecuentes-prescripcion-tributaria/ — Rendimiento 59/100
- https://defensordelcontribuyente.cl/preguntas-frecuentes-cobranza-fiscal/ — Rendimiento 59/100
- https://defensordelcontribuyente.cl/cobranza-fiscal/ — Rendimiento 61/100

## Hallazgos transversales (auditoría técnica base)

**[CRÍTICO] Meta Pixel ausente en las 14 URL, sin excepción.**  
No se encontró fbq(), facebook.com/tr ni connect.facebook.net en ninguna página. Si alguna de estas URL recibe o va a recibir tráfico de Meta Ads, hoy no hay forma de medir conversiones ni construir públicos de remarketing.

**[CRÍTICO] La herramienta de diagnóstico (diagnostico.defensordelcontribuyente.cl) no tiene ningún tracking.**  
Es el punto de conversión de mayor intención del ecosistema — un formulario con carga de documentos tributarios — y no tiene GTM, tag de conversión de Google Ads, ni Meta Pixel. Cualquier campaña que la use como destino no está midiendo su resultado más importante.

**[CRÍTICO] Tres instalaciones de WordPress distintas, en tres versiones distintas.**  
Dominio principal: WordPress 6.8.8. Subdominio servicios.: WordPress 7.0.4. Subdominio diagnostico.: WordPress 6.7.5. Son sitios separados que se actualizan y mantienen de forma independiente — una corrección aplicada en uno no se propaga a los otros dos.

**[ALTO] Google Tag Manager duplicado en las 8 URL del dominio principal.**  
GTM-N7BQZZW y GTM-MQC692WV activos a la vez, confirmado en cobranza-fiscal, prescripcion-tributaria, fiscalizacion-tributaria-citaciones-sii, ambas FAQ del dominio principal, ambas páginas de casos de éxito y el post de blog del dominio principal. El subdominio servicios. no presenta esta duplicidad.

**[ALTO] Dos de las 14 URL están bloqueadas para buscadores (noindex, nofollow).**  
La FAQ de convenios y condonaciones (servicios.) y la herramienta de diagnóstico. Ninguna apareció en las búsquedas de verificación. El de la herramienta puede ser intencional; el de la FAQ probablemente no debería estarlo si se espera capturar tráfico orgánico.

**[ALTO] Encabezado H1 duplicado en 8 de las 14 URL.**  
Un segundo H1 con el texto "Reunión ✅ [Servicio]" (bloque de agendamiento) aparece marcado como H1 además del título principal. Debería bajar a H2 o H3 — dos H1 diluyen la señal de tema principal para buscadores.

**[MEDIO] Ninguna de las 3 páginas de FAQ usa schema FAQPage.**  
Se pierde la posibilidad de un acordeón expandible de preguntas y respuestas en el resultado de búsqueda — uno de los rich snippets más simples de implementar y con mejor tasa de clics para contenido de FAQ.

**[MEDIO] Las páginas de casos de éxito no usan schema Review ni AggregateRating.**  
Con testimonios reales disponibles, agregar este schema es una oportunidad de mostrar estrellas de valoración directamente en el resultado de búsqueda.

**[MEDIO] Fragmentación de CSS confirmada en todo el sitio, no solo en la home.**  
Entre 37 y 46 hojas de estilo cargadas por separado en cada página del dominio principal y de servicios. — mismo hallazgo de la auditoría SEO original, ahora verificado a nivel de sitio completo.

**[MEDIO] Imágenes sin texto alternativo: entre 29% y 100% según la página.**  
El promedio del grupo es peor que el de la home (58%). Casos más severos: la herramienta de diagnóstico (100% sin alt) y el post sobre prescripción de deudas (73%).

**[INFO] El subdominio servicios. tiene una experiencia de conversión más limitada que el dominio principal.**  
Ninguna de sus 5 páginas tiene botón de WhatsApp, y sus formularios tienen menos campos (48-77 elementos) que las páginas equivalentes del dominio principal (100-102 elementos). Confirmar si es deliberado.

**[INFO] Dos posts de blog usan una URL de campaña con `?preview_id`, que no cambia el contenido pero cuesta ~14x en velocidad.**  
ml-condonaciones-convenios y perdonazo-tributario-2022 cargan en 1.5s con ese parámetro, frente a 0.1s de la versión limpia — el contenido es idéntico, así que es un cambio de URL sin riesgo y de alto impacto en velocidad por cada clic pagado.

## Tabla resumen — Lighthouse por URL

| # | Categoría | Rendimiento | Accesibilidad | Buenas prácticas | SEO | Visibilidad IA |
|---|---|---|---|---|---|---|
| 1 | Servicio — campaña Ads | 61 | 88 | 73 | 100 | 33 |
| 2 | Servicio — campaña Ads | 65 | 88 | 73 | 100 | 33 |
| 3 | Servicio — campaña Ads | 61 | 88 | 73 | 100 | 33 |
| 4 | Servicio — campaña Ads (subdominio servicios.) | 93 | 90 | 100 | 100 | 50 |
| 5 | FAQ | 59 | 83 | 73 | 100 | 33 |
| 6 | FAQ | 59 | 83 | 73 | 100 | 33 |
| 7 | FAQ (subdominio servicios.) — contenido desactualizado, modificación pendiente | 88 | 77 | 100 | 66 | 50 |
| 8 | Casos de éxito | 74 | 83 | 73 | 100 | 33 |
| 9 | Casos de éxito | 75 | 86 | 73 | 100 | 33 |
| 10 | Blog — recurso de campaña | 74 | 91 | 73 | 100 | 33 |
| 11 | Blog — recurso de campaña (subdominio servicios.) | 83 | 87 | 96 | 100 | 49 |
| 12 | Blog — recurso de campaña (subdominio servicios.) — contenido desactualizado, modificación pendiente | 69 | 87 | 96 | 100 | 30 |
| 13 | Blog — recurso de campaña (subdominio servicios.) — contenido desactualizado, modificación pendiente | 94 | 87 | 96 | 100 | 50 |
| 14 | Herramienta de diagnóstico y evaluación | 90 | 97 | 100 | 66 | 100 |

## Detalle por URL

*Cada sección combina los datos técnicos/SEO/tracking de la auditoría base con los resultados Lighthouse de esa misma URL.*

### 1. Servicio — campaña Ads
`https://defensordelcontribuyente.cl/cobranza-fiscal/`

**Estado, indexación y medición**

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | self |
| Google Tag Manager | GTM-MQC692WV, GTM-N7BQZZW (duplicado) |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |

**SEO on-page**

- Title: Cobranza Fiscal ✅Soluciones Legales para Deudas Tributarias (60 car.)
- Meta description: Cobranza Fiscal: evita embargos y soluciona tus deudas con Tesorería... (122 car.)
- H1: 1: Cobranza Fiscal: Soluciones para Deudas con Tesorería.
- Schema: BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite
- Palabras (contenido visible): 429

**Conversión de leads / técnico**

- Formularios: 4 | WhatsApp: Sí | Teléfono: 227121756
- CSS: 46 hojas | Imágenes sin alt: 12 de 24 (50%) | WordPress: 6.8.8

**Lighthouse**

- Rendimiento 61 | Accesibilidad 88 | Buenas prácticas 73 | SEO 100 | Visibilidad IA 33
- Principales hallazgos Lighthouse:
  - Background and foreground colors do not have a sufficient contrast ratio.
  - Links do not have a discernible name
  - Touch targets do not have sufficient size or spacing.
  - Uses third-party cookies
  - Document does not have a main landmark.
  - Browser errors were logged to the console

**Notas específicas (auditoría base)**

- H1 único y correcto.
- Sin schema Service específico.
- 50% de las imágenes sin alt descriptivo.

### 2. Servicio — campaña Ads
`https://defensordelcontribuyente.cl/prescripcion-tributaria/`

**Estado, indexación y medición**

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | self |
| Google Tag Manager | GTM-MQC692WV, GTM-N7BQZZW (duplicado) |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |

**SEO on-page**

- Title: Prescripción tributaria en Chile: Evaluación legal y Representación (67 car.)
- Meta description: Evaluación de deudas fiscales legalmente con ayuda de abogados tributarios... (132 car.)
- H1: 1: Prescripción Tributaria: Evaluación Legal y Representación Experta
- Schema: BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite
- Palabras (contenido visible): 482

**Conversión de leads / técnico**

- Formularios: 4 | WhatsApp: Sí | Teléfono: 227121756
- CSS: 46 hojas | Imágenes sin alt: 12 de 26 (46%) | WordPress: 6.8.8

**Lighthouse**

- Rendimiento 65 | Accesibilidad 88 | Buenas prácticas 73 | SEO 100 | Visibilidad IA 33
- Principales hallazgos Lighthouse:
  - Background and foreground colors do not have a sufficient contrast ratio.
  - Links do not have a discernible name
  - Touch targets do not have sufficient size or spacing.
  - Uses third-party cookies
  - Document does not have a main landmark.
  - Browser errors were logged to the console

**Notas específicas (auditoría base)**

- H1 único y correcto.
- Sin schema Service específico.
- 46% de las imágenes sin alt descriptivo.

### 3. Servicio — campaña Ads
`https://defensordelcontribuyente.cl/fiscalizacion-tributaria-citaciones-sii/`

**Estado, indexación y medición**

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | self |
| Google Tag Manager | GTM-MQC692WV, GTM-N7BQZZW (duplicado) |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |

**SEO on-page**

- Title: Fiscalización Tributaria y Citaciones del SII ✅Defiéndete (58 car.)
- Meta description: ¿Te notificó el SII? Aprende cómo enfrentar una Fiscalización Tributaria... (146 car.)
- H1: 1: Fiscalización Tributaria y Citaciones del SII.
- Schema: BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite
- Palabras (contenido visible): 745

**Conversión de leads / técnico**

- Formularios: 4 | WhatsApp: Sí | Teléfono: 227121756
- CSS: 45 hojas | Imágenes sin alt: 18 de 37 (49%) | WordPress: 6.8.8

**Lighthouse**

- Rendimiento 61 | Accesibilidad 88 | Buenas prácticas 73 | SEO 100 | Visibilidad IA 33
- Principales hallazgos Lighthouse:
  - Background and foreground colors do not have a sufficient contrast ratio.
  - Links do not have a discernible name
  - Touch targets do not have sufficient size or spacing.
  - Uses third-party cookies
  - Document does not have a main landmark.
  - Browser errors were logged to the console

**Notas específicas (auditoría base)**

- H1 único y correcto.
- Página de servicio con más contenido (745 palabras).
- 49% de las imágenes sin alt — la de más imágenes del grupo de servicios.

### 4. Servicio — campaña Ads (subdominio servicios.)
`https://servicios.defensordelcontribuyente.cl/convenios-condonaciones/`

**Estado, indexación y medición**

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | self |
| Google Tag Manager | GTM-N7BQZZW (único, sin duplicidad) |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |

**SEO on-page**

- Title: Condonación de Deuda Fiscal | Reduce tu deuda con Tesorería ✅ (61 car.)
- Meta description: Condonación de Deuda Fiscal: accede a facilidades de pago... (125 car.)
- H1: 1: Condonación de Deuda Fiscal: Alivia tu carga tributaria
- Schema: BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite
- Palabras (contenido visible): 751

**Conversión de leads / técnico**

- Formularios: 3 | WhatsApp: No | Teléfono: 227121756
- CSS: 46 hojas | Imágenes sin alt: 8 de 24 (33%) | WordPress: 7.0.4

**Lighthouse**

- Rendimiento 93 | Accesibilidad 90 | Buenas prácticas 100 | SEO 100 | Visibilidad IA 50
- Principales hallazgos Lighthouse:
  - Background and foreground colors do not have a sufficient contrast ratio.
  - Links do not have a discernible name
  - Touch targets do not have sufficient size or spacing.
  - Accessibility tree is not well-formed

**Notas específicas (auditoría base)**

- Corre sobre WordPress 7.0.4 — instalación separada del dominio principal (6.8.8).
- Sin botón de WhatsApp.
- Solo 1 contenedor GTM — no presenta la duplicidad del dominio principal.
- 33% de las imágenes sin alt — el mejor porcentaje de las 14 URL.

### 5. FAQ
`https://defensordelcontribuyente.cl/preguntas-frecuentes-prescripcion-tributaria/`

**Estado, indexación y medición**

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | self |
| Google Tag Manager | GTM-MQC692WV, GTM-N7BQZZW (duplicado) |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |

**SEO on-page**

- Title: Preguntas Frecuentes sobre Prescripción Tributaria en Chile ✅ (61 car.)
- Meta description: Resuelve tus dudas sobre cómo opera la prescripción tributaria en Chile... (117 car.)
- H1: 2 (duplicado): Preguntas Frecuentes sobre la Prescripción Tributaria en Chile / Reunión ✅Prescripción Tributaria
- Schema: BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite
- Palabras (contenido visible): 696

**Conversión de leads / técnico**

- Formularios: 4 | WhatsApp: Sí | Teléfono: 227121756
- CSS: 39 hojas | Imágenes sin alt: 6 de 12 (50%) | WordPress: 6.8.8

**Lighthouse**

- Rendimiento 59 | Accesibilidad 83 | Buenas prácticas 73 | SEO 100 | Visibilidad IA 33
- Principales hallazgos Lighthouse:
  - Background and foreground colors do not have a sufficient contrast ratio.
  - Links do not have a discernible name
  - Uses third-party cookies
  - Document does not have a main landmark.
  - Browser errors were logged to the console
  - Issues were logged in the `Issues` panel in Chrome Devtools

**Notas específicas (auditoría base)**

- Doble H1 — el segundo corresponde al bloque de agendamiento, debería bajar a H2/H3.
- Sin schema FAQPage pese a ser una FAQ.
- 50% de las imágenes sin alt.

### 6. FAQ
`https://defensordelcontribuyente.cl/preguntas-frecuentes-cobranza-fiscal/`

**Estado, indexación y medición**

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | self |
| Google Tag Manager | GTM-MQC692WV, GTM-N7BQZZW (duplicado) |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |

**SEO on-page**

- Title: Preguntas Frecuentes sobre Cobranza Fiscal en Chile ✅ (53 car.)
- Meta description: Conoce las respuestas a las dudas más comunes sobre cobranza fiscal en Chile... (136 car.)
- H1: 2 (duplicado): Preguntas Frecuentes sobre Cobranza Fiscal en Chile / Reunión ✅Cobranza Fiscal
- Schema: BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite
- Palabras (contenido visible): 603

**Conversión de leads / técnico**

- Formularios: 4 | WhatsApp: Sí | Teléfono: 227121756
- CSS: 39 hojas | Imágenes sin alt: 6 de 11 (55%) | WordPress: 6.8.8

**Lighthouse**

- Rendimiento 59 | Accesibilidad 83 | Buenas prácticas 73 | SEO 100 | Visibilidad IA 33
- Principales hallazgos Lighthouse:
  - Background and foreground colors do not have a sufficient contrast ratio.
  - Links do not have a discernible name
  - Uses third-party cookies
  - Document does not have a main landmark.
  - Browser errors were logged to the console
  - Issues were logged in the `Issues` panel in Chrome Devtools

**Notas específicas (auditoría base)**

- Mismo problema de doble H1 que la FAQ de prescripción.
- Sin schema FAQPage.
- 55% de las imágenes sin alt.

### 7. FAQ (subdominio servicios.) — contenido desactualizado, modificación pendiente
`https://servicios.defensordelcontribuyente.cl/faq-convenios-condonaciones/`

**Estado, indexación y medición**

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | NO (noindex, nofollow) |
| Canonical | Sin canonical |
| Google Tag Manager | GTM-N7BQZZW (único) |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |

**SEO on-page**

- Title: Resuelve tus dudas sobre Convenios y Condonaciones (50 car.)
- Meta description: Conoce las dudas más comunes de personas que quieren pagar sus deudas fiscales... (136 car.)
- H1: 2 (duplicado): Preguntas Frecuentes / Reunión ✅Convenios y Condonaciones
- Schema: BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite
- Palabras (contenido visible): 580

**Conversión de leads / técnico**

- Formularios: 2 | WhatsApp: No | Teléfono: 227121756
- CSS: 40 hojas | Imágenes sin alt: 6 de 10 (60%) | WordPress: 7.0.4

**Lighthouse**

- Rendimiento 88 | Accesibilidad 77 | Buenas prácticas 100 | SEO 66 | Visibilidad IA 50
- Principales hallazgos Lighthouse:
  - Background and foreground colors do not have a sufficient contrast ratio.
  - Links do not have a discernible name
  - Touch targets do not have sufficient size or spacing.
  - Page is blocked from indexing
  - Heading elements are not in a sequentially-descending order
  - Accessibility tree is not well-formed

**Notas específicas (auditoría base)**

- Bloqueada para buscadores (noindex, nofollow), sin canonical — única FAQ de las tres no indexable.
- WordPress 7.0.4 (instalación distinta).
- Sin botón de WhatsApp.
- Sin schema FAQPage.
- 60% de las imágenes sin alt.

### 8. Casos de éxito
`https://defensordelcontribuyente.cl/casos-exito-tributario/`

**Estado, indexación y medición**

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | self |
| Google Tag Manager | GTM-MQC692WV, GTM-N7BQZZW (duplicado) |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |

**SEO on-page**

- Title: Casos de Éxito Tributario en Chile | Prescripción y Cobranza ✅ (62 car.)
- Meta description: Testimonios reales sobre prescripción tributaria y cobranza fiscal en Chile... (136 car.)
- H1: 2 (duplicado): Clientes Felices Comparten su Experiencia / Reunión ✅Diagnóstico Tributario
- Schema: BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite
- Palabras (contenido visible): 650

**Conversión de leads / técnico**

- Formularios: 3 | WhatsApp: Sí | Teléfono: 227121756
- CSS: 37 hojas | Imágenes sin alt: 20 de 26 (77%) | WordPress: 6.8.8

**Lighthouse**

- Rendimiento 74 | Accesibilidad 83 | Buenas prácticas 73 | SEO 100 | Visibilidad IA 33
- Principales hallazgos Lighthouse:
  - Background and foreground colors do not have a sufficient contrast ratio.
  - Links do not have a discernible name
  - Uses third-party cookies
  - Heading elements are not in a sequentially-descending order
  - Document does not have a main landmark.
  - Browser errors were logged to the console

**Notas específicas (auditoría base)**

- Doble H1 (mismo patrón del bloque de agendamiento).
- Sin schema Review/AggregateRating pese a ser testimonios.
- 77% de las imágenes sin alt — el peor porcentaje entre páginas de contenido.

### 9. Casos de éxito
`https://defensordelcontribuyente.cl/casos-de-exito/`

**Estado, indexación y medición**

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | self |
| Google Tag Manager | GTM-MQC692WV, GTM-N7BQZZW (duplicado) |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |

**SEO on-page**

- Title: Casos de éxito del Defensor del Contribuyente (45 car.)
- Meta description: Descubre los casos de éxito del Defensor del Contribuyente... (126 car.)
- H1: 1: Nuestros Casos de Éxito
- Schema: BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite
- Palabras (contenido visible): 410

**Conversión de leads / técnico**

- Formularios: 4 | WhatsApp: Sí | Teléfono: 227121756
- CSS: 44 hojas | Imágenes sin alt: 8 de 28 (29%) | WordPress: 6.8.8

**Lighthouse**

- Rendimiento 75 | Accesibilidad 86 | Buenas prácticas 73 | SEO 100 | Visibilidad IA 33
- Principales hallazgos Lighthouse:
  - Elements with an ARIA `[role]` that require children to contain a specific `[role]` are missing some or all of those required children.
  - Background and foreground colors do not have a sufficient contrast ratio.
  - Links do not have a discernible name
  - Uses third-party cookies
  - Heading elements are not in a sequentially-descending order
  - Browser errors were logged to the console

**Notas específicas (auditoría base)**

- H1 único y correcto.
- Existen DOS páginas de "casos de éxito" activas y distintas (esta y casos-exito-tributario/) apuntando al mismo tema — confirmar si es deliberado o compiten entre sí por las mismas búsquedas.
- Sin schema Review/AggregateRating.
- 29% de las imágenes sin alt — buen porcentaje relativo.

### 10. Blog — recurso de campaña
`https://defensordelcontribuyente.cl/blog/prescriben-deudas-fiscales-chile/`

**Estado, indexación y medición**

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | self |
| Google Tag Manager | GTM-MQC692WV, GTM-N7BQZZW (duplicado) |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |

**SEO on-page**

- Title: ¿Prescriben las Deudas Fiscales en Chile? | Prescripción Tributaria (67 car.)
- Meta description: Conoce cómo funciona la prescripción tributaria en Chile... (133 car.)
- H1: 2 (duplicado): ¿Prescriben las Deudas Fiscales en Chile?... / Reunión ✅Prescripción Tributaria
- Schema: Article, BreadcrumbList, CommentAction, EntryPoint, ImageObject, ListItem, Organization, Person, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite
- Palabras (contenido visible): 1383

**Conversión de leads / técnico**

- Formularios: 3 | WhatsApp: Sí | Teléfono: 227121756
- CSS: 39 hojas | Imágenes sin alt: 22 de 30 (73%) | WordPress: 6.8.8

**Lighthouse**

- Rendimiento 74 | Accesibilidad 91 | Buenas prácticas 73 | SEO 100 | Visibilidad IA 33
- Principales hallazgos Lighthouse:
  - Background and foreground colors do not have a sufficient contrast ratio.
  - Links do not have a discernible name
  - Uses third-party cookies
  - Document does not have a main landmark.
  - Browser errors were logged to the console
  - Issues were logged in the `Issues` panel in Chrome Devtools

**Notas específicas (auditoría base)**

- La URL de campaña incluye parámetros de tracking (_gcl_au, _ga, _ga_V3QV7MTY5Q) — confirma uso real en clics de campañas pagadas/Analytics.
- Doble H1 (bloque de agendamiento).
- Usa correctamente schema Article y Person — único grupo con esta cobertura.
- 73% de las imágenes sin alt — la peor proporción del sitio.
- El contenido con objetivo de búsqueda más directo del grupo.

### 11. Blog — recurso de campaña (subdominio servicios.)
`https://servicios.defensordelcontribuyente.cl/blog/ml-deudas-fiscales-cobranza-tesoreria/`

**Estado, indexación y medición**

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | self |
| Google Tag Manager | GTM-N7BQZZW (único) |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |

**SEO on-page**

- Title: ¿Deudas Fiscales? Aprende sobre la Cobranza Tributaria (54 car.)
- Meta description: La cobranza fiscal se inicia con la notificación, requerimiento de pago y embargo... (130 car.)
- H1: 2 (duplicado): ¿Deudas Fiscales? Principales alcances... / Reunión ✅Cobranza Fiscal
- Schema: Article, BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, Person, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite
- Palabras (contenido visible): 1766

**Conversión de leads / técnico**

- Formularios: 2 | WhatsApp: No | Teléfono: 227121756
- CSS: 40 hojas | Imágenes sin alt: 12 de 16 (75%) | WordPress: 7.0.4

**Lighthouse**

- Rendimiento 83 | Accesibilidad 87 | Buenas prácticas 96 | SEO 100 | Visibilidad IA 49
- Principales hallazgos Lighthouse:
  - Background and foreground colors do not have a sufficient contrast ratio.
  - Links do not have a discernible name
  - Touch targets do not have sufficient size or spacing.
  - Skip links are not focusable.
  - Browser errors were logged to the console
  - Accessibility tree is not well-formed

**Notas específicas (auditoría base)**

- Corre sobre WordPress 7.0.4 (instalación distinta).
- Sin botón de WhatsApp.
- El contenido de mayor extensión de las 14 URL (1.766 palabras).
- 75% de las imágenes sin alt.

### 12. Blog — recurso de campaña (subdominio servicios.) — contenido desactualizado, modificación pendiente
`https://servicios.defensordelcontribuyente.cl/blog/ml-condonaciones-convenios/`

**Estado, indexación y medición**

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | self |
| Google Tag Manager | GTM-N7BQZZW (único) |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |

**SEO on-page**

- Title: Condonaciones de Intereses y Multas en Materia Tributaria (57 car.)
- Meta description: Una simple mora o postergación en el pago de un impuesto puede convertirse en pesadilla... (128 car.)
- H1: 2 (duplicado): Alcances a las Condonaciones de Intereses y Multas... / Reunión ✅Convenios y Condonaciones
- Schema: Article, BreadcrumbList, EntryPoint, ImageObject, ListItem, Organization, Person, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite
- Palabras (contenido visible): 1206

**Conversión de leads / técnico**

- Formularios: 2 | WhatsApp: No | Teléfono: 227121756
- CSS: 40 hojas | Imágenes sin alt: 20 de 32 (63%) | WordPress: 7.0.4

**Lighthouse**

- Rendimiento 69 | Accesibilidad 87 | Buenas prácticas 96 | SEO 100 | Visibilidad IA 30
- Principales hallazgos Lighthouse:
  - Background and foreground colors do not have a sufficient contrast ratio.
  - Links do not have a discernible name
  - Touch targets do not have sufficient size or spacing.
  - Skip links are not focusable.
  - Browser errors were logged to the console
  - Accessibility tree is not well-formed

**Notas específicas (auditoría base)**

- La URL de campaña lleva el parámetro ?preview_id (sin valor). Contenido idéntico a la versión limpia (mismo title/canonical/H1/meta robots), pero pierde caché: 1.51s de carga vs 0.11s — ~14x más lento en cada clic pagado. CORRECCIÓN DE MAYOR IMPACTO DEL ANÁLISIS: cambiar la URL de la campaña a la versión sin parámetros.
- WordPress 7.0.4.
- Sin botón de WhatsApp.
- 63% de las imágenes sin alt.

### 13. Blog — recurso de campaña (subdominio servicios.) — contenido desactualizado, modificación pendiente
`https://servicios.defensordelcontribuyente.cl/blog/perdonazo-tributario-2022/`

**Estado, indexación y medición**

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | Sí (index, follow) |
| Canonical | self |
| Google Tag Manager | GTM-N7BQZZW (único) |
| Conversión Google Ads | AW-593050363 |
| Meta Pixel | No |

**SEO on-page**

- Title: Perdonazo Tributario 2022 ¿Es para ti? 🤔Descúbrelo aquí (56 car.)
- Meta description: Conoce las claves para acceder al Perdonazo Tributario 2022... (114 car.)
- H1: 2 (duplicado): Nuevo "Perdonazo" Tributario 2022. Proyecto de Ley Boletín N° 15239-03. / Reunión ✅Convenios y Condonaciones
- Schema: Article, BreadcrumbList, CommentAction, EntryPoint, ImageObject, ListItem, Organization, Person, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite
- Palabras (contenido visible): 1097

**Conversión de leads / técnico**

- Formularios: 2 | WhatsApp: No | Teléfono: 227121756
- CSS: 39 hojas | Imágenes sin alt: 10 de 14 (71%) | WordPress: 7.0.4

**Lighthouse**

- Rendimiento 94 | Accesibilidad 87 | Buenas prácticas 96 | SEO 100 | Visibilidad IA 50
- Principales hallazgos Lighthouse:
  - Background and foreground colors do not have a sufficient contrast ratio.
  - Links do not have a discernible name
  - Touch targets do not have sufficient size or spacing.
  - Skip links are not focusable.
  - Browser errors were logged to the console
  - Accessibility tree is not well-formed

**Notas específicas (auditoría base)**

- Mismo problema de ?preview_id: 1.53s vs 0.12s de la versión limpia.
- El título referencia "2022" y un Boletín de ley específico — confirmar con el equipo legal si la normativa sigue vigente tal cual descrita; si cambió, es contenido desactualizado que un anuncio activo podría estar promoviendo.
- 71% de las imágenes sin alt.

### 14. Herramienta de diagnóstico y evaluación
`https://diagnostico.defensordelcontribuyente.cl/`

**Estado, indexación y medición**

| Campo | Valor |
|---|---|
| Estado | HTTP 200 |
| Indexable | NO (noindex, nofollow) |
| Canonical | Sin canonical |
| Google Tag Manager | Ninguno |
| Conversión Google Ads | No |
| Meta Pixel | No |

**SEO on-page**

- Title: Diagnóstico Tributario por Expertos - Defensor del Contribuyente (64 car.)
- Meta description: Es hora de conocer tus opciones y tomar el control de tu futuro. Descarga y envía tu información fiscal... (133 car.)
- H1: 0 encontrados — falta
- Schema: BreadcrumbList, EntryPoint, ImageObject, ListItem, PropertyValueSpecification, ReadAction, SearchAction, WebPage, WebSite
- Palabras (contenido visible): 1002

**Conversión de leads / técnico**

- Formularios: 1 | WhatsApp: No | Teléfono: 227121756
- CSS: 20 hojas | Imágenes sin alt: 53 de 53 (100%) | WordPress: 6.7.5

**Lighthouse**

- Rendimiento 90 | Accesibilidad 97 | Buenas prácticas 100 | SEO 66 | Visibilidad IA 100
- Principales hallazgos Lighthouse:
  - Background and foreground colors do not have a sufficient contrast ratio.
  - Page is blocked from indexing

**Notas específicas (auditoría base)**

- SIN NINGÚN TRACKING: cero contenedores GTM, sin tag de conversión de Ads, sin Meta Pixel. Es la herramienta de mayor intención de conversión (formulario con carga de documentos tributarios) y hoy no queda registro de una sola conversión completada.
- noindex, nofollow, sin canonical — no se encontró en búsquedas de verificación.
- Sin ningún H1 en la página — rompe la jerarquía de encabezados del resto del sitio.
- Las 53 imágenes tienen alt vacío — 0% con texto descriptivo, el peor resultado de accesibilidad de las 14 URL.
- WordPress 6.7.5 — la tercera versión de WordPress distinta encontrada en el ecosistema.
- La página más pesada del análisis (329 KB).

## Priorización de acciones

| Prioridad | Acción | Por qué |
|---|---|---|
| 1 | Instalar tracking (GTM + conversión Ads) en diagnostico.defensordelcontribuyente.cl | Es el formulario de mayor intención de todo el ecosistema y hoy no mide ni una conversión |
| 2 | Quitar uno de los dos contenedores GTM duplicados en las 8 URL del dominio principal | Riesgo de conversiones infladas/duplicadas en cualquier reporte |
| 3 | Instalar Meta Pixel si se piensa pautar o ya se pauta en Meta Ads | Sin esto no hay medición de conversión ni remarketing en ese canal |
| 4 | Cambiar la URL de campaña de los 2 posts con `?preview_id` a la versión limpia | Corrección de 1 línea, ~14x más rápido en cada clic pagado |
| 5 | Unificar versión de WordPress entre dominio principal, servicios. y diagnostico. | Evita que un fix en un sitio no se propague a los otros dos |
| 6 | Revisar si las 2 páginas de "casos de éxito" deben coexistir o consolidarse | Evita canibalización SEO entre páginas del mismo tema |
| 7 | Bajar el segundo H1 ("Reunión...") a H2/H3 en las 8 URL afectadas | Señal de tema más limpia para buscadores |
| 8 | Agregar schema FAQPage a las 3 FAQ y Review/AggregateRating a las páginas de casos de éxito | Rich snippets de bajo esfuerzo con buena tasa de clics |
| 9 | Agregar texto alternativo a imágenes, empezando por diagnostico. (100% sin alt) y el blog de prescripción (73%) | Accesibilidad + señal SEO adicional |

## Metodología y limitaciones

- Datos SEO/tracking/técnicos obtenidos por descarga directa del HTML público de cada URL (sin autenticación) y verificación cruzada de indexación mediante búsqueda web.
- La verificación de indexación en Google es orientativa, no equivale a una consulta directa a Google Search Console.
- Complemento de rendimiento/accesibilidad/mejores prácticas/SEO/visibilidad IA generado con Lighthouse (Google Chrome), modo headless, una corrida por URL, sin throttling personalizado adicional al perfil por defecto de Lighthouse.
- No se tuvo acceso a Google Search Console ni al Administrador de Eventos de Meta al momento de la auditoría base; el Google Ads MCP y el Analytics MCP oficiales quedaron instalados en esta misma sesión de trabajo (Analytics ya operativo, Ads pendiente de aprobación de Google) para auditorías futuras con datos reales de tráfico y conversión.
- El conteo de palabras es aproximado (texto visible, sin scripts ni estilos).
