# Backlog ClickUp — Intervenciones SEO y Landing Page

**Fecha:** 19-08-2026 · **Fuente:** [Alcance Técnico — SEO](alcance-tecnico-seo.md) y [Alcance Técnico — Landing Page y Meta Ads](../landing/alcance-tecnico-landing-meta-ads.md), segunda corrida. **Formato:** tareas listas para crear como cards en ClickUp, agrupadas por matriz de impacto/esfuerzo.

## Leyenda

**Responsable** — Agencia-prestador / Cliente-Estudio / conjunto (ambos), siguiendo la misma convención del Backlog ClickUp GA4 e Investigación 2.

**Total de tareas:** 24 — 22 Agencia-prestador, 2 conjuntas Cliente-Estudio + Agencia.

## Matriz de priorización (impacto × esfuerzo)

### Q1 — Alto impacto / esfuerzo bajo-medio (hacer primero)

- **SL1** — Consolidar Google Tag Manager en un único contenedor (hoy GTM-N7BQZZW + GTM-MQC692WV activos a la vez) (1-2 horas)
- **SL2** — Instalar Meta Pixel en la totalidad del sitio + evento Lead en el formulario (2-4 horas)
- **SL3** — Combinar y minificar las 51 hojas de estilo CSS de Elementor (3-5 horas)
- **SL4** — Reducir JavaScript no utilizado (~294 KiB estimados por Lighthouse) (3-5 horas)
- **SL5** — Optimizar el elemento LCP de la home (hoy 12.4s, meta <2.5s) (2-4 horas)
- **SL6** — Investigar el 57% de abandono de formulario (141 form_start vs 61 form_submit/30d) (1-2 horas análisis + ajustes)
- **SL23** — Publicar el set de anuncios del Anexo A (5 variantes) — condicional a SL2 (1 día)

### Q3 — Impacto medio (agenda regular)

- **SL7** — Investigar la tasa de rebote de 72% en tráfico Direct (vs 45% Paid Search) (1-2 horas)
- **SL8** — Diseñar y probar formulario corto (nombre + teléfono) para tráfico frío de Meta (1 día + 2 semanas de test)
- **SL9** — Variar el texto del CTA entre secciones de la landing (1-2 horas)
- **SL10** — Reforzar la propuesta de valor específica en el primer bloque visible (2-3 horas)
- **SL11** — Incorporar prueba social numérica (casos resueltos, años de operación) en la home (2-3 horas)
- **SL12** — Completar atributo alt en imágenes de contenido (hoy 42% de cobertura en la home) (3-4 horas)
- **SL14** — Implementar schema LocalBusiness (1-2 horas)
- **SL15** — Implementar schema Service en las 6 páginas de servicio (3-4 horas)
- **SL22** — Actualizar WordPress (6.8.8) y Elementor/Pro (4.1.4/4.1.2) a la versión estable más reciente (1 día (con staging y respaldo))
- **SL24** — Reporte quincenal de campañas (CTR, CPC, ROAS, costo por lead) (1-2 horas c/u)

### Q4 — Impacto bajo (rellenar huecos / quick wins sueltos)

- **SL13** — Ampliar cobertura de loading=lazy a imágenes fuera del primer scroll (hoy 41%) (1-2 horas)
- **SL16** — Ajustar imagen Open Graph a 1200×630 (hoy cuadrada 1080×1080) (30 min)
- **SL17** — Completar twitter:title, twitter:description y twitter:image (30 min)
- **SL18** — Ampliar meta description de la home a 150-160 caracteres (hoy 135) (15 min)
- **SL19** — Apuntar enlaces de menú a /servicios/ y /blog/ con barra final (evitar 301) (15 min)
- **SL20** — Agregar cabecera Strict-Transport-Security (30 min)
- **SL21** — Resolver respuesta 404 de /favicon.ico (15 min)

## Detalle completo (formato asset ClickUp)

| # | Tarea | Lista (carpeta) | Responsable | Impacto | Esfuerzo | Duración | Plataforma / Tag | Referencia |
|---|---|---|---|---|---|---|---|---|
| SL1 | Consolidar Google Tag Manager en un único contenedor (hoy GTM-N7BQZZW + GTM-MQC692WV activos a la vez) | Tracking | Agencia-prestador | Alto | Bajo | 1-2 horas | GTM | Alcance SEO P1 / Backlog GA4 |
| SL2 | Instalar Meta Pixel en la totalidad del sitio + evento Lead en el formulario | Tracking | Agencia-prestador | Alto | Medio | 2-4 horas | Meta Pixel | Alcance Landing P1 |
| SL3 | Combinar y minificar las 51 hojas de estilo CSS de Elementor | Rendimiento | Agencia-prestador | Alto | Medio | 3-5 horas | WP Rocket / Elementor | Alcance SEO P2 |
| SL4 | Reducir JavaScript no utilizado (~294 KiB estimados por Lighthouse) | Rendimiento | Agencia-prestador | Alto | Medio | 3-5 horas | Elementor / plugins | Nuevo — Lighthouse 19-08 |
| SL5 | Optimizar el elemento LCP de la home (hoy 12.4s, meta <2.5s) | Rendimiento | Agencia-prestador | Alto | Medio | 2-4 horas | Lighthouse | Nuevo — Lighthouse 19-08 |
| SL6 | Investigar el 57% de abandono de formulario (141 form_start vs 61 form_submit/30d) | CRO | Cliente-Estudio + Agencia | Alto | Medio | 1-2 horas análisis + ajustes | GA4 / UX | Alcance Landing P2 / Backlog GA4 G10 |
| SL7 | Investigar la tasa de rebote de 72% en tráfico Direct (vs 45% Paid Search) | CRO | Cliente-Estudio + Agencia | Medio | Medio | 1-2 horas | GA4 | Nuevo — datos reales GA4 |
| SL8 | Diseñar y probar formulario corto (nombre + teléfono) para tráfico frío de Meta | CRO | Agencia-prestador | Medio | Medio | 1 día + 2 semanas de test | Landing / Meta Ads | Alcance Landing P2 |
| SL9 | Variar el texto del CTA entre secciones de la landing | CRO | Agencia-prestador | Medio | Bajo | 1-2 horas | Landing | Alcance Landing P2 |
| SL10 | Reforzar la propuesta de valor específica en el primer bloque visible | CRO | Agencia-prestador | Medio | Bajo | 2-3 horas | Landing | Alcance Landing P2 |
| SL11 | Incorporar prueba social numérica (casos resueltos, años de operación) en la home | CRO | Agencia-prestador | Medio | Bajo | 2-3 horas | Landing | Alcance Landing P3 |
| SL12 | Completar atributo alt en imágenes de contenido (hoy 42% de cobertura en la home) | Accesibilidad | Agencia-prestador | Medio | Medio | 3-4 horas | WordPress | Alcance SEO P3 |
| SL13 | Ampliar cobertura de loading=lazy a imágenes fuera del primer scroll (hoy 41%) | Accesibilidad | Agencia-prestador | Bajo | Bajo | 1-2 horas | WordPress | Alcance SEO P3 |
| SL14 | Implementar schema LocalBusiness | Datos estructurados | Agencia-prestador | Medio | Bajo | 1-2 horas | Schema / Yoast | Alcance SEO P5 |
| SL15 | Implementar schema Service en las 6 páginas de servicio | Datos estructurados | Agencia-prestador | Medio | Medio | 3-4 horas | Schema / Yoast | Alcance SEO P5 |
| SL16 | Ajustar imagen Open Graph a 1200×630 (hoy cuadrada 1080×1080) | Datos estructurados | Agencia-prestador | Bajo | Bajo | 30 min | Yoast SEO | Alcance SEO P5 |
| SL17 | Completar twitter:title, twitter:description y twitter:image | Datos estructurados | Agencia-prestador | Bajo | Bajo | 30 min | Yoast SEO | Alcance SEO P5 |
| SL18 | Ampliar meta description de la home a 150-160 caracteres (hoy 135) | Datos estructurados | Agencia-prestador | Bajo | Bajo | 15 min | Yoast SEO | Alcance SEO P5 |
| SL19 | Apuntar enlaces de menú a /servicios/ y /blog/ con barra final (evitar 301) | Técnico | Agencia-prestador | Bajo | Muy bajo | 15 min | WordPress | Alcance SEO P6 |
| SL20 | Agregar cabecera Strict-Transport-Security | Técnico | Agencia-prestador | Bajo | Bajo | 30 min | Servidor / hosting | Alcance SEO P6 |
| SL21 | Resolver respuesta 404 de /favicon.ico | Técnico | Agencia-prestador | Bajo | Muy bajo | 15 min | WordPress | Alcance SEO P6 |
| SL22 | Actualizar WordPress (6.8.8) y Elementor/Pro (4.1.4/4.1.2) a la versión estable más reciente | Plataforma | Agencia-prestador | Medio | Alto | 1 día (con staging y respaldo) | WordPress / Elementor | Alcance SEO P4 |
| SL23 | Publicar el set de anuncios del Anexo A (5 variantes) — condicional a SL2 | Campañas | Agencia-prestador | Alto | Medio | 1 día | Meta Ads | Alcance Landing P4 |
| SL24 | Reporte quincenal de campañas (CTR, CPC, ROAS, costo por lead) | Campañas | Agencia-prestador | Medio | Bajo | 1-2 horas c/u | General | Alcance Landing P4 |

## Notas de cruce con otros backlogs

- SL1 y SL6 ya existen como tareas en el [Backlog ClickUp GA4](../campanas-ads/backlog-clickup-ga4.md) (G3/G9 y G10) — no crear cards duplicadas en ClickUp, enlazar la card existente.
- SL2 y SL23 dependen entre sí: no publicar el Anexo A de anuncios (SL23) sin haber resuelto el Meta Pixel (SL2), porque no habría forma de medir el resultado.

Fuente en CSV para el importador de ClickUp: [`Backlog-ClickUp-SEO-Landing-Import.csv`](../descargables/Backlog-ClickUp-SEO-Landing-Import.csv). Versión Word: [`Backlog-ClickUp-SEO-Landing.docx`](../descargables/Backlog-ClickUp-SEO-Landing.docx).
