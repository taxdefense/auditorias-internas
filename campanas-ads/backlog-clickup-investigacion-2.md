# Backlog ClickUp — Investigación 2 (políticas y algoritmo Meta 2026)

**Fecha:** 18-08-2026 · **Fuente única:** [Investigación 2 — políticas y algoritmo Meta 2026](investigacion-2-politicas-algoritmo-meta.md) · **Formato:** tareas y activos listos para crear como cards en ClickUp, uno por fila.

---

## Reglas que aplican a todo este backlog

> **Exclusión CAE.** Este backlog no incluye ninguna instrucción para activar, reactivar o lanzar campañas o audiencias asociadas a la deuda CAE. La audiencia y las 3 campañas CAE siguen supeditadas a la actualización de oferta pendiente del Cliente-Estudio (ver [plan-ajustes-post-cae-clickup.md](plan-ajustes-post-cae-clickup.md)). Donde la Investigación 2 mencionaba la audiencia "Personas con deudas CAE" como semilla de Advantage+, esa mención se excluyó explícitamente de las tareas de abajo.

> **Regla de compliance de copy.** Ningún copy producido o revisado a partir de este backlog puede afirmar o implicar directamente, en segunda persona, que el espectador individual tiene una deuda tributaria (ej. "tú le debes al SII"). Todo copy debe mantener encuadre de tercera persona o estadístico (ej. "miles de contribuyentes..."). Esta regla es criterio de aceptación obligatorio en toda tarea de esta lista marcada con 🔒 y aplica también, hacia adelante, a cualquier creativo del banco de 70 que se reactive.

---

## 1. Pixel y medición — Conversions API de mensajería

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| T1 | Activar destino WhatsApp con Click-to-WhatsApp (CTWA) en las campañas activas, si no está ya configurado | Tarea | Agencia-prestador | Alto | 30 min | Precondición técnica para T2 |
| T2 | Conectar Conversions API (CAPI) de mensajería, enlazada por `ctwa_clid` | Tarea | Agencia-prestador | Alto | 2-4 horas | Requiere acceso a Meta Business Suite / WhatsApp Business API |
| T3 | Definir, junto al equipo de atención, qué conversación de WhatsApp cuenta como "lead calificado" | Tarea | Cliente-Estudio | Alto | 1 reunión (1 hora) | Insumo obligatorio para T4; sin esta definición no hay evento que reenviar |
| T4 | Reenviar a Meta el evento "lead calificado" vía CAPI usando el mismo `ctwa_clid` | Tarea | Agencia-prestador | Alto | 2-3 horas | Depende de T2 y T3. Habilita T14 (objetivo Leads) |

## 2. Contenido con IA vs. sin IA

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| T5 | Verificar y activar el control de divulgación de IA en Ads Manager en todo material con avatar IA | Tarea | Agencia-prestador | Medio | 1 hora | No basta el rótulo visual en el video; Meta detecta origen IA automáticamente desde el 01-06-2026 |
| T6 🔒 | Documentar criterio de uso: avatar IA para prospección fría / testeo de ángulo; testimonio real para audiencias cálidas y remarketing | Tarea | Cliente-Estudio aprueba · Agencia documenta | Medio | 2 horas | Queda como estándar escrito para todo creativo nuevo, no solo para el banco actual |

## 3. Video de personas reales vs. video editado

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| T7 | Instrumentar hook rate y hold rate como métricas de diagnóstico estándar para cada pieza nueva | Tarea | Agencia-prestador | Medio | 2 horas (setup de reporte) | Métrica de seguimiento, no de un solo uso |
| T8 | Definir estándar de duración por tipo de ángulo: 15-20s para miedo/urgencia, 30-50s para explicativo/autoridad | Tarea | Cliente-Estudio + Agencia (brief conjunto) | Medio | 1 reunión | Se aplica como checklist de producción para todo creativo nuevo |

## 4. Formatos sugeridos por Meta (imagen + video)

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| T9 | Aplicar la recomendación "mixed_formats" en el ad set activo: agregar variante de imagen al video existente | Tarea | Agencia-prestador | Alto | 20 min | Acción directa y gratuita ya identificada por Meta en vivo; +4 pts de Opportunity Score |
| T10 🔒 | Seleccionar y subir 10-20 creativos variados del banco de 70 para alcanzar el mínimo que pide Advantage+ Creative | Tarea | Cliente-Estudio selecciona · Agencia publica | Alto | 2-3 horas | Todo creativo seleccionado pasa primero por el checklist de T15 |

## 5. Algoritmo de entrega y fatiga creativa 2026

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| T11 | Definir calendario de rotación de creativos (semanal a quincenal) | Tarea | Agencia-prestador propone · Cliente-Estudio aprueba | Alto | 1 reunión | El ciclo de fatiga 2026 es de 5-7 días, no 14-21 |
| T12 | Configurar alertas de fatiga como gatillo automático de reemplazo: CTR con caída superior a 20%, frecuencia superior a 3,0, relevance score menor a 6/10 | Tarea | Agencia-prestador | Medio | 1-2 horas | Reemplazar por gatillo de dato, no por percepción de "se ve viejo" |

## 6. Configuraciones de cuenta y campaña

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| T13 | Activar como semilla de Advantage+ Audience las audiencias lookalike ya construidas | Tarea | Agencia-prestador | Medio | 15 min | **Excluye expresamente** la audiencia/lookalike de naming CAE — solo aplica a segmentación general, sin oferta CAE |
| T14 | Testear el objetivo "Leads" (en paralelo a Conversations) en un ad set piloto | Tarea | Agencia-prestador | Medio (condicionado) | 30 min de setup | Depende de T4 — sin señal de calidad vía CAPI, Meta no puede optimizar por calidad de lead |

## 7. Compliance de copy y categoría restringida

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| T15 🔒 | Crear checklist formal de compliance de copy (regla de tercera persona/estadístico, ver reglas arriba) | Tarea | Cliente-Estudio define · Agencia implementa como paso de aprobación previo a publicar | Alto | 2 horas | Checklist obligatorio antes de publicar cualquier pieza nueva o reactivada |
| T16 🔒 | Auditar el banco de 70 creativos existente contra ese checklist antes de reactivar cualquiera | Tarea | Cliente-Estudio | Alto | 1 día (revisión por lotes) | Ningún creativo se reactiva sin pasar esta auditoría |
| T17 | Revisar en Business Manager si la cuenta tiene alguna bandera de categoría "servicios financieros" | Tarea | Agencia-prestador | Bajo | 30 min | Preventivo — no hay evidencia de bloqueo hoy, pero conviene confirmar |

## Activos ya disponibles para desplegar (no son tareas nuevas)

| # | Activo | Por qué importa | Tarea vinculada |
|---|---|---|---|
| A1 | Banco de 70 creativos (testimonio real, avatar IA rotulado, slide informativo) | Cubre de sobra el mínimo de 10-20 assets que pide Advantage+ Creative, sin producción nueva | T10, T16 |
| A2 | Evento de optimización ya activo `onsite_conversion.messaging_deep_conversation` | Es una señal más avanzada que "conversación iniciada"; solo falta conectarlo a CAPI para medir calidad real | T2, T4 |
| A3 | Configuración estructural de cuenta (Opportunity Score 96/100) | Confirma que el foco debe ir 100% a ejecución (creativo + medición), no a ajustes de cuenta | Contexto — sin tarea directa |
| A4 | Audiencias lookalike ya construidas (excluida la de naming CAE) | Insumo listo para Advantage+ Audience sin costo de reconstrucción | T13 |

---

## Resumen para ClickUp

- **17 tareas** (T1-T17) + **4 activos de referencia** (A1-A4) = 21 cards.
- **Agencia-prestador:** 11 tareas (algunas condicionadas a insumo de Cliente-Estudio).
- **Cliente-Estudio:** 4 tareas exclusivas + 3 compartidas con aprobación/definición.
- **Marcadas 🔒 (criterio de aceptación de compliance de copy obligatorio):** T6, T10, T15, T16.
- **Cero tareas de activación de servicios o audiencias CAE** — exclusión aplicada en T13 y en la nota de reglas.
