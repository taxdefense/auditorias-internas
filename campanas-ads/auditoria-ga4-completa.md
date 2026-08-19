# Auditoría Completa GA4 — Defensor del Contribuyente

**Fecha:** 19-08-2026 (segunda corrida, reemplaza la versión del 18-08-2026) · **Fuente:** servidor MCP oficial de Google Analytics (`googleanalytics/google-analytics-mcp`), esta vez conectado de forma nativa por Claude Code (la sesión cargó el servidor correctamente, sin necesitar el cliente manual usado en la primera corrida). **Periodo de datos:** últimos 30 días (30daysAgo - yesterday).

## Resumen ejecutivo

Se repitió la auditoría GA4 completa y se agregó el cruce pedido: tráfico y conversiones reales para cada una de las **14 URL de la auditoría técnica de campañas**. Los hallazgos estructurales de la primera corrida se mantienen sin cambios (2 propiedades GA4 sin relacionar, ninguna en diagnostico., el evento de conversión de Fiscalización Tributaria sigue sin marcarse). Lo nuevo: de las 14 URL, **13 tienen datos GA4 disponibles y 1 (diagnostico.) no tiene ninguna propiedad asociada**. Esas 13 URL sumaron **1364 vistas de página, 1275 sesiones y 41 conversiones** en 30 días — el 100% de esas conversiones concentradas en solo 2 de las 14 páginas. Varias de las 14 URL de campaña tienen tráfico real casi nulo en el último mes.

## Hallazgos críticos (confirmados en esta segunda corrida)

**[CRÍTICO] Dos propiedades GA4 sin relacionar — sesiones fragmentadas por diseño**
- `properties/487864971` — defensordelcontribuyente.cl
- `properties/484039052` — servicios.defensordelcontribuyente.cl

**[CRÍTICO] servicios.defensordelcontribuyente.cl sigue sin un solo evento personalizado configurado.** Solo eventos automáticos de GA4.

**[ALTO] `form_submit_fiscalizacion_tributaria_cit` sigue sin marcarse como conversión** — 19 eventos en 30 días, 0 conversiones, mientras que los otros 2 formularios de servicio sí cuentan (27 y 15 conversiones respectivamente). Este hallazgo no cambió entre la primera y la segunda corrida — sigue pendiente de corrección.

**[NUEVO] De las 14 URL de campaña auditadas técnicamente, varias tienen tráfico real casi nulo en 30 días.** Ejemplos: `/preguntas-frecuentes-prescripcion-tributaria/` (3 vistas, 2 sesiones), `servicios./convenios-condonaciones/` (5 vistas, 1 sesión), `servicios./blog/perdonazo-tributario-2022/` (1 vista, 1 sesión). Vale la pena confirmar si estas páginas siguen recibiendo tráfico pagado activo o si son recursos legacy que ya no se están promocionando.

## Detalle GA4 por las 14 URL de campaña

| # | Categoría | URL | Vistas (30d) | Sesiones (30d) | Conversiones (30d) |
|---|---|---|---|---|---|
| 1 | Servicio — campaña Ads | defensordelcontribuyente.cl/cobranza-fiscal/ | 413 | 383 | 27 |
| 2 | Servicio — campaña Ads | defensordelcontribuyente.cl/prescripcion-tributaria/ | 445 | 410 | 14 |
| 3 | Servicio — campaña Ads | defensordelcontribuyente.cl/fiscalizacion-tributaria-citaciones-sii/ | 294 | 288 | 0 |
| 4 | Servicio — campaña Ads (servicios.) | servicios.defensordelcontribuyente.cl/convenios-condonaciones/ | 5 | 1 | 0 |
| 5 | FAQ | defensordelcontribuyente.cl/preguntas-frecuentes-prescripcion-tributaria/ | 3 | 2 | 0 |
| 6 | FAQ | defensordelcontribuyente.cl/preguntas-frecuentes-cobranza-fiscal/ | 15 | 13 | 0 |
| 7 | FAQ (servicios.) | servicios.defensordelcontribuyente.cl/faq-convenios-condonaciones/ | 2 | 1 | 0 |
| 8 | Casos de éxito | defensordelcontribuyente.cl/casos-exito-tributario/ | 0 | 0 | 0 |
| 9 | Casos de éxito | defensordelcontribuyente.cl/casos-de-exito/ | 35 | 31 | 0 |
| 10 | Blog | defensordelcontribuyente.cl/blog/prescriben-deudas-fiscales-chile/ | 146 | 143 | 0 |
| 11 | Blog (servicios.) | servicios.defensordelcontribuyente.cl/blog/ml-deudas-fiscales-cobranza-tesoreria/ | 2 | 1 | 0 |
| 12 | Blog (servicios.) | servicios.defensordelcontribuyente.cl/blog/ml-condonaciones-convenios/ | 3 | 1 | 0 |
| 13 | Blog (servicios.) | servicios.defensordelcontribuyente.cl/blog/perdonazo-tributario-2022/ | 1 | 1 | 0 |
| 14 | Herramienta de diagnóstico | diagnostico.defensordelcontribuyente.cldiagnostico.defensordelcontribuyente.cl/ | — | — | — (sin propiedad GA4) |

**Totales (13 URL con propiedad GA4):** 1364 vistas · 1275 sesiones · 41 conversiones.

## Propiedad: defensordelcontribuyente.cl
`properties/487864971`

| Campo | Valor |
|---|---|
| Creada | 2025-05-02 |
| Zona horaria | America/Santiago |
| Moneda | CLP |
| Categoría de industria | OTHER |
| Vínculo Google Ads | Sí — customer_id 8985279729, creado 2025-05-05 |

**Tráfico por canal — últimos 30 días**

| Canal | Sesiones | Usuarios | Tasa interacción | Duración media (s) | Tasa rebote |
|---|---|---|---|---|---|
| Paid Search | 1221 | 1082 | 54.6% | 128 | 45.4% |
| Organic Search | 536 | 461 | 57.6% | 173 | 42.4% |
| Direct | 197 | 163 | 27.9% | 97 | 72.1% |
| Referral | 24 | 19 | 54.2% | 197 | 45.8% |
| Organic Social | 18 | 17 | 77.8% | 35 | 22.2% |
| AI Assistant | 9 | 6 | 33.3% | 6 | 66.7% |
| Cross-network | 8 | 8 | 87.5% | 93 | 12.5% |
| Display | 5 | 2 | 80.0% | 691 | 20.0% |
| Organic Video | 1 | 1 | 100.0% | 149 | 0.0% |

**Eventos — últimos 30 días**

| Evento | Cantidad | Marcado como conversión |
|---|---|---|
| page_view | 2526 | No |
| session_start | 2022 | No |
| first_visit | 1703 | No |
| user_engagement | 1497 | No |
| scroll | 605 | No |
| form_start | 141 | No |
| click | 33 | No |
| form_submit_cobranza_fiscal | 27 | Sí (27) |
| form_submit_fiscalizacion_tributaria_cit | 19 | No |
| form_submit_prescripcion | 15 | Sí (15) |
| file_download | 13 | No |

## Propiedad: servicios.defensordelcontribuyente.cl
`properties/484039052`

| Campo | Valor |
|---|---|
| Creada | 2025-04-01 |
| Zona horaria | America/Santiago |
| Moneda | USD |
| Categoría de industria | INDUSTRY_CATEGORY_UNSPECIFIED |
| Vínculo Google Ads | Sí — customer_id 8985279729, creado 2025-05-07 |

**Tráfico por canal — últimos 30 días**

| Canal | Sesiones | Usuarios | Tasa interacción | Duración media (s) | Tasa rebote |
|---|---|---|---|---|---|
| Direct | 11 | 7 | 45.5% | 259 | 54.5% |
| Paid Search | 1 | 1 | 100.0% | 15 | 0.0% |

**Eventos — últimos 30 días**

| Evento | Cantidad | Marcado como conversión |
|---|---|---|
| page_view | 32 | No |
| user_engagement | 28 | No |
| scroll | 16 | No |
| session_start | 12 | No |
| first_visit | 8 | No |

## Priorización de acciones

| Prioridad | Acción | Por qué |
|---|---|---|
| 1 | Marcar `form_submit_fiscalizacion_tributaria_cit` como evento clave/conversión en GA4 | Confirmado en 2 corridas: 19 conversiones reales del mes no se cuentan |
| 2 | Confirmar con marketing si las URL de campaña con tráfico casi nulo siguen activas en campañas pagadas | 3+ de las 14 URL auditadas técnicamente tienen 1-5 vistas en 30 días — posible presupuesto mal dirigido o páginas legacy |
| 3 | Instrumentar GTM + GA4 en diagnostico.defensordelcontribuyente.cl | No existe propiedad GA4 para este subdominio |
| 4 | Instrumentar eventos personalizados en servicios.defensordelcontribuyente.cl | Cero eventos propios pese a formularios reales de campaña |
| 5 | Corregir moneda de la propiedad servicios. (USD → CLP) | Configuración inconsistente con el resto de la cuenta |

## Metodología y limitaciones

- Segunda corrida de esta auditoría (18 y 19-08-2026). En la primera, la sesión de Claude Code no logró cargar el servidor MCP y se usó un cliente manual (JSON-RPC directo sobre stdio). En esta segunda corrida el servidor cargó de forma nativa en la sesión, y todas las consultas se hicieron con la herramienta oficial integrada.
- Periodo de datos: 30daysAgo - yesterday (zona horaria de cada propiedad, America/Santiago). Los números pueden variar levemente entre corridas por el rolling window de fechas relativas.
- El cruce con las 14 URL de campaña usa exactamente las mismas URL de la Auditoría Técnica — 14 URL de Campañas y Recursos de Conversión (17-08-2026), buscando cada pagePath en el reporte de GA4 de la propiedad correspondiente según el dominio.
- No se pudo auditar diagnostico.defensordelcontribuyente.cl vía GA4 porque no existe una propiedad asociada a ese subdominio.
