# Alcance Técnico — SEO

**Sitio:** www.defensordelcontribuyente.cl (redirige correctamente a defensordelcontribuyente.cl)
**Fecha:** 19 de agosto de 2026 (segunda corrida — línea base: 17 de agosto de 2026)
**Preparado para:** equipo de marketing entrante

## Resumen del alcance

Este documento detalla las modificaciones técnicas de SEO que deben ejecutarse sobre defensordelcontribuyente.cl, ordenadas por prioridad. Esta segunda corrida repite la auditoría íntegra usando la metodología profesional de 8 categorías ponderadas (meta tags, headings, imágenes, enlaces, Open Graph/social, datos estructurados, técnico y contenido) y confirma, hallazgo por hallazgo, qué sigue pendiente desde la línea base del 17-08-2026.

## Puntuación profesional: 69/100

Nota metodológica: Lighthouse le da a esta misma página SEO 100/100 porque solo mide crawlability técnica básica (indexabilidad, meta viewport, enlaces rastreables). La puntuación de abajo es más amplia — incorpora imágenes, redes sociales, datos estructurados y deuda técnica real, que es donde está la mayoría de las oportunidades.

| Categoría | Peso | Puntaje | Motivo |
|---|---|---|---|
| Meta Tags | 20% | 88/100 | Title (55 car.) y meta description (135 car., bajo el rango 150-160) presentes y persuasivos. Canonical, robots meta, viewport y lang correctos. |
| Headings | 15% | 95/100 | Exactamente 1 H1 ("Abogado tributario") en la home, sin salto de jerarquía detectado. |
| Imágenes | 10% | 40/100 | 66 imágenes en la home, solo 28 con alt (42%) y 27 con lazy loading (41%). |
| Enlaces | 10% | 85/100 | 0 enlaces rotos en la muestra de 20 URL de navegación verificadas. 2 enlaces de menú (/servicios, /blog) sin barra final generan un salto 301 evitable. |
| Open Graph y Social | 10% | 55/100 | Open Graph completo pero con imagen cuadrada (1080×1080, debería ser 1200×630). Twitter Card solo declara el tipo, sin title/description/image propios. |
| Schema / Datos Estructurados | 10% | 65/100 | Organization, WebSite, WebPage, BreadcrumbList e ImageObject bien formados. Falta LocalBusiness y schema Service en las páginas de servicio. |
| Técnico | 15% | 45/100 | HTTPS, robots.txt, sitemap (vía sitemap_index.xml) y redirección www correctos, con servidor rápido (145ms TTFB). Pesan en contra: 51 hojas de estilo CSS, LCP de 12.4s, sin header HSTS, favicon en 404 y GTM duplicado. |
| Contenido | 10% | 60/100 | 801 palabras visibles en la home (sobre el mínimo de 300), pero ratio texto/HTML muy bajo (~2%) por el peso de CSS/JS de Elementor. |

## Qué sigue vigente desde la línea base del 17-08-2026

| Hallazgo | Estado | Verificación de hoy |
|---|---|---|
| GTM duplicado (GTM-N7BQZZW + GTM-MQC692WV) | Persiste | Confirmado en el HTML de hoy. |
| 51 hojas de estilo CSS en la home | Persiste (empeoró levemente: 50 → 51) | Confirmado por conteo directo de <link rel=stylesheet>. |
| 58% de imágenes sin alt | Persiste | 42% con alt hoy (28 de 66), igual que en la auditoría base. |
| Imagen Open Graph cuadrada | Persiste | 1080×1080 confirmado en el meta og:image:width/height. |
| Twitter Cards incompletas | Persiste | Solo twitter:card presente. |
| Header Strict-Transport-Security ausente | Persiste | No aparece en los headers de respuesta. |
| Favicon.ico en 404 | Persiste | HTTP 404 confirmado. |
| Enlaces de menú sin barra final (/servicios, /blog) | Persiste | Confirmado: ambos responden 301 hacia la versión con barra. |
| WordPress 6.8.8 / Elementor 4.1.4 / Pro 4.1.2 desactualizados | Persiste | Mismas versiones detectadas en el query string de los assets. |
| Schema LocalBusiness y Service ausentes | Persiste | No aparecen en el JSON-LD de la home. |

## Hallazgos nuevos de esta corrida

- **LCP (Largest Contentful Paint) de 12.4 segundos** en la home — muy por sobre el umbral de "bueno" (2.5s). Es la métrica más crítica de Core Web Vitals y afecta tanto el ranking como la experiencia real de usuarios que llegan desde campañas pagadas.
- **Total Blocking Time de 730ms** — la página queda "congelada" para el usuario ese tiempo mientras carga JavaScript.
- **294 KiB de JavaScript sin usar** cargado en cada visita (hallazgo Lighthouse, ahorro estimado ~1.76s si se elimina).
- **Ratio texto/HTML de ~2%**, muy por debajo del 25% recomendado — confirma que el peso de CSS/JS de Elementor está desproporcionado respecto al contenido real de la página.
- **Meta description de 135 caracteres** — funcional y persuasiva, pero bajo el rango óptimo de 150-160; se puede ampliar sin reescribirla del todo.
- El **sitemap no está en `/sitemap.xml`** (esa ruta da 404) sino en `/sitemap_index.xml`, correctamente declarado en `robots.txt` — esto es la convención estándar de Yoast SEO, **no es un error**, se aclara para que no se reporte como bug en el traspaso.

## Prioridad 1 — Medición y tracking (crítico)

Sin cambios respecto a la línea base — sigue sin resolverse:

- Consolidar la implementación de Google Tag Manager en un único contenedor.
- Migrar el tag de conversión de Google Ads (ID de conversión AW-593050363) dentro del contenedor consolidado.
- Verificar en el Asistente de Etiquetas de Google que no se disparen eventos duplicados en ninguna página.
- Documentar el contenedor GTM vigente y entregar acceso de administrador al equipo interno.

## Prioridad 2 — Rendimiento

- Combinar y minificar las hojas de estilo CSS de Elementor (51 archivos separados hoy en la home, subió respecto a los 50 de la línea base).
- Revisar y activar la opción de combinación de CSS en WP Rocket, o ajustar el "print method" de Elementor.
- **Nuevo:** reducir JavaScript no utilizado (~294 KiB) — revisar qué scripts de plugins/Elementor se cargan sin necesitarse en cada página.
- **Nuevo:** atacar directamente el LCP de 12.4s — probablemente la imagen o bloque above-the-fold más pesado del hero.
- Validar el resultado con PageSpeed Insights / Core Web Vitals después de cada cambio.

## Prioridad 3 — Accesibilidad e imágenes

- Completar el atributo `alt` en todas las imágenes de contenido (hoy 42% de cobertura en la home, 28 de 66).
- Ampliar la cobertura de `loading="lazy"` a las imágenes fuera del primer scroll (hoy 41% de cobertura).

## Prioridad 4 — Actualización de plataforma

- Actualizar WordPress (hoy 6.8.8) a la versión estable más reciente — el subdominio servicios. ya corre WordPress 7.0.4, confirmando que es viable.
- Actualizar Elementor (hoy 4.1.4) y Elementor Pro (hoy 4.1.2) a la versión más reciente.
- Confirmar compatibilidad de plugins activos antes de cada actualización, con respaldo y staging previos.

## Prioridad 5 — Datos estructurados y metadatos

- Implementar schema `LocalBusiness` para el negocio.
- Implementar schema `Service` en cada una de las 6 páginas de servicio.
- Ajustar la imagen Open Graph a proporción 1.91:1 (1200×630) — hoy es cuadrada (1080×1080).
- Completar las etiquetas `twitter:title`, `twitter:description` y `twitter:image` — hoy solo existe `twitter:card`.
- Ampliar la meta description a 150–160 caracteres (hoy 135).

## Prioridad 6 — Otros ajustes

- Apuntar los enlaces del menú directamente a `/servicios/` y `/blog/` (con barra final) — confirmado que hoy generan un salto 301.
- Agregar la cabecera `Strict-Transport-Security` — confirmado ausente.
- Resolver la respuesta 404 de `/favicon.ico` — confirmado vigente.

## Criterios de aceptación

| Punto | Cómo se valida |
|---|---|
| Tracking consolidado | Un solo contenedor GTM visible en el código fuente; sin eventos duplicados en el Asistente de Etiquetas |
| CSS combinado | Menos de 10 peticiones de hojas de estilo en la home |
| LCP bajo control | Menos de 2.5s en PageSpeed Insights / Lighthouse |
| Imágenes con alt | 100% de imágenes de contenido con alt descriptivo |
| Plataforma actualizada | Versión de WordPress y Elementor al día, confirmable en el panel de administración |
| Schema implementado | Validación sin errores en el Rich Results Test de Google |

## Metodología

- Auditoría de meta tags, headings, imágenes, enlaces, Open Graph/social, schema, técnico y contenido ejecutada sobre el HTML real de la home (descarga directa, sin autenticación).
- Verificación técnica de robots.txt, sitemap, favicon, redirecciones www/no-www y http/https vía curl.
- Verificación de 20 enlaces internos de navegación por código de estado HTTP.
- Core Web Vitals y oportunidades de rendimiento vía Lighthouse (Google Chrome), modo headless.
- La puntuación de 8 categorías sigue la metodología de la skill de auditoría SEO del usuario, complementada con los hallazgos ya confirmados de auditorías previas del sitio.
