# Backlog ClickUp — Consolidación y Auditoría GA4

**Fecha:** 18-08-2026 · **Estado:** Pre-auditoría — basado en hallazgos ya confirmados de auditorías previas (tracking, WordPress, 14 URL de campañas). **Formato:** tareas listas para crear como cards en ClickUp, uno por fila.

---

> **Nota de estado.** El servidor MCP oficial de Google Analytics (`googleanalytics/google-analytics-mcp`) quedó instalado y con credenciales reales configuradas en esta sesión de trabajo, pero requiere un reinicio de la sesión de Claude Code para cargar. Este backlog se armó con lo que **ya está confirmado** por auditorías anteriores (ausencia total de tracking en diagnostico., GTM duplicado en 8 de 14 URL, tres subdominios con instalaciones WordPress independientes). Apenas se ejecute la auditoría en vivo, este documento se complementa con datos reales de tráfico, conversión y calidad de eventos — no reemplaza esa auditoría, la prepara.

---

## 1. Consolidación de tracking (bloqueante para medir cualquier resultado)

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| G1 | Instalar Google Tag Manager + tag de configuración GA4 en diagnostico.defensordelcontribuyente.cl | Tarea | Agencia-prestador | Alto | 1-2 horas | Confirmado: 0 contenedores GTM en esta herramienta. Es el formulario de mayor intención del ecosistema y hoy no genera ni un evento en GA4 |
| G2 | Eliminar uno de los dos contenedores GTM duplicados (GTM-N7BQZZW / GTM-MQC692WV) en las 8 URL del dominio principal | Tarea | Agencia-prestador | Alto | 1-2 horas | Confirmado en la auditoría de 14 URL. Mientras ambos estén activos, cualquier evento de GA4 disparado desde GTM puede estar duplicándose (pageviews y conversiones infladas) |
| G3 🔒 | Verificar, tras G2, que el tag de configuración GA4 no quede disparando dos veces por página | Tarea | Agencia-prestador | Alto | 30 min | Criterio de aceptación: en Tag Assistant / DebugView, un `page_view` por carga de página, no dos |
| G4 | Confirmar cuántos Measurement ID de GA4 (G-XXXXXXX) están en uso hoy y en qué subdominios | Tarea | Agencia-prestador | Alto | 1 hora | Tres instalaciones WordPress independientes (dominio principal 6.8.8, servicios. 7.0.4, diagnostico. 6.7.5) — riesgo de que cada una tenga su propia configuración GA4 sin coordinar |
| G5 | Configurar cross-domain measurement entre defensordelcontribuyente.cl, servicios.defensordelcontribuyente.cl y diagnostico.defensordelcontribuyente.cl | Tarea | Agencia-prestador | Alto | 2-3 horas | Sin esto, un usuario que navega del dominio principal a servicios. o diagnostico. cuenta como sesión nueva y se pierde el recorrido real hasta la conversión |

## 2. Eventos de conversión

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| G6 | Marcar como conversión en GA4 el envío de formulario en las páginas de servicio, FAQ y diagnóstico | Tarea | Agencia-prestador | Alto | 1-2 horas | Depende de G1 para diagnostico. — hoy no hay evento que marcar ahí |
| G7 | Marcar como conversión los clics a WhatsApp (presente en 8 de 14 URL auditadas) y a teléfono | Tarea | Agencia-prestador | Alto | 1 hora | Confirmar que el clic dispara un evento medible (no solo un enlace `tel:`/`wa.me` sin tracking) |
| G8 | Definir junto al equipo qué cuenta como "lead calificado" para diferenciarlo de una simple visita al formulario | Tarea | Cliente-Estudio | Alto | 1 reunión (1 hora) | Insumo obligatorio para G9 |
| G9 | Configurar el evento de "lead calificado" (G8) como conversión clave en GA4 | Tarea | Agencia-prestador | Alto | 1-2 horas | Depende de G8 |

## 3. Vinculación con Google Ads y otras herramientas

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| G10 | Vincular la propiedad GA4 con la cuenta de Google Ads (AW-593050363) | Tarea | Agencia-prestador | Alto | 30 min | Habilita que las conversiones reales de GA4 (no solo el tag de conversión suelto de Ads) alimenten la optimización de campañas |
| G11 | Importar como conversión de Google Ads los eventos definidos en G6/G7/G9 | Tarea | Agencia-prestador | Alto | 1 hora | Depende de G10 |
| G12 | Evaluar instalación de Meta Pixel y, si corresponde, vincular sus eventos de conversión con los mismos hitos definidos en GA4 (G6/G7/G9) | Tarea | Cliente-Estudio decide · Agencia implementa | Alto | 2-3 horas | Confirmado: Meta Pixel ausente en las 14 URL auditadas. Bloqueante si se piensa pautar en Meta |

## 4. Calidad de datos y medición mejorada

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| G13 | Revisar configuración de Enhanced Measurement (scroll, clics salientes, descargas de archivo, búsqueda en el sitio) | Tarea | Agencia-prestador | Medio | 1 hora | Estándar de GA4, verificar que no quede desactivado por defecto |
| G14 | Excluir tráfico interno (equipo del Estudio y agencia) de los reportes de GA4 | Tarea | Agencia-prestador | Medio | 30 min | Evita que pruebas internas infle métricas de tráfico/conversión |
| G15 | Configurar retención de datos y accesos de usuario en la propiedad GA4 (quién ve qué) | Tarea | Cliente-Estudio define accesos · Agencia configura | Bajo | 1 hora | Alinear con quién administra la cuenta tras el traspaso a la agencia |

## 5. Auditoría en vivo (pendiente de reinicio de sesión)

| # | Tarea / Activo | Tipo | Responsable | Impacto | Tiempo estimado | Notas / criterios de aceptación |
|---|---|---|---|---|---|---|
| G16 | Ejecutar auditoría GA4 en vivo con datos reales (tráfico, conversiones, embudos, tiempo real) vía MCP oficial | Tarea | Cliente-Estudio (vía Claude Code) | Alto | 10-15 min | Requiere reiniciar la sesión de Claude Code para cargar el servidor `analytics-mcp` ya configurado. Complementa este backlog con hallazgos reales |

---

## Resumen para ClickUp

- **16 tareas** (G1-G16), de las cuales 10 son de Agencia-prestador, 3 son conjuntas (Cliente-Estudio define/aprueba, Agencia implementa), 2 son de Cliente-Estudio, y 1 es de ejecución directa vía Claude Code.
- Prioridad de secuencia sugerida: **1 (tracking) → 2 (conversiones) → 3 (vinculación Ads/Meta) → 4 (calidad de datos)**. La sección 5 puede correr en paralelo apenas se reinicie la sesión — no bloquea el resto.
