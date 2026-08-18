# Auditoría de cuenta Meta Ads — Defensor del Contribuyente

**Cuenta:** 949295082543787 (CLP) · **Generado:** 17-08-2026 · **Fuente:** acceso directo vía Meta Ads MCP (datos reales de la cuenta conectada, no Biblioteca de Anuncios pública).

Versión visual completa: [`auditoria-cuenta-meta-ads.html`](auditoria-cuenta-meta-ads.html) · Versión editable: [`/descargables/Auditoria-Cuenta-Meta-Ads.docx`](../descargables/Auditoria-Cuenta-Meta-Ads.docx)

## Puntuación global: 43/100 — Campaña con problemas, correcciones necesarias

| Dimensión | Puntaje |
|---|---|
| Salud de cuenta y entrega | 15/15 |
| Estructura y foco de campañas | 5/20 |
| Frescura y rotación creativa | 4/20 |
| Medición y atribución | 3/15 |
| Coherencia oferta ↔ landing | 9/15 |
| Audiencias y segmentación | 7/15 |

## Los dos hallazgos que más cuestan

1. **La única campaña activa es la menos eficiente.** "Diagnósticos Gratuitos" (activa desde abril 2025) cuesta $1.099 CLP por conversación. Las 3 campañas CAE, pausadas desde abril de 2026, lograron $373–$649 CLP — hasta 3x más eficientes — y siguen apagadas.
2. **No hay evento de conversión medido.** El Pixel (524558258682248) está activo y dispara hoy mismo, pero solo registra `PageView`. No hay Lead, Contact ni clic a WhatsApp. Nadie sabe cuántas de las conversaciones iniciadas en Messenger/WhatsApp terminan siendo clientes.

## Estructura de campañas (histórico completo)

| Campaña | Estado | Gasto | CTR | CPC | Costo/resultado | Resultados |
|---|---|---|---|---|---|---|
| Diagnósticos Gratuitos (21-04-2025) | **Activa** | $5.338.077 | 1,48% | $283 | **$1.099** | 4.858 |
| Estrategia CAE Centralizada | Pausada | $901.929 | 2,14% | $121 | **$470** | 1.920 |
| Prescripción CAE | Pausada | $50.000 | 3,21% | $120 | **$373** | 134 |
| Defensa CAE | Pausada | $50.000 | 2,34% | $226 | $649 | 77 |
| Ley de alivio tributario | Pausada | $65.765 | 1,47% | $202 | $1.461 | 45 |
| Tráfico – Página Diagnóstico | Pausada | $256 | 4,13% | $18 | $28 | 9 (clics) |

El único anuncio activo, **"Video 22"**, concentra el 71% del gasto de su campaña, lleva 16 meses sin refrescarse y Meta lo clasifica en el **bottom 35% de interacción**, con el diagnóstico textual: *"This ad is not spurring interest."*

## Banco creativo: 70 creativos, 1 activo

Ángulos ya producidos: miedo/urgencia (embargo, cobranza fiscal), curiosidad (¿deuda prescrita?, CAE), oferta (diagnósticos gratuitos), autoridad (+10 años) y testimonio real (Silvana, Ramón López, casos de éxito). El problema no es falta de material — es falta de rotación.

⚠️ Revisar antes de reactivar: un creativo cita a un tercero por su usuario de red social (`@rfantuzzih`) — confirmar autorización de uso.

## Medición y tracking

- **GTM duplicado** (`GTM-MQC692WV` y `GTM-N7BQZZW`, cada uno cargado 2 veces): ya documentado como bloqueante #1 en el [alcance técnico de este mismo repositorio](../README.md) — **sigue sin resolverse**.
- Pixel activo pero solo mide `PageView`. Falta evento de Lead/Contact.

## Audiencias

Audiencia "Personas con deudas CAE" activa y sana (3.800–4.500). Audiencia de visitantes del sitio casi vacía (~20 en 180 días, coherente con estrategia WhatsApp-first). 3 audiencias lookalike ya construidas pero **inactivas**.

## Checklist priorizado

| Impacto | Acción |
|---|---|
| Alto | Reactivar las 3 campañas CAE pausadas; reducir/pausar "Diagnósticos Gratuitos" mientras se refresca su creativo |
| Alto | Configurar evento Lead/Contact en el Pixel (GTM o Conversions API) |
| Alto | Refrescar "Video 22" con creativos ya disponibles del banco de 70 |
| Medio | Resolver GTM duplicado |
| Medio | Agregar variantes de imagen junto al video (recomendación directa de Meta, +4 pts Opportunity Score) |
| Medio | Unificar CTAs de la landing a uno solo; simplificar formulario |
| Medio | Reactivar las 3 audiencias lookalike |
| Bajo | Corregir nomenclatura de campañas (fechas inconsistentes) |
| Bajo | Revisar compliance del creativo con cita de tercero |

Detalle completo, benchmarks de sector, auditoría de landing y pack de 5 anuncios nuevos listos para lanzar: ver [HTML](auditoria-cuenta-meta-ads.html) o [Word](../descargables/Auditoria-Cuenta-Meta-Ads.docx).
