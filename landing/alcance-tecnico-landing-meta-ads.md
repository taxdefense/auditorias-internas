# Alcance Técnico — Landing Page y Meta Ads

**Sitio:** defensordelcontribuyente.cl
**Fecha:** 19 de agosto de 2026 (segunda corrida — línea base: 17 de agosto de 2026, complementada ahora con datos reales de GA4)
**Preparado para:** equipo de marketing entrante

## Resumen del alcance

Este documento detalla las modificaciones requeridas en la landing page y la puesta a punto necesaria antes de operar campañas en Meta Ads, ordenadas por prioridad. Esta versión incorpora datos reales de comportamiento obtenidos vía el MCP oficial de Google Analytics (ver [Auditoría Completa GA4](../campanas-ads/auditoria-ga4-completa.md)), que antes no estaban disponibles.

## Datos reales de conversión (nuevo — vía GA4, últimos 30 días)

| Canal | Sesiones | Tasa de rebote | Duración media |
|---|---|---|---|
| Paid Search | 1.221 | 45.4% | 128s |
| Organic Search | 536 | 42.4% | 173s |
| **Direct** | 197 | **72.1%** | 97s |

- **El tráfico Direct tiene casi el doble de rebote que Paid Search** (72% vs 45%) — quien llega directo a la landing (probablemente de campañas offline, WhatsApp compartido, o recordación de marca) no encuentra lo que busca tan rápido como quien llega desde un anuncio con mensaje específico.
- De los 3 formularios de servicio con tracking, **Cobranza Fiscal (27 conversiones/mes) y Prescripción Tributaria (14/mes) sí convierten y se cuentan**; **Fiscalización Tributaria tiene 19 envíos reales pero 0 marcados como conversión** — error de configuración en GA4, no de la landing (ver Backlog ClickUp GA4, tarea G1).
- **57% de quienes inician un formulario no lo terminan** (141 `form_start` vs 61 `form_submit_*` completados en 30 días) — esto sí es un problema de la landing/formulario, no de medición.

## Prioridad 1 — Tracking y medición (crítico, bloqueante para pautar)

- Instalar el Meta Pixel en la totalidad del sitio — **confirmado ausente** en las 14 URL de campaña auditadas.
- Configurar el evento `Lead` para que se dispare al enviar el formulario de consulta (y, si existe, el formulario de contacto por WhatsApp).
- Resolver la duplicidad de Google Tag Manager (ver Alcance Técnico — SEO, Prioridad 1) — afecta también la medición de campañas.
- Confirmar el estado actual de la cuenta de Meta Business Manager: campañas activas, históricas, y auditorías previas si existieran.

## Prioridad 2 — Optimización de conversión (CRO)

- **Investigar el 57% de abandono de formulario** (dato real GA4) — revisar largo del formulario, campos innecesarios o fricción de UX antes de invertir más presupuesto en tráfico hacia ese mismo formulario.
- **Investigar por qué el tráfico Direct rebota un 72%** — probablemente necesita un mensaje de bienvenida o contexto distinto al de quien llega desde un anuncio específico.
- Diseñar y probar una versión simplificada del formulario (nombre + teléfono) específica para tráfico frío proveniente de Meta.
- Variar el texto del CTA entre las distintas secciones de la página en lugar de repetir el mismo texto.
- Reforzar la propuesta de valor específica (deuda con el SII/Tesorería) desde el primer bloque visible de la página.

## Prioridad 3 — Prueba social

- Incorporar prueba social numérica (casos resueltos, años de operación) en la home, complementando los testimonios en video ya existentes.

## Prioridad 4 — Campañas

- Publicar el set de anuncios del Anexo A (5 variantes con ángulos distintos) como primera tanda de testing, una vez resuelto el Meta Pixel (Prioridad 1).
- Reportar estructura de campañas, presupuesto y resultados de forma quincenal: CTR, CPC, ROAS y costo por lead, segmentado por campaña.

## Anexo A — Anuncios listos para publicar

*(sin cambios respecto a la línea base del 17-08-2026 — ver versión anterior del documento para el detalle de las 5 variantes de ángulo)*

## Criterios de aceptación

| Punto | Cómo se valida |
|---|---|
| Meta Pixel activo | Evento visible en el Administrador de Eventos de Meta al probar el formulario |
| Abandono de formulario reducido | Tasa de form_submit/form_start sobre el 43% actual, medida en GA4 |
| Formulario corto probado | Reporte de test A/B con al menos 2 semanas de datos |
| Prueba social numérica | Visible en la home sin necesidad de scroll adicional |
| Reporte de campañas | Entrega quincenal con las métricas indicadas |
