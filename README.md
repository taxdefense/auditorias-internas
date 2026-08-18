# Auditorías Internas — Defensor del Contribuyente

Alcance técnico para el traspaso de la presencia digital (WordPress/Elementor, landing y Meta Ads) a la agencia de marketing entrante.

## Documentos

- [Alcance Técnico — SEO](seo/alcance-tecnico-seo.md)
- [Alcance Técnico — Landing Page y Meta Ads](landing/alcance-tecnico-landing-meta-ads.md)
- [Auditoría técnica — 14 URL de campañas y recursos de conversión](campanas-ads/auditoria-14-urls.md) — complementada 18-08-2026 con resultados Lighthouse (rendimiento, accesibilidad, buenas prácticas, SEO, visibilidad IA) por cada URL
- [Auditoría de cuenta Meta Ads (datos reales vía MCP) — 17-08-2026](campanas-ads/auditoria-cuenta-meta-ads.md) — ajustada 18-08-2026 (alcance CAE descontado)
- [Plan de tareas post-ajuste CAE (backlog ClickUp)](campanas-ads/plan-ajustes-post-cae-clickup.md)
- [Investigación 2 — políticas y algoritmo Meta 2026](campanas-ads/investigacion-2-politicas-algoritmo-meta.md)
- [Guiones y configuración de anuncios — 7 temas](campanas-ads/guiones-y-configuracion-7-temas.md)
- [Backlog ClickUp — Investigación 2](campanas-ads/backlog-clickup-investigacion-2.md) (excluye CAE, copy en 3ª persona)
- [Brief de ejecución de los 3 puntos](campanas-ads/brief-ejecucion-ajustes-2026-08.md)
- [Auditoría Completa GA4](campanas-ads/auditoria-ga4-completa.md) — actualizada 19-08-2026 (segunda corrida, conexión nativa al MCP), datos reales de las 2 propiedades GA4 más el cruce de tráfico/conversiones para cada una de las 14 URL de campaña
- [Backlog ClickUp — Consolidación y Auditoría GA4](campanas-ads/backlog-clickup-ga4.md) — actualizado 19-08-2026, confirmado con datos reales (11 tareas Agencia-prestador / Cliente-Estudio)
- [Estructura de Tareas ClickUp — Paid Media & Growth (Constanza Zárate)](clickup/estructura-tareas-clickup.md): desglose de tareas/assets del contrato vigente (17-ago-2026) por Carpeta/Lista/Tarea, con responsable, naturaleza contractual, recurrencia y plataforma, listo para crear el Espacio en ClickUp.
- [Guía 360° de Marketing Digital para Pymes (2026)](estrategia-360/guia-marketing-digital-360-pyme.md): auditoría cruzada de SEO, SEM (Google/Meta/TikTok/LinkedIn), Funnels comerciales, redes orgánicas y AEO/GEO, contrastada contra el estado del arte de agencias de referencia y las políticas vigentes de las plataformas (18-ago-2026). Checklist priorizado y matriz de qué hacer primero. Se actualiza con la skill `auditoria-360-mkt-digital` (modo actualización).

Versiones editables en Word: carpeta [`/descargables`](descargables/). El desglose ClickUp también incluye un CSV plano en [`/descargables/Tareas-ClickUp-Import.csv`](descargables/Tareas-ClickUp-Import.csv) para adaptar al importador de ClickUp.

## Orden de prioridad sugerido

1. Consolidar tracking (Google Tag Manager duplicado, evento de Lead ausente en el Pixel) — bloqueante para medir cualquier resultado posterior. Confirmado vigente en la [auditoría de cuenta del 17-08-2026](campanas-ads/auditoria-cuenta-meta-ads.md). *(Ajuste 18-08-2026: la [auditoría GA4](campanas-ads/auditoria-ga4-completa.md) confirma un quick win de menos de 30 min dentro de este mismo punto — un evento de conversión de Fiscalización Tributaria no está marcado como tal, perdiendo 19 conversiones reales del último mes.)*
2. Refrescar el anuncio activo con fatiga confirmada y reducir/pausar "Diagnósticos Gratuitos" mientras se refresca. *(Ajuste 18-08-2026: reactivar las campañas CAE pausadas deja de ser acción inmediata — su oferta/creativo está desactualizado. Se mantienen documentadas como referencia de eficiencia, no como palanca de alcance disponible hoy. Detalle: [plan-ajustes-post-cae-clickup.md](campanas-ads/plan-ajustes-post-cae-clickup.md).)*
3. Rendimiento y accesibilidad (SEO).
4. Optimización de conversión de la landing.
5. Actualización de plataforma (WordPress/Elementor).
6. Lanzamiento de campañas nuevas.
7. Puesta en marcha operativa con la nueva agencia (Constanza Zárate): fase inicial del contrato (Cláusula Cuarta) y carga de la estructura de tareas en ClickUp.
