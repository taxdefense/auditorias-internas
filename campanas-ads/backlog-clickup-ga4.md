# Backlog ClickUp — Consolidación y Auditoría GA4

**Fecha:** 19-08-2026 (segunda corrida, reemplaza la versión del 18-08-2026) · **Estado:** Confirmado con datos reales — ver [Auditoría Completa GA4](auditoria-ga4-completa.md). **Formato:** tareas listas para crear como cards en ClickUp, uno por fila.

---

> **Nota de método.** En la primera corrida (18-08-2026), la sesión interactiva de Claude Code no logró cargar el servidor MCP de Google Analytics recién instalado, ni tras un reinicio, y se conectó manualmente hablando el protocolo MCP (JSON-RPC sobre stdio) directamente contra el proceso `pipx run analytics-mcp`. En esta segunda corrida (19-08-2026) el servidor cargó de forma nativa en la sesión y todas las consultas se hicieron con la herramienta oficial integrada — mismos resultados, sin diferencias relevantes entre ambas corridas. Los datos de este backlog son reales en ambos casos, no estimados.

---

## 1. Corrección de conversiones (impacto inmediato, sin desarrollo)

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| G1 | Marcar `form_submit_fiscalizacion_tributaria_cit` como evento clave (conversión) en GA4 | Tarea | Agencia-prestador | Alto | 15 min | Confirmado: 19 eventos en 30 días, 0 marcados como conversión, mientras que form_submit_cobranza_fiscal (27/27) y form_submit_prescripcion (15/15) sí lo están. Cambio de configuración, no de código |
| G2 | Importar `form_submit_fiscalizacion_tributaria_cit` como conversión en Google Ads, igual que los otros 2 | Tarea | Agencia-prestador | Alto | 15 min | Depende de G1 |

## 2. Tracking ausente (bloqueante para medir resultado)

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| G3 | Instalar Google Tag Manager + tag de configuración GA4 en diagnostico.defensordelcontribuyente.cl | Tarea | Agencia-prestador | Alto | 1-2 horas | Confirmado: no existe ninguna propiedad GA4 asociada a este subdominio. Es el formulario de mayor intención del ecosistema y hoy no genera ni un evento en GA4 |
| G4 | Instrumentar eventos `form_start` / `form_submit_*` / `click` en la propiedad GA4 de servicios.defensordelcontribuyente.cl | Tarea | Agencia-prestador | Alto | 2-3 horas | Confirmado: esta propiedad solo registra los eventos automáticos de GA4 (page_view, session_start, first_visit, scroll, user_engagement) — cero eventos personalizados pese a tener formularios reales de campaña |
| G5 | Instrumentar eventos distintos para clics a WhatsApp y a teléfono | Tarea | Agencia-prestador | Medio | 1-2 horas | Hoy existe un único evento genérico `click` (33 en 30 días en el dominio principal) sin desglose por destino |

## 3. Configuración de propiedad

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| G6 | Corregir moneda de la propiedad servicios. (hoy USD) a CLP | Tarea | Agencia-prestador | Medio | 15 min | El dominio principal ya está en CLP; servicios. quedó en USD por defecto |
| G7 | Definir categoría de industria en la propiedad servicios. (hoy sin especificar) | Tarea | Agencia-prestador | Bajo | 15 min | El dominio principal tiene "OTHER"; servicios. está en `INDUSTRY_CATEGORY_UNSPECIFIED` |
| G8 | Decidir si servicios.defensordelcontribuyente.cl sigue siendo una propiedad GA4 separada o se consolida | Tarea | Cliente-Estudio decide · Agencia ejecuta | Alto | 1 reunión | Con 12 sesiones/30 días y cero eventos personalizados, hoy es prácticamente un dato muerto. Definir esto antes de invertir en G4 |

## 4. Cross-domain y arquitectura de medición

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| G9 | Configurar cross-domain measurement o rollup entre las propiedades del dominio principal y servicios. (si G8 decide mantenerlas separadas) | Tarea | Agencia-prestador | Alto | 2-3 horas | Confirmado: son 2 propiedades GA4 sin relación entre sí — un usuario que cruza de un dominio a otro genera una sesión nueva en una propiedad distinta |

## 5. Experiencia de conversión

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| G10 | Investigar por qué el 57% de quienes inician un formulario no lo terminan (141 `form_start` vs 61 `form_submit_*` en 30 días, dominio principal) | Tarea | Cliente-Estudio + Agencia (revisión conjunta) | Alto | 1-2 horas de análisis + ajustes según hallazgo | Puede ser largo del formulario, campos innecesarios, o fricción de UX — revisar antes de invertir más presupuesto en llevar tráfico a ese mismo formulario |
| G11 | Confirmar si las URL de campaña con tráfico casi nulo en 30 días siguen activas en campañas pagadas | Tarea | Cliente-Estudio + Agencia (revisión conjunta) | Medio | 1 hora | Del cruce con las 14 URL de la auditoría técnica: `/preguntas-frecuentes-prescripcion-tributaria/` (3 vistas), `servicios./convenios-condonaciones/` (5 vistas/1 sesión), `servicios./blog/perdonazo-tributario-2022/` (1 vista) — confirmar si son recursos legacy o si debería llegarles más tráfico |

---

## Tareas de la versión anterior ya confirmadas como completas (no requieren acción)

- ~~Vincular la propiedad GA4 con la cuenta de Google Ads~~ — **confirmado: ya está hecho** en ambas propiedades (customer_id 8985279729, vinculado desde mayo 2025 por tributariodefensor@gmail.com).

---

## Resumen para ClickUp

- **11 tareas** (G1-G11): 7 de Agencia-prestador, 2 conjuntas (Cliente-Estudio decide/revisa, Agencia ejecuta), 2 de reunión/revisión conjunta.
- **Quick wins (< 30 min, sección 1 y parte de 3):** G1, G2, G6, G7 — resuelven la pérdida de 19 conversiones/mes y dos errores de configuración, sin desarrollo.
- Prioridad de secuencia sugerida: **1 (conversiones) → 2 (tracking ausente) → 3 (configuración) → 4 (cross-domain, depende de decisión en G8) → 5 (experiencia de conversión, puede correr en paralelo)**.
