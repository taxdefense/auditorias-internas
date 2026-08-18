# Auditoría Completa GA4 — Defensor del Contribuyente

**Fecha:** 18-08-2026 · **Fuente:** servidor MCP oficial de Google Analytics (`googleanalytics/google-analytics-mcp`), conectado manualmente vía protocolo MCP dado que la sesión interactiva de Claude Code no pudo reiniciarse. **Periodo de datos:** últimos 30 días (30daysAgo - yesterday).

## Resumen ejecutivo

La cuenta de Google Analytics **"Defensor del Contribuyente"** (accounts/350833440) tiene **dos propiedades GA4 separadas y sin relacionar entre sí** — una por dominio principal, otra por el subdominio servicios. — y **ninguna propiedad para diagnostico.defensordelcontribuyente.cl** (confirma lo detectado en la auditoría de 14 URL: cero tracking ahí). Las dos propiedades existentes están vinculadas correctamente a la cuenta de Google Ads (customer_id 8985279729). El dominio principal mueve tráfico real (2013 sesiones/30d, dominado por Paid Search) con eventos de conversión ya configurados para 2 de 3 servicios principales; el subdominio servicios. prácticamente no registra actividad (12 sesiones/30d) ni tiene un solo evento personalizado configurado, pese a alojar páginas reales de campaña (confirmado en la auditoría de 14 URL).

## Hallazgos críticos

**[CRÍTICO] Dos propiedades GA4 sin relacionar — sesiones fragmentadas por diseño**
- `properties/487864971` — defensordelcontribuyente.cl
- `properties/484039052` — servicios.defensordelcontribuyente.cl

No existe una propiedad de rollup ni relación entre ambas. Un usuario que navega del dominio principal a servicios. (o viceversa) genera una sesión nueva en una propiedad distinta — el recorrido real del usuario no se puede reconstruir sin cruzar manualmente ambos datasets.

**[CRÍTICO] servicios.defensordelcontribuyente.cl no tiene ni un solo evento personalizado configurado.** Solo registra los eventos automáticos de GA4 (page_view, session_start, first_visit, scroll, user_engagement). No hay `form_start`, `form_submit`, ni `click` — pese a que la auditoría de 14 URL confirmó formularios reales en sus páginas de campaña (ej. convenios-condonaciones con 3 formularios). Ninguna conversión de este subdominio se está midiendo.

**[ALTO] Un evento de conversión configurado de forma inconsistente en el dominio principal.** De los 3 eventos `form_submit_*` que existen, 2 están marcados como conversión (`form_submit_cobranza_fiscal`: 27 eventos, 27 conversiones; `form_submit_prescripcion`: 15 eventos, 15 conversiones) y **uno no** (`form_submit_fiscalizacion_tributaria_cit`: 19 eventos, **0 conversiones**). Esas 19 conversiones reales no se están contando ni reportando a Google Ads.

**[MEDIO] La propiedad servicios. tiene la moneda configurada en USD, no en CLP** (el dominio principal sí está en CLP). Y su categoría de industria está sin especificar (`INDUSTRY_CATEGORY_UNSPECIFIED`), a diferencia del dominio principal (`OTHER`).

**[MEDIO] Ningún clic a WhatsApp o teléfono tiene un evento propio.** El único evento de clic genérico (`click`: 33 en 30 días en el dominio principal) no permite distinguir qué se clickeó. La auditoría de 14 URL confirmó botones de WhatsApp en 8 de 14 páginas — hoy no hay forma de saber cuántos de esos 33 clics fueron a WhatsApp.

**[INFO] Ya existe tráfico real proveniente de asistentes de IA.** El canal "AI Assistant" generó 9 sesiones en 30 días en el dominio principal — coincide con el hallazgo de la auditoría Lighthouse (visibilidad IA: 33/100, llms.txt fuera de norma). Ya hay señal real que justifica mejorar ese puntaje, no es un tema puramente especulativo.

## Propiedad: defensordelcontribuyente.cl
`properties/487864971`

**Configuración**

| Campo | Valor |
|---|---|
| Creada | 2025-05-02 |
| Zona horaria | America/Santiago |
| Moneda | CLP |
| Categoría de industria | OTHER |
| Nivel de servicio | GOOGLE_ANALYTICS_STANDARD |
| Vínculo Google Ads | Sí — customer_id 8985279729, personalización de anuncios: True, creado 2025-05-05 |

**Tráfico por canal — últimos 30 días (total: 2013 sesiones)**

| Canal | Sesiones | Usuarios | Tasa de interacción | Duración media (s) | Tasa de rebote |
|---|---|---|---|---|---|
| Paid Search | 1219 | 1082 | 54.6% | 128 | 45.4% |
| Organic Search | 533 | 458 | 57.6% | 174 | 42.4% |
| Direct | 196 | 162 | 28.1% | 97 | 71.9% |
| Referral | 24 | 19 | 54.2% | 197 | 45.8% |
| Organic Social | 18 | 17 | 77.8% | 35 | 22.2% |
| AI Assistant | 9 | 6 | 33.3% | 6 | 66.7% |
| Cross-network | 8 | 8 | 87.5% | 93 | 12.5% |
| Display | 5 | 2 | 80.0% | 691 | 20.0% |
| Organic Video | 1 | 1 | 100.0% | 149 | 0.0% |

**Páginas más vistas — últimos 30 días**

| Página | Vistas | Sesiones |
|---|---|---|
| /prescripcion-tributaria/ | 445 | 410 |
| /cobranza-fiscal/ | 413 | 382 |
| /fiscalizacion-tributaria-citaciones-sii/ | 294 | 288 |
| / | 277 | 239 |
| /blog/prescripcion-tributaria/ | 151 | 154 |
| /blog/prescriben-deudas-fiscales-chile/ | 146 | 143 |
| /contacto/ | 105 | 99 |
| /blog/prescripcion-tributaria-art-200/ | 87 | 89 |
| /equipo/ | 72 | 70 |
| /blog/certificado-deuda-fiscal/ | 58 | 54 |
| /servicios/ | 54 | 42 |
| /casos-de-exito/ | 34 | 29 |
| /servicio-tributario/concepcion/ | 23 | 23 |
| /blog/abandono-del-procedimiento/ | 22 | 21 |
| /blog/citacion-del-sii-como-defenderte/ | 21 | 21 |

**Eventos — últimos 30 días**

| Evento | Cantidad | Marcado como conversión |
|---|---|---|
| page_view | 2519 | No |
| session_start | 2016 | No |
| first_visit | 1699 | No |
| user_engagement | 1492 | No |
| scroll | 605 | No |
| form_start | 141 | No |
| click | 33 | No |
| form_submit_cobranza_fiscal | 27 | Sí (27) |
| form_submit_fiscalizacion_tributaria_cit | 19 | No |
| form_submit_prescripcion | 15 | Sí (15) |
| file_download | 13 | No |

**Custom dimensions / metrics:** ninguno configurado.

## Propiedad: servicios.defensordelcontribuyente.cl
`properties/484039052`

**Configuración**

| Campo | Valor |
|---|---|
| Creada | 2025-04-01 |
| Zona horaria | America/Santiago |
| Moneda | USD |
| Categoría de industria | INDUSTRY_CATEGORY_UNSPECIFIED |
| Nivel de servicio | GOOGLE_ANALYTICS_STANDARD |
| Vínculo Google Ads | Sí — customer_id 8985279729, personalización de anuncios: True, creado 2025-05-07 |

**Tráfico por canal — últimos 30 días (total: 12 sesiones)**

| Canal | Sesiones | Usuarios | Tasa de interacción | Duración media (s) | Tasa de rebote |
|---|---|---|---|---|---|
| Direct | 11 | 7 | 45.5% | 259 | 54.5% |
| Paid Search | 1 | 1 | 100.0% | 15 | 0.0% |

**Páginas más vistas — últimos 30 días**

| Página | Vistas | Sesiones |
|---|---|---|
| /convenios-condonaciones/ | 5 | 1 |
| / | 4 | 3 |
| /politica-privacidad/ | 4 | 4 |
| /blog/ml-condonaciones-convenios/ | 3 | 1 |
| /convenios-condonaciones | 3 | 1 |
| /acceso-df-77   fue cambiado el login | 2 | 2 |
| /blog/ml-deudas-fiscales-cobranza-tesoreria/ | 2 | 1 |
| /faq-convenios-condonaciones/ | 2 | 1 |
| /ml-agenda-ddcon/ | 2 | 2 |
| /blog/perdonazo-tributario-2022/ | 1 | 1 |
| /ml-abogado-tributario/ | 1 | 1 |
| /ml-cobranza-fiscal/ | 1 | 1 |
| /perdonazo-tributario/ | 1 | 1 |
| /terminos-y-condiciones/ | 1 | 1 |

**Eventos — últimos 30 días**

| Evento | Cantidad | Marcado como conversión |
|---|---|---|
| page_view | 32 | No |
| user_engagement | 28 | No |
| scroll | 16 | No |
| session_start | 12 | No |
| first_visit | 8 | No |

**Custom dimensions / metrics:** ninguno configurado.

## Priorización de acciones

| Prioridad | Acción | Por qué |
|---|---|---|
| 1 | Marcar `form_submit_fiscalizacion_tributaria_cit` como evento clave/conversión en GA4 | Confirmado: 19 conversiones reales del último mes no se están contando, a diferencia de los otros 2 servicios |
| 2 | Instrumentar GTM + GA4 en diagnostico.defensordelcontribuyente.cl | No existe propiedad GA4 para este subdominio — cero visibilidad del formulario de mayor intención |
| 3 | Instrumentar eventos `form_start`/`form_submit`/`click` en servicios.defensordelcontribuyente.cl | Hoy solo tiene los eventos automáticos de GA4; sus formularios de campaña no generan ningún evento medible |
| 4 | Corregir moneda de la propiedad servicios. (USD → CLP) y definir categoría de industria | Configuración inconsistente con el resto de la cuenta |
| 5 | Instrumentar eventos distintos para clics a WhatsApp y a teléfono | Hoy solo existe un evento genérico `click` sin desglose por destino |
| 6 | Definir si servicios. debe seguir siendo una propiedad separada o consolidarse con el dominio principal | Con 12 sesiones/30 días y cero eventos personalizados, hoy es prácticamente un dato muerto |
| 7 | Investigar la caída de 141 `form_start` a 61 `form_submit_*` totales (57% de abandono) en el dominio principal | Posible fricción de formulario a resolver junto con UX de la landing |

## Metodología y limitaciones

- Datos obtenidos en vivo vía el servidor MCP oficial `googleanalytics/google-analytics-mcp` (Apache 2.0, Google), autenticado con Application Default Credentials del proyecto `doppler-dddcon`.
- La sesión interactiva de Claude Code no logró cargar el servidor MCP recién registrado ni tras reinicio solicitado; se conectó manualmente hablando el protocolo MCP (JSON-RPC sobre stdio) directamente contra el proceso `pipx run analytics-mcp`, replicando exactamente las mismas llamadas que haría el cliente integrado.
- Periodo de datos: 30daysAgo - yesterday (zona horaria de cada propiedad, America/Santiago).
- El reporte especializado de conversiones (`run_conversions_report`) no aceptó `eventName` como dimensión en esta versión del servidor; se sustituyó por un reporte estándar (`run_report`) con dimensión `eventName` y métricas `eventCount`/`conversions`, que entrega la misma información.
- No se auditó diagnostico.defensordelcontribuyente.cl porque no existe una propiedad GA4 asociada a ese subdominio.
