# Plan de ajustes post-CAE y backlog para ClickUp

**Punto 1 del brief de ejecución** ([`brief-ejecucion-ajustes-2026-08.md`](brief-ejecucion-ajustes-2026-08.md)) · **Fecha:** 18-08-2026 · **Fuente única:** [Auditoría de cuenta Meta Ads — 17-08-2026](auditoria-cuenta-meta-ads.md) (Auditoría 1 de Meta). Este documento no incorpora hallazgos de la investigación 2 ni del punto 3.

---

## 1. Registro de cambios sobre la Auditoría 1

| # | Cambio | Dónde | Motivo |
|---|---|---|---|
| 1 | Se agrega nota de ajuste al inicio del informe (.md y .html) | `auditoria-cuenta-meta-ads.md`, `auditoria-cuenta-meta-ads.html` | Documentar que las campañas CAE no se eliminan del historial, pero se descuentan como palanca de alcance inmediato |
| 2 | El hallazgo "La única campaña activa es la menos eficiente" se mantiene, con aclaración de que el dato de eficiencia CAE es histórico, no una acción disponible hoy | Sección "Los dos hallazgos que más cuestan" | Evitar que se lea como recomendación de reactivación inmediata |
| 3 | Ítem "Reactivar las 3 campañas CAE pausadas" se retira del checklist de impacto Alto y se reemplaza por "Pausar/reducir Diagnósticos Gratuitos mientras se refresca su creativo" como ítem Alto independiente | Checklist priorizado (.md y .html) | La reactivación ya no es ejecutable sin actualizar oferta primero |
| 4 | README del repo: orden de prioridad sugerido, ítem 2 reescrito | `README.md` | Reflejar que la prioridad 2 ya no es "reactivar CAE" sino "refrescar creativo activo" |
| 5 | Se agregan 2 tareas nuevas no existentes en la Auditoría 1: actualizar oferta CAE vigente, y evaluar relanzamiento como campaña nueva | Este documento, sección 3 | Dar continuidad accionable al hallazgo CAE sin perder el dato de eficiencia |

**Lo que NO cambia:** puntuación global (43/100), hallazgo de medición (Pixel solo con PageView), GTM duplicado, fatiga de "Video 22", coherencia oferta↔landing, audiencias lookalike inactivas, compliance del creativo con cita de tercero. Todos los demás hallazgos y su prioridad relativa se mantienen íntegros.

---

## 2. Regla de responsables

- **Agencia-prestador:** ejecución técnica en Ads Manager, Meta Business Suite, GTM/Pixel, diseño y publicación de landing. Es quien tiene (o debe tener) acceso administrador a la cuenta.
- **Cliente-Estudio:** decisiones de negocio, oferta y condiciones legales/tributarias vigentes, aprobación de contenido, compliance (uso de imagen/testimonios), acceso y credenciales de las cuentas propias.
- Cuando una tarea requiere a ambos, se lista una vez con responsable **principal** y una nota de quién aprueba/entrega insumo.

---

## 3. Backlog para ClickUp

> Formato pensado para copiar/pegar como lista de tareas: Nombre — Responsable — Impacto — Tiempo estimado — Notas. Cada tarea es una sola tarjeta ClickUp; el campo "Responsable" mapea a un único assignee.

### Lista "Ajuste CAE" (nuevo, deriva del hallazgo #1 de la Auditoría 1)

| Tarea | Responsable | Impacto | Tiempo estimado | Notas |
|---|---|---|---|---|
| Actualizar oferta y condiciones CAE vigentes (montos, plazos, programa) en el copy y en los 3 creativos CAE pausados | **Cliente-Estudio** | Alto | A definir por equipo legal | Insumo obligatorio antes de que Agencia pueda relanzar cualquier campaña con ángulo CAE. Sin esto, la tarea de Agencia queda bloqueada |
| Relanzar ángulo CAE como campaña nueva (no reactivación) una vez aprobada la oferta actualizada | **Agencia-prestador** | Alto (potencial, condicionado) | 15-30 min en Ads Manager una vez recibido el insumo | Depende 100% de la tarea anterior. Nomenclatura nueva, no reutilizar el naming de abril 2026 |

### Lista "Impacto Alto" (Auditoría 1)

| Tarea | Responsable | Impacto | Tiempo estimado | Notas |
|---|---|---|---|---|
| Pausar o reducir presupuesto de "Diagnósticos Gratuitos" mientras se refresca su creativo | **Agencia-prestador** | Alto | 15 min | Aprobación de Cliente-Estudio antes de tocar la única campaña activa hoy |
| Configurar evento Lead/Contact en el Pixel (GTM o Conversions API), disparado en envío de formulario y clic a WhatsApp | **Agencia-prestador** | Alto | 2-4 horas (requiere acceso GTM) | Bloqueante para medir cualquier resultado real; ya señalado también en el alcance técnico de landing |
| Refrescar o pausar "Video 22" y activar 2-3 creativos nuevos del banco de 70 | **Agencia-prestador** (publicación) — **Cliente-Estudio** (selección/aprobación del creativo) | Alto | 30 min de publicación | Meta ya diagnosticó "This ad is not spurring interest" |

### Lista "Impacto Medio"

| Tarea | Responsable | Impacto | Tiempo estimado | Notas |
|---|---|---|---|---|
| Resolver GTM duplicado (2 contenedores, cada uno cargado 2 veces) | **Agencia-prestador** | Medio-alto | 1-2 horas | Bloqueante ya identificado en el alcance técnico; sigue pendiente |
| Agregar variantes de imagen junto al video en el conjunto activo | **Agencia-prestador** | Medio | 20 min | Recomendación directa de Meta, +4 pts de Opportunity Score |
| Unificar CTAs de la landing a un solo mensaje y simplificar formulario (sin RUT en primer contacto) | **Agencia-prestador** | Medio | 1-2 horas de diseño/dev | Cliente-Estudio aprueba el CTA final antes de publicar |
| Reactivar las 3 audiencias lookalike en un conjunto de prueba | **Agencia-prestador** | Medio | 15 min | Ya están construidas, sin costo de mantenerlas encendidas |

### Lista "Impacto Bajo"

| Tarea | Responsable | Impacto | Tiempo estimado | Notas |
|---|---|---|---|---|
| Corregir nomenclatura de campañas (fechas inconsistentes) | **Agencia-prestador** | Bajo | 15 min | Orden y trazabilidad interna |
| Revisar compliance del creativo que cita a un tercero por su usuario de red social (@rfantuzzih) | **Cliente-Estudio** | Bajo (riesgo si se ignora) | A definir con equipo legal | Confirmar autorización de uso antes de reactivar ese creativo específico; bloquea su reactivación, no las del resto del banco |

---

## 4. Resumen para ClickUp (conteo)

- **Agencia-prestador:** 8 tareas (1 condicionada al insumo de Cliente-Estudio).
- **Cliente-Estudio:** 3 tareas (2 son insumo/bloqueante para tareas de Agencia).
- **Total:** 11 tareas, 0 con responsable compartido/ambiguo.
