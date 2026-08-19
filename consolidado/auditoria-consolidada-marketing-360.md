# Auditoría Consolidada de Marketing 360° — Defensor del Contribuyente

## 1. Portada

- **Empresa/cliente:** Estudio Jurídico Boutique — Defensor del Contribuyente (DDCON), Concepción.
- **Fecha de emisión:** 19 de agosto de 2026.
- **Carpetas analizadas:** `Downloads/Auditoria Total MKT/Auditoria Total Cliente` (14 documentos PDF), `Downloads/Auditoria Total MKT/Informe 360 agencia`, repositorio `auditorias-internas` (fuente versionada de las mismas auditorías Claude Code, en Markdown).
- **Periodos comprendidos:** documentos técnicos Claude Code: 28-05-2026 y 17/19-08-2026. Informe 360 agencia: histórico jun-2023–jul-2026, con foco en abr–jul 2026 (Google Ads) y "últimos 30 días" para tráfico orgánico reciente. Emitido agosto 2026.
- **Documentos procesados:** 16 (ver inventario, sección 4).
- **Documentos no procesados:** 0 archivos ilegibles. 2 documentos (`Guiones-y-Configuracion-7-Temas`, `Estructura-Tareas-ClickUp`) se registraron en el inventario y se usaron como contexto pero no se extrajeron línea por línea al detalle de cifras — son activos operativos (guiones de anuncios, desglose contractual), no auditorías con hallazgos a contrastar; ver limitaciones en Anexos.
- **Versión del reporte:** v1.1 (ver nota 1.2 — agrega auditoría técnica WordPress y backlog maestro, sin alterar la comparación central con el Informe 360 de la agencia).

## 1.2 Nota de actualización (19-08-2026 — segunda sesión, auditoría WordPress)

Se ejecutó una segunda auditoría, esta vez documental (WXR + inventario de plugins/Wordfence) y en vivo (escaneo de la home, las 10 páginas de servicio y los 7 posts de blog en canibalización), fuera del alcance original de este reporte. **Esta nota es aditiva — no modifica ninguna sección del análisis original (2-13), incluida la comparación contra el Diagnóstico 360 de la agencia.** Se agregó:

- **Sección 4 (inventario documental):** DOC-17 a DOC-23.
- **Sección 6.15 (nueva):** WordPress técnico, con los hallazgos de la auditoría profunda.
- **Backlog maestro:** [`consolidado/backlog-maestro-clickup.csv`](backlog-maestro-clickup.csv) — 93 tareas, fusiona sin duplicar los 6 backlogs ya existentes en el repositorio (consolidado de 32, SEO/Landing de 24, GA4 de 11, Investigación 2 de 17+4 activos, Plan post-CAE de 11, Gobernanza Google Ads de 3) más las 14 tareas WordPress y 13 hallazgos nuevos del escaneo en vivo. Es el backlog operativo recomendado a partir de ahora — los backlogs individuales (SL, G, T, CAE, WP) siguen vigentes como fuente por área, pero para trabajo de ClickUp use el maestro.
- **Hallazgo de mayor relevancia agregado por esta sesión:** el sitio corre un **tercer sistema de tracking no documentado** (Google tag `GT-NCHTQWQT` vía Site Kit by Google, exclusivo del subdominio `servicios.`) y **RUT obligatorio como estándar en casi todos los formularios de captación** — esto último contradice directamente el checklist de mejores prácticas ya escrito en DOC-11 (formulario simplificado 2-3 campos para tráfico frío). Ninguno de los dos hallazgos estaba documentado antes de esta sesión.
- El escaneo en vivo también **confirma con evidencia técnica más fuerte** la contradicción ya anotada en la sección 9 original (Meta Pixel activo según Ads Manager vs. ausente en el HTML): 0 rastros de `fbq()`/pixel en 11 páginas escaneadas hoy (home + 10 URL de servicio), con el único indicio nuevo siendo una meta tag `facebook-domain-verification` en `servicios.` — no se altera el veredicto ya registrado en la sección 9, se refuerza con más evidencia (ver TASK-066 del backlog maestro).

## 1.1 Nota de actualización (19-08-2026)

Mientras se compilaba este reporte, aterrizaron en este mismo repositorio una segunda corrida de las auditorías SEO, Landing y GA4, más las versiones ya versionadas en Markdown de DOC-12 (gobernanza/Google Ads, antes solo disponible en PDF) y DOC-13 (backlog SEO/Landing, ídem). Se revisó el diff completo contra lo ya analizado: **ningún hallazgo citado en este reporte quedó invalidado** — la segunda corrida de SEO/Landing confirma explícitamente, hallazgo por hallazgo, que todo lo citado en la sección 9 (GTM duplicado, imagen OG cuadrada, Twitter Cards incompletas, favicon 404, HSTS ausente) sigue vigente, y agrega una puntuación profesional de 69/100 en 8 categorías ponderadas (antes no existía ese framework). La segunda corrida de GA4 confirma sin cambios los hallazgos críticos ya citados y agrega un cruce nuevo: de las 14 URL de campaña, 13 tienen propiedad GA4 y sumaron 41 conversiones en 30 días concentradas en solo 2 páginas — dato complementario, no se incorporó al cuerpo del reporte por llegar después del cierre de redacción; consultar directamente `campanas-ads/auditoria-ga4-completa.md` para el detalle URL por URL. El contenido de DOC-12 y DOC-13 en su versión Markdown es consistente con lo extraído de los PDF originales usados en este análisis — sin diferencias materiales.

## 2. Resumen ejecutivo

Las auditorías Claude Code y el Informe 360 de la agencia **no compiten por el mismo terreno — se complementan casi sin superponerse**, y donde sí se superponen, se confirman mutuamente. Claude Code auditó profundidad técnica de plataforma (código fuente, GTM, Pixel, GA4 evento por evento, Lighthouse por URL, políticas de Meta 2026) con datos en vivo vía MCP de Meta y GA4. La agencia auditó el embudo de negocio completo (Pipedrive/CRM, tasa de cierre real, Google Ads a nivel de keyword y término de búsqueda, panorama competitivo) con acceso a sistemas que Claude Code no tenía — de hecho, la propia auditoría Claude Code (DOC-12) señala como bloqueante P0 la falta de upgrade del developer token de Google Ads, lo que explica por qué el lado Claude Code nunca llegó a auditar campañas de Google Ads en profundidad.

**Coincidencias fuertes (validación cruzada, dos fuentes independientes, mismo hallazgo):** el Pixel de Meta solo mide `PageView` y no tiene evento de Lead/Contacto (DOC-03 y DOC-16, cifras de gasto y resultados casi idénticas); la medición está fragmentada en propiedades/dominios sin relación entre sí (GA4 dividido en 2 propiedades sin rollup — DOC-04 — coincide con "Analytics dividido en dos propiedades" de DOC-16); la Conversions API de Meta está incompleta (DOC-08 y DOC-16).

**Omisión más relevante de la agencia:** el hallazgo técnico más grave y accionable de todo el corpus — que el pixel `524558258682248` está activo y funcionando pero **solo** mide `PageView`, con el detalle de que la única campaña activa optimiza por `onsite_conversion.messaging_deep_conversation` — el Informe 360 lo describe en términos generales pero sin la profundidad técnica ni la solución específica (CTWA + CAPI vía `ctwa_clid`) que sí aporta DOC-08.

**Omisión más relevante de Claude Code:** el hallazgo central del Informe 360 — que la tasa de cierre real de lead a cliente es 2,3% (135 de 5.950 tratos) y es pareja entre todos los canales — no tiene ningún equivalente en el corpus Claude Code, porque ninguna auditoría Claude Code tuvo acceso a Pipedrive. Es la brecha más importante de todo el diagnóstico técnico: sin este dato, arreglar tracking y campañas (foco casi total de las auditorías Claude Code) deja sin resolver la mayor parte del problema real de crecimiento, tal como advierte el propio Informe 360.

**Contradicción real detectada (cifras):** el gasto y resultados de la campaña "Diagnósticos Gratuitos" no coinciden exactamente entre ambas fuentes ($5.338.077 / 4.858 resultados / $1.099 por resultado en DOC-03, vs. $5.070.552 / 4.655 resultados / $1.089 en DOC-16) — ver sección 10, clasificada como diferencia temporal de captura, no como error, porque el resto de las 5 campañas CAE coinciden en cifra exacta entre ambas fuentes.

**Calidad del Informe 360:** sólido y honesto — incluye correcciones explícitas hechas en conversación con el cliente ("ajuste de estrategia" en 3 puntos), reconoce con transparencia cuando un dato de Pipedrive no es confiable, y prioriza según lo que el propio cliente definió, no según un framework genérico. Su debilidad es de profundidad técnica de plataforma (no llega al nivel de evento GA4, código fuente o Lighthouse).

**Calidad de las auditorías Claude Code:** exhaustivas a nivel técnico y con datos en vivo verificables, con buena disciplina de trazabilidad (ajustes documentados con fecha, ej. el descuento del alcance CAE). Su límite es de negocio: sin Pipedrive ni Google Ads a nivel cuenta, no pueden pronunciarse sobre si arreglar la medición efectivamente va a mover el resultado comercial.

**Prioridades inmediatas (consolidadas, ver sección 11):** (1) cerrar el circuito de medición de Meta (Pixel + CAPI + CTWA) — coincidencia total entre ambas fuentes; (2) resolver el acceso bloqueado a Google Ads (developer token) para poder auditar y corregir el objetivo de conversión roto que reporta la agencia; (3) ordenar Pipedrive hacia adelante (no hacia atrás, según el propio cliente) para poder medir tasa de cierre real por canal.

**Recomendación general 2026:** no iniciar producción de contenido ni campañas nuevas de gran escala hasta cerrar el circuito de medición extremo a extremo (Pixel/CAPI de Meta + objetivo de conversión de Google Ads + Pipedrive) — ambas fuentes, por caminos distintos, llegan a la misma conclusión: hoy nadie puede saber con certeza qué campaña o pieza de contenido realmente genera un cliente.

## 3. Metodología

- **Fuentes analizadas:** 9 auditorías/documentos Claude Code en Markdown (repositorio `auditorias-internas`), 5 documentos Claude Code solo disponibles en PDF (extraídos a texto para este análisis), 1 Informe 360 de la agencia (PDF, extraído a texto), 1 exportación de herramienta externa (SEO Public, palabras clave).
- **Criterios de comparación:** las 25 dimensiones y las 10 explicaciones razonables de `references/metodologia-comparacion.md` de la skill `auditoria-consolidada-marketing-360`.
- **Tratamiento de diferencias temporales:** cuando dos fuentes reportan la misma campaña/métrica con cifras cercanas pero no idénticas, y una fuente documenta una fecha de captura posterior a la otra, se clasifica como diferencia temporal si la dirección del cambio es consistente con el tiempo transcurrido (más gasto/resultados en la captura más reciente).
- **Tratamiento de cifras:** toda cifra específica se contrastó contra su fuente original citada en el propio documento; cuando dos documentos reportan la misma cifra de forma idéntica se trató como corroboración cruzada fuerte.
- **Escala de importancia:** alta/media/baja según `references/criterios-priorizacion.md` de la misma skill.
- **Limitaciones generales:** este análisis no tuvo acceso directo a las plataformas (Meta Ads Manager, Google Ads, GA4, Pipedrive, Search Console) — se trabajó exclusivamente sobre lo que los 16 documentos reportan. Ningún hallazgo de este reporte fue re-verificado en vivo contra la plataforma.

## 4. Inventario documental

| ID | Documento | Ruta | Origen | Área | Fecha | Periodo analizado | Tipo | Estado | Observaciones |
|---|---|---|---|---|---|---|---|---|---|
| DOC-01 | Alcance Técnico — SEO | `seo/alcance-tecnico-seo.md` | Claude Code | SEO técnico | 17-08-2026 | Estado del sitio a esa fecha | Alcance/plan de tareas | Vigente | También en PDF/DOCX idéntico en `descargables/` y en Downloads |
| DOC-02 | Alcance Técnico — Landing/Meta Ads | `landing/alcance-tecnico-landing-meta-ads.md` | Claude Code | Landing / Meta Ads | 17-08-2026 | Estado del sitio a esa fecha | Alcance/plan de tareas | Vigente | Incluye 5 anuncios listos para publicar (Anexo A) |
| DOC-03 | Auditoría de cuenta Meta Ads | `campanas-ads/auditoria-cuenta-meta-ads.md` | Claude Code | Meta Ads | 17-08-2026, ajustado 18-08-2026 | Histórico completo de la cuenta hasta 17/18-08-2026 | Auditoría (datos reales vía MCP) | Vigente, con nota de ajuste | Puntuación 43/100. Fuente: Meta Ads MCP directo, no Biblioteca de Anuncios |
| DOC-04 | Auditoría Completa GA4 | `campanas-ads/auditoria-ga4-completa.md` | Claude Code | GA4 | 18-08-2026 | Últimos 30 días desde la fecha del informe | Auditoría (datos reales vía MCP) | Vigente | 2 propiedades GA4 auditadas evento por evento |
| DOC-05 | Backlog ClickUp — GA4 | `campanas-ads/backlog-clickup-ga4.md` | Claude Code | GA4 | 18-08-2026 | — | Backlog | Vigente | 10 tareas (G1-G10) |
| DOC-06 | Plan de ajustes post-CAE | `campanas-ads/plan-ajustes-post-cae-clickup.md` | Claude Code | Meta Ads | 18-08-2026 | — | Backlog / registro de cambios | Vigente | Ajusta DOC-03; 11 tareas |
| DOC-07 | Backlog ClickUp — Investigación 2 | `campanas-ads/backlog-clickup-investigacion-2.md` | Claude Code | Meta Ads / políticas | 18-08-2026 | — | Backlog | Vigente | 17 tareas + 4 activos de referencia |
| DOC-08 | Investigación 2 — Políticas y algoritmo Meta 2026 | `campanas-ads/investigacion-2-politicas-algoritmo-meta.md` | Claude Code | Meta Ads / políticas | 18-08-2026 | Estado de plataforma a esa fecha, con fuentes externas oficiales citadas | Investigación con datos en vivo + fuentes externas | Vigente | Reconcilia expresamente Opportunity Score 96/100 vs. puntaje 43/100 de DOC-03 |
| DOC-09 | Auditoría técnica 14 URL | `campanas-ads/auditoria-14-urls.md` | Claude Code | SEO técnico / Landing | 17-08-2026, complemento Lighthouse 18-08-2026 | Estado de 14 URL a esa fecha | Auditoría técnica + Lighthouse | Vigente | Promedios: rendimiento 75, accesibilidad 87, buenas prácticas 84, SEO 95, visibilidad IA 42 (sobre 100) |
| DOC-10 | Estructura de tareas ClickUp — Paid Media & Growth | `clickup/estructura-tareas-clickup.md` | Claude Code | Gobernanza / contrato | 17-08-2026 | Vigencia del contrato con la Prestadora | Desglose contractual | Vigente | 108 tareas identificadas desde el contrato, no desde una auditoría de hallazgos |
| DOC-11 | Guía 360° de Marketing Digital para Pymes | `estrategia-360/guia-marketing-digital-360-pyme.md` | Claude Code | Estrategia 2026 | 18-08-2026 | Estado del arte 2025-2026 | Guía / benchmark externo | Vigente | Metodología cruzada de 3 skills internas + BigSEO/Yoast/Metrix Digital |
| DOC-12 | Complemento — Acceso a Google Ads y Gobernanza de Cuentas | PDF original en `Downloads/...`; versionado en el repo el 19-08-2026 en `google-ads-gobernanza/complemento-google-ads-gobernanza.md` | Claude Code | Gobernanza / Google Ads | 18-08-2026 | — | Investigación + backlog (3 tareas) | Vigente | Confirma que el acceso a Google Ads (developer token, solo aprobado para cuentas de prueba) está bloqueado — explica por qué no hay auditoría Claude Code de campañas Google Ads. La versión Markdown del repo agrega el mapa de gobernanza de las 4 plataformas, sin diferencias materiales frente al PDF |
| DOC-13 | Backlog ClickUp — Intervenciones SEO y Landing Page | PDF original en `Downloads/...`; versionado en el repo el 19-08-2026 en `seo/backlog-clickup-seo-landing.md` | Claude Code | SEO / Landing | 19-08-2026 | — | Backlog (24 tareas, SL1-SL24) | Vigente | Consolida DOC-01 + DOC-02 en tareas priorizadas por impacto×esfuerzo; señala explícitamente que SL1 y SL6 ya existen en DOC-05 (evita duplicado). Contenido idéntico entre PDF y versión Markdown del repo |
| DOC-14 | Auditoría SEO — defensordelcontribuyente.cl (versión anterior) | PDF (`Downloads/.../3. Auditoria-seo-defensordelcontribuyente.pdf`) | Claude Code (herramienta anterior: "Claude Code + Beoutique") | SEO técnico | **28-05-2026** | Homepage principalmente | Auditoría con puntuación (70/100) | **Superseded parcialmente por DOC-01/DOC-09** | Foco distinto: homepage y meta tags sociales, no todo el sitio. Persisten sin resolver a agosto: schema LocalBusiness, imagen OG cuadrada, favicon 404 |
| DOC-15 | Palabras clave verificadas — SEO Public | PDF (`Downloads/.../1. Palabras clave verificadas SEO Public.pdf`) | Herramienta externa (SEO Public) | SEO de contenidos | Snapshot "hace 21 minutos" al momento de exportar (~agosto 2026) | Estado del sitemap indexado | Exportación de herramienta | Vigente | 11 cubiertas, 40 cobertura parcial, 8 sin cobertura |
| DOC-16 | Diagnóstico Estratégico de Marketing 360 (DDCON) | PDF (`Downloads/.../Informe 360 agencia.pdf`) | Agencia (Constanza Zárate, Paid Media & Growth Partner) | Estrategia 360 / CRM / Google Ads / Meta Ads / SEO / competencia | Agosto 2026 | jun-2023–jul-2026 (histórico), abr–jul 2026 (Google Ads), últimos 30 días / 3 meses / 12 meses (SEO) | Diagnóstico integral | Vigente | Incluye correcciones en vivo acordadas con el cliente ("ajuste de estrategia", 3 casos) |
| DOC-17 | Exportación WXR del sitio (contenido completo) | Proporcionado por el cliente, no versionado (binario 9,5 MB) | Cliente (export nativo WordPress) | WordPress / contenido | 19-08-2026 | Estado del contenido a esa fecha | Exportación de plataforma | Vigente | 25 posts de blog, 20 CPT de servicio/equipo/casos de éxito |
| DOC-18 | Transcripción — Plugins y seguridad WordPress | Proporcionado por el cliente, no versionado (fuente intermedia, consolidada en DOC-19) | Cliente (transcripción IA + verificación humana) | WordPress / seguridad | 19-08-2026 | Estado del panel a esa fecha | Transcripción de panel de administración | Vigente | 21 plugins, panel de Wordfence |
| DOC-19 | Auditoría Técnica — WordPress (Plugins, Seguridad y Contenido) | `wordpress/auditoria-tecnica-wordpress-plugins-seguridad.md` | Claude Code | WordPress técnico | 19-08-2026 | Estado del panel/contenido a esa fecha | Auditoría documental | Vigente | v1 — sin conexión al panel, sin escaneo del dominio |
| DOC-20 | Auditoría Técnica WordPress — Versión Detallada (Escaneo en Vivo) | `wordpress/auditoria-tecnica-wordpress-detallada.md` | Claude Code | WordPress técnico | 19-08-2026 | Estado en vivo a esa fecha | Auditoría técnica (HTML en vivo) | Vigente | v2 — profundiza DOC-19 con escaneo de home + 10 páginas de servicio + 7 posts de blog |
| DOC-21 | Correlación — Auditoría Técnica WordPress × Auditorías de Marketing 360° | `consolidado/correlacion-wordpress-marketing-360.md` | Claude Code | WordPress técnico / correlación | 19-08-2026 | — | Correlación entre auditorías | Vigente | Sesión previa a DOC-20; cruza DOC-19 contra DOC-01/DOC-02 |
| DOC-22 | Backlog ClickUp — Auditoría Técnica WordPress | `consolidado/backlog-clickup-wordpress.csv` | Claude Code | WordPress técnico | 19-08-2026 | — | Backlog (14 tareas, WP-01 a WP-14) | Vigente | Validado con `validar_backlog.py` |
| DOC-23 | Backlog ClickUp Maestro | `consolidado/backlog-maestro-clickup.csv` | Claude Code | Todas las áreas | 19-08-2026 | — | Backlog fusionado (93 tareas) | Vigente | Fusiona sin duplicar TASK-001..032, SL1-24, G1-11, T1-17+A1-4, CAE-plan (11), Gobernanza Google Ads (3) y WP-01..14, más 13 hallazgos nuevos del escaneo en vivo |

**No procesados al detalle de cifras (contexto, no auditoría):** `campanas-ads/guiones-y-configuracion-7-temas.md` (guiones de anuncios, activo creativo) y el desglose completo de las 108 tareas de `clickup/estructura-tareas-clickup.md` (DOC-10) — se usaron para contexto de gobernanza/responsables, no se extrajeron fila por fila porque no son hallazgos de auditoría sino un desglose contractual y un banco de creatividades.

## 5. Matriz ejecutiva de cobertura

| Tema | Auditorías Claude Code | Informe 360 agencia | Coincidencia | Diferencia | Evaluación | Importancia | Fuente |
|---|---|---|---|---|---|---|---|
| Meta Pixel sin evento de conversión | Cubre en detalle técnico (ID de pixel, evento exacto) | Cubre a nivel de negocio (fecha de instalación, volumen de eventos) | Coincidencia total | Claude Code más técnico; agencia da contexto histórico (activo desde 2021) | Confirmado por ambas fuentes de forma independiente | Alta | DOC-03, DOC-16 |
| Meta CAPI incompleta | Cubre con solución técnica específica (CTWA + `ctwa_clid`) | Cubre con dato adicional: "se empezó a configurar en abril 2026, nunca se completó" | Coincidencia total, complementaria | Agencia aporta un dato (intento parcial) que Claude Code no reporta | Hallazgo complementario | Alta | DOC-08, DOC-16 |
| GA4 fragmentado en propiedades sin relación | Cubre en profundidad evento por evento, 2 propiedades | Cubre a nivel de síntoma ("Analytics dividido en dos propiedades") | Coincidencia total | Profundidad muy distinta | Claude Code aporta el detalle accionable | Alta | DOC-04, DOC-16 |
| GTM duplicado en el dominio principal | Cubre con IDs exactos de contenedor, confirmado en 8/14 URL | No lo menciona con ese nivel de detalle | Hallazgo exclusivo de Claude Code (más profundo) | La agencia describe la fragmentación de dominios, no la duplicidad interna de GTM | Hallazgo exclusivo de Claude Code | Alta | DOC-01, DOC-03, DOC-09 |
| Google Ads: objetivo de conversión roto, autocanibalización de keywords, términos de búsqueda sin conversión | No cubierto — acceso bloqueado (ver DOC-12) | Cubierto en profundidad, con cifras exactas | Hallazgo exclusivo de la agencia | Explicado por una limitación de acceso documentada del lado Claude Code, no por omisión | Requiere validación en plataforma una vez resuelto el acceso | Alta | DOC-12, DOC-16 |
| Pipedrive / tasa de cierre real | No cubierto — sin acceso a CRM | Cubierto en profundidad (5.950 tratos, 2,3% cierre) | Hallazgo exclusivo de la agencia | Brecha estructural del lado Claude Code | El hallazgo más importante del corpus completo | Alta | DOC-16 |
| Indexación total del sitio (45%) | No cubierto a nivel de sitio completo (solo 2/14 URL con noindex) | Cubierto con dato de Search Console (56/123 páginas) | Hallazgo exclusivo de la agencia | Claude Code no tuvo acceso a Search Console a nivel de propiedad completa | Confirma y cuantifica lo que DOC-09 solo insinuaba | Alta | DOC-09, DOC-16 |
| Fragmentación de WordPress (3 instalaciones, 3 versiones) | Cubierto en detalle técnico | Cubierto solo como "6 dominios/subdominios sin gobernanza" | Coincidencia parcial | Ángulos distintos del mismo problema | Ambos apuntan a la misma causa raíz | Alta | DOC-09, DOC-16 |
| Rendimiento de carga / Core Web Vitals móvil | Cubierto por URL vía Lighthouse (promedio 75/100) | Cubierto vía Search Console (100% de URL móviles "necesita mejora") | Coincidencia total | Metodologías distintas (Lighthouse en frío vs. datos de campo de Search Console) — resultado consistente: ambas marcan rendimiento móvil como problema | Confirmado por dos metodologías independientes | Alta | DOC-09, DOC-16 |
| Fatiga del anuncio "Video 22" / ciclo de fatiga creativa 2026 | Cubierto en profundidad, con CTR exacto (-40,72%) y fuente oficial de Meta | No mencionado (agencia no auditó creativos a ese nivel) | Hallazgo exclusivo de Claude Code | — | Sin contraparte en el Informe 360 | Alta | DOC-03, DOC-08 |
| Palabras clave / keyword research | Cubierto vía herramienta SEO Public (cobertura de contenido existente) | Cubierto vía Google Ads + Search Console (volumen y conversión reales) | Hallazgo complementario | Ángulos distintos: SEO Public mide cobertura de contenido; agencia mide volumen/costo/conversión real | Se complementan, no se contradicen | Media-Alta | DOC-15, DOC-16 |
| Panorama competitivo | No cubierto | Cubierto en profundidad (8 competidores directos + marketplaces + jugadores de deuda personal) | Hallazgo exclusivo de la agencia | — | Sin contraparte Claude Code | Media | DOC-16 |
| Políticas Meta 2026 / IA generativa / divulgación | Cubierto en profundidad con fuentes oficiales citadas | No cubierto | Hallazgo exclusivo de Claude Code | — | Sin contraparte en el Informe 360 | Media | DOC-08 |
| Contexto normativo tributario 2026 (Ley 21.713, condonaciones) | No cubierto (fuera del alcance de marketing técnico) | Cubierto como motor de demanda de contenido | Hallazgo exclusivo de la agencia | Fuera de alcance declarado de las auditorías Claude Code | Complementario, no contradictorio | Media | DOC-16 |

## 6. Análisis consolidado por área

### 6.1 Meta Ads

**Hallazgos consolidados:** cuenta con salud de entrega correcta (15/15 en DOC-03) pero estructura y frescura creativa muy débiles (5/20 y 4/20). Un solo anuncio activo desde abril de 2025 concentra el 71% del gasto de su campaña y Meta lo diagnostica textualmente como "This ad is not spurring interest" (DOC-03), con una caída de CTR confirmada del 40,72% (DOC-08, consulta en vivo). El banco de 70 creativos producidos permanece prácticamente sin usar. Las 3 campañas CAE, más eficientes en costo por resultado ($373-$649 vs. $1.089-$1.099 de la campaña activa), quedaron pausadas por desactualización de oferta, no por bajo rendimiento — ajuste documentado el 18-08-2026 en DOC-06.

**Coincidencias:** el Pixel solo mide `PageView` (DOC-03, DOC-16); el gasto histórico y resultados de las campañas CAE coinciden en cifra exacta entre ambas fuentes (ver sección 10); ambas fuentes reconocen que la cuenta no tiene señal de conversión real.

**Omisiones:** el Informe 360 no llega al detalle de fatiga creativa por anuncio ni a las políticas de divulgación de IA 2026; las auditorías Claude Code no cubren la atribución de Meta dentro del CRM (DOC-16: "de 6.329 contactos históricos, ninguno tiene a Meta o Instagram como fuente de origen" — un hallazgo de alto impacto que ninguna auditoría Claude Code puede replicar sin acceso a Pipedrive).

**Contradicciones:** ninguna confirmada. Diferencia temporal en cifras de "Diagnósticos Gratuitos" (sección 10).

**Riesgos:** seguir invirtiendo en la única campaña activa sin refrescar creativo (fatiga confirmada) y sin CAPI conectada (optimización ciega por volumen, no por calidad de lead).

**Recomendaciones:** ver backlog consolidado, tareas de importancia alta en el bloque Meta Ads.

### 6.2 Políticas y algoritmo de Meta

Cubierto en profundidad solo por Claude Code (DOC-08), con fuentes oficiales citadas y fecha de consulta (18-08-2026): CAPI ya soporta eventos de mensajería (clave para el embudo 100% conversacional de DDC), Meta detecta origen de IA generativa automáticamente desde el 1-jun-2026, el ciclo de fatiga creativa bajó de 14-21 días a 5-7 días con Andromeda, y la política de "Privacidad y Atributos Personales" es el riesgo de rechazo más probable para el ángulo de miedo/urgencia que ya usa DDC (regla de compliance ya incorporada como criterio de aceptación obligatorio en DOC-07, marcada 🔒). El Informe 360 no cubre este eje — no es una omisión grave dado que es una investigación de plataforma muy específica, fuera del alcance de un diagnóstico estratégico de negocio.

### 6.3 Landing pages y CRO

**Hallazgos consolidados:** formulario largo (100-102 elementos en el dominio principal) sin versión corta para tráfico frío de Meta (DOC-02); CTA repetido sin variación; 57% de abandono de formulario confirmado con datos reales de GA4 (141 `form_start` vs. 61 `form_submit_*`, DOC-04, tarea G10 en DOC-05 y SL6 en DOC-13 — correctamente identificado como la misma tarea en ambos backlogs, sin duplicar). El Informe 360 no audita la landing a nivel de elementos de formulario, pero sí confirma el síntoma agregado: 77% del tráfico pagado es móvil y el 100% de las URL móviles están en Core Web Vitals "necesita mejora" (DOC-16) — coherente con que la fricción de conversión también tiene un componente de velocidad, no solo de diseño de formulario.

**Contradicción aparente, no confirmada:** DOC-02 (Alcance Técnico Landing) recomienda "formulario simplificado (nombre + teléfono)" como Prioridad 2; el subdominio servicios. según DOC-09 ya tiene formularios más cortos (48-77 elementos) que el dominio principal (100-102) — sin botón de WhatsApp en ninguna de sus 5 páginas. Es decir, el subdominio ya probó una versión más corta y aun así rinde peor en tráfico (12 sesiones/30d según DOC-04) — no hay evidencia suficiente en el corpus para saber si el problema real es el largo del formulario o la falta de tráfico/campañas activas hacia ese subdominio. Se clasifica como **no resuelto por falta de evidencia** — requiere test A/B real, no solo inferencia (así lo marca correctamente SL8 en DOC-13, con 2 semanas de test).

### 6.4 Auditoría técnica de las 14 URL

Cubierta en exclusiva y en profundidad por Claude Code (DOC-09): Meta Pixel ausente en las 14, sin excepción; 3 instalaciones de WordPress en 3 versiones distintas; 2 de 14 URL bloqueadas para buscadores (una posiblemente sin querer — la FAQ de convenios y condonaciones en servicios.); H1 duplicado en 8/14 por un bloque de agendamiento mal etiquetado; promedio de visibilidad IA de solo 42/100 (coherente con el hallazgo de DOC-04 de que ya existe tráfico real desde "AI Assistant", 9 sesiones/30d — no es un tema especulativo). El Informe 360 no baja a este nivel de granularidad por URL, pero sus cifras agregadas de indexación (45% del sitio) y Core Web Vitals móvil (100% "necesita mejora") son consistentes con — y cuantifican a nivel de sitio completo — lo que DOC-09 encontró en su muestra de 14 URL.

### 6.5 GA4

Ver 6.1-style detalle ya cubierto en la matriz de cobertura (sección 5) y en el resumen ejecutivo. Punto adicional: el hallazgo de mayor apalancamiento de todo el corpus GA4 es de bajísimo esfuerzo — marcar `form_submit_fiscalizacion_tributaria_cit` como conversión (G1 en DOC-05, 15 minutos), recuperando 19 conversiones reales/mes que hoy no se reportan a Google Ads. El Informe 360 no llega a este nivel de evento individual.

### 6.6 Google Search Console

Cubierto casi en exclusiva por el Informe 360 (DOC-16): 45% de indexación (56/123 páginas), tráfico orgánico cayendo activamente (-14% clics, -13% impresiones en 3 meses), CTR bajo (1,4-1,6%) pese a posición promedio decente (~7,7) — oportunidad de mejora de metadata sin necesidad de subir posición. Las auditorías Claude Code tocan Search Console solo tangencialmente (DOC-11 lo menciona como checklist de medición, DOC-10 como reporte trimestral contractual) — es una brecha real de cobertura del lado Claude Code, sin acceso propio documentado a la herramienta.

### 6.7 Google Ads

Cubierto en exclusiva por el Informe 360, con el detalle de que el acceso Claude Code estaba bloqueado (DOC-12: developer token pendiente de upgrade, marcado P0). Hallazgos de la agencia: autocanibalización de keywords ("abogado tributario" compite en dos campañas propias con CPC de $352 vs. $1.236-$1.618); objetivo de conversión "Cliente potencial cualificado" configurado pero con 0 conversiones y estado "Configuración errónea"; ~$205.000 CLP gastados en búsquedas de marca sin conversión registrada (posible conversión no registrada por teléfono/WhatsApp, a confirmar — la propia agencia lo marca como pendiente de confirmar, no como hallazgo cerrado); 15 de 18 campañas pausadas, varias fuera de giro. **Este es el bloque de mayor prioridad para validación en plataforma una vez resuelto el acceso** (DOC-12).

### 6.8 Gobernanza de cuentas

Cubierta por Claude Code vía DOC-12 (bloqueo de acceso a Google Ads, 3 cuentas de Google Ads no vinculadas a GA4 pendientes de aclarar titularidad) y DOC-10 (desglose contractual completo: quién debe tener acceso a qué, con cláusula de origen). El Informe 360 no aborda gobernanza de accesos como tema propio, aunque sí documenta indirectamente el mismo síntoma (6 dominios/subdominios sin gobernanza clara). Coincidencia parcial en el diagnóstico, exclusividad de Claude Code en el detalle accionable de accesos.

### 6.9 SEO técnico

Ver comparación relevante entre DOC-14 (28-05-2026, foco homepage) y DOC-01/DOC-09 (17/18-08-2026, foco sitio completo) en sección 9 — persisten sin resolver 3 meses después: schema LocalBusiness/Service, imagen Open Graph cuadrada, favicon 404. El Informe 360 no repite esta auditoría a nivel de código, pero su cifra de indexación (45%) es el resultado agregado de estos mismos problemas sin resolver.

### 6.10 SEO de contenidos

DOC-15 (SEO Public) reporta 11 palabras clave con cobertura completa, 40 con cobertura parcial, 8 sin cobertura, medido contra el contenido ya publicado en el sitemap. DOC-16 aporta el ángulo de negocio: cero artículos sobre Convenios y Condonaciones (uno de los 6 servicios pagados, y con la novedad normativa más grande del momento — condonación de hasta 80%), sin contenido sobre Ley 21.713, y un competidor (Abogados Tributarios Chile) dominando el terreno long-tail. Ambas fuentes son complementarias: DOC-15 mide cobertura de lo ya escrito, DOC-16 identifica lo que falta escribir y por qué importa comercialmente — el glosario de palabras clave de DOC-16 (sección 11 del propio Informe 360, con clusters por intención) es un insumo directamente aprovechable como brief editorial.

### 6.11 Medición y atribución

Tema transversal, ya cubierto en el resumen ejecutivo y en 6.1/6.5/6.6. Síntesis: el problema no es falta de herramientas (Pixel, GA4, GTM, objetivo de conversión de Google Ads y CRM ya existen), es que ninguna está completando el circuito hasta el dato de negocio real — coincidencia total entre ambas fuentes en el diagnóstico, con Claude Code aportando la solución técnica exacta y la agencia aportando la prueba de que, aun si se arregla, el problema de fondo (cierre 2,3%) es también de proceso comercial.

### 6.12 Integración de plataformas

Meta ↔ GA4 ↔ Google Ads ↔ Pipedrive no están conectadas entre sí en ningún punto verificado por ninguna de las dos fuentes. Dependencia crítica documentada explícitamente en el propio corpus Claude Code: la tarea T4 de DOC-07 (reenviar "lead calificado" a Meta vía CAPI) depende de T2 y T3, y a su vez habilita T14 (testear objetivo Leads) — es decir, las propias auditorías Claude Code ya modelan esta dependencia en cadena. Falta agregar a esa cadena la conexión con Pipedrive, que es donde el Informe 360 sitúa el verdadero cuello de botella.

### 6.13 Estrategia de marketing 360

DOC-11 (Guía 360° Claude Code) y DOC-16 (Informe 360 agencia) tienen el mismo nombre de género pero alcance distinto: DOC-11 es un playbook de mejores prácticas 2026 por plataforma (benchmark externo, BigSEO/Yoast/Metrix Digital); DOC-16 es un diagnóstico específico del negocio con datos propios (CRM, cuentas reales). No se contradicen — DOC-11 es el "qué se espera que funcione en 2026 según la industria", DOC-16 es "qué está pasando realmente en esta cuenta". Se complementan de forma natural: DOC-16 debería usar el checklist de DOC-11 como referencia de estándar, y DOC-11 debería incorporar el hallazgo de cierre comercial de DOC-16 en su Sección 4 (Funnels).

### 6.14 Tendencias y recomendaciones 2026

Ver sección 12.

### 6.15 WordPress técnico (auditoría profunda, DOC-19/DOC-20/DOC-21)

**Naturaleza aditiva de esta subsección:** cubre terreno que ninguna de las 16 fuentes originales (DOC-01 a DOC-16) auditó — inventario de plugins, panel de seguridad, contenido completo del blog vía WXR, y un escaneo en vivo section-by-section/form-by-form/button-by-button de 21 URLs. No reemplaza ni contradice los hallazgos SEO/técnicos ya consolidados en 6.4 y 6.9 — los profundiza.

**Hallazgos consolidados:** 21 plugins instalados (18 activos, 3 inactivos), actualizaciones automáticas deshabilitadas en los 21 sin excepción, dos herramientas de backup instaladas pero **ninguna activa** (sin evidencia de qué respalda el sitio hoy), licencia vencida en Code Snippets Pro (plugin que ejecuta PHP arbitrario en todo el sitio), y canibalización SEO confirmada en 7 posts publicados del blog (3 sobre "Auditoría Tributaria del SII", 4 sobre "Prescripción Tributaria" — uno de estos últimos, el post de 2020, es la página de mayor tráfico histórico real del sitio ya identificada en 6.9).

**Hallazgos exclusivos de esta subsección, sin contraparte en DOC-01 a DOC-16:**
- **Tercer sistema de tracking no documentado**: el subdominio `servicios.` corre un Google tag adicional (`GT-NCHTQWQT`, vía plugin Site Kit by Google) y una meta tag `facebook-domain-verification`, ninguno presente en el dominio principal ni en `diagnostico.` — el inventario de plugins original (DOC-18/19) solo cubrió el WordPress del dominio principal; `servicios.` es una instalación separada nunca inventariada hasta ahora.
- **RUT obligatorio como estándar de captación**: 3 de los 4 formularios de la home y la mayoría de los formularios de las 10 páginas de servicio piden RUT en el primer contacto — contradice directamente el checklist de DOC-11 (formulario simplificado 2-3 campos para tráfico frío) y agrega una causa técnica concreta al 57% de abandono de formulario ya documentado vía GA4 (DOC-04/DOC-05, tarea G10/SL6).
- **Meta description duplicada e inválida** en los 7 posts de blog auditados en vivo, con contenido de otro post pegado por error en 3 de ellos — indicio de causa raíz común con la canibalización (posts creados duplicando plantilla sin limpiar campos).
- El bug de título Yoast ya reportado (post id 9097) está **solo parcialmente corregido**: el campo social (`og:title`) y el schema ya son correctos, pero el `&lt;title&gt;` real que usa Google en el snippet de búsqueda sigue siendo el de otro post.

**Cruce con hallazgos ya consolidados en 6.4 (14 URL) y 6.9 (SEO técnico):** el escaneo en vivo confirma con datos exactos varios puntos ya señalados de forma agregada — GTM duplicado confirmado en 8 de 11 páginas escaneadas hoy (coincide con DOC-01/DOC-09), doble H1 confirmado en 5+ páginas (coincide con el hallazgo transversal de DOC-09), y refuerza con evidencia técnica más fuerte la contradicción sobre el Meta Pixel ya anotada en la sección 9 (cero rastro de `fbq()`/pixel en 11 páginas escaneadas hoy, vs. pixel activo según Meta Ads Manager en DOC-03) — el único indicio nuevo es la `facebook-domain-verification` de `servicios.`, que no confirma un pixel disparando pero sí una conexión real a Meta Business Manager a nivel de dominio.

**Riesgo de mayor impacto práctico:** actualizar WordPress/Elementor (ya priorizado como punto 5 en el README) no debería ejecutarse hasta confirmar el mecanismo de backup real vigente — las dos herramientas de respaldo instaladas están inactivas, y no hay evidencia documental de qué las reemplaza.

**Backlog:** ver DOC-22 (WP-01 a WP-14) y el backlog maestro DOC-23, que integra estos hallazgos junto con los de 6.1-6.14.

- **Aciertos completos:** el diagnóstico de que el pixel de Meta solo mide `PageView` (validado de forma independiente por DOC-03); la fragmentación de Analytics en dos propiedades (validado y ampliado por DOC-04); la identificación de que Convenios y Condonaciones no tiene campaña activa pese a ser servicio core con novedad normativa fuerte.
- **Aciertos parciales:** el diagnóstico de indexación (45%) es correcto y verificable (dato de Search Console), pero no profundiza en la causa técnica exacta (GTM duplicado, 3 WordPress distintos) que sí documentan DOC-01/DOC-09.
- **Recomendaciones válidas:** priorizar tracking antes que campañas nuevas (coincide con el orden de prioridad ya sugerido en el README del repo Claude Code); no reconstruir el histórico de Pipedrive, ordenar hacia adelante (decisión de negocio razonable, evita un esfuerzo de bajo retorno).
- **Hallazgos correctamente priorizados:** la Matriz de Priorización (sección 12 del Informe 360) sigue el orden que el propio cliente dio en la conversación de revisión — es una práctica metodológica sólida (prioriza según quien decide, no según un framework genérico) y **transparente**: documenta explícitamente cuándo un punto se ajustó por una aclaración del cliente, en vez de presentar el resultado final como si siempre hubiera sido así.

## 8. Exclusiones y omisiones

- **Omitido por la agencia:** profundidad de plataforma (Lighthouse por URL, eventos GA4 individuales, código fuente, IDs de contenedor GTM, políticas de IA generativa de Meta 2026).
- **Omitido por Claude Code:** CRM/Pipedrive completo, Google Ads a nivel de cuenta y keyword (por bloqueo de acceso, documentado — no negligencia), panorama competitivo, contexto normativo tributario como motor de demanda de contenido.
- **Fuera del alcance de ambos:** auditoría de WhatsApp Business API a nivel de plantillas y costos reales (DOC-11 lo señala como "revisar antes de automatizar", pero ninguna de las dos fuentes trae cifras propias de WhatsApp); auditoría de email marketing / MailChimp más allá de la mención contractual en DOC-10.
- **Exclusiones justificadas:** el Informe 360 excluye explícitamente reconstruir el histórico de Pipedrive (decisión de negocio del cliente, documentada en el propio informe). Las auditorías Claude Code excluyen SEO off-page/backlinks salvo mención tangencial en DOC-11 — la auditoría de perfil de enlaces (DOC-16: solo 8 enlaces externos, 6 del mismo dominio) queda como hallazgo exclusivo de la agencia sin contraparte técnica Claude Code, pero no hay evidencia de que esto sea un vacío intencional del lado Claude Code, más bien no estaba en el alcance de ninguno de los documentos encargados.
- **Exclusiones problemáticas:** ninguna de gravedad alta. La más relevante es que ninguna de las dos fuentes, hasta la fecha de este reporte, verificó en vivo si el ajuste de conversión de GA4 (G1, 15 minutos) ya se ejecutó — sigue como tarea abierta en el backlog consolidado.

## 9. Contradicciones y diferencias

| Tema | Posición Claude Code | Posición agencia | Evidencia | Explicación probable | Veredicto | Importancia | Acción requerida |
|---|---|---|---|---|---|---|---|
| Cifras de la campaña "Diagnósticos Gratuitos" | Gasto $5.338.077, 4.858 resultados, $1.099/resultado (DOC-03, capturado 17/18-08) | Gasto $5.070.552, 4.655 resultados, $1.089/resultado (DOC-16, capturado antes, "histórico hasta jul-2026") | Ambas cifras vía acceso directo a Meta (MCP vs. Ads Manager) | Fecha de captura distinta — DOC-03 es ~2-3 semanas posterior y la campaña sigue activa y acumulando gasto/resultados a diario; la dirección de la diferencia (todo mayor en la captura más reciente) es consistente con eso | Diferencia temporal | Media | Ninguna — no requiere corrección, ambas cifras son correctas para su fecha de captura |
| H1 genérico en homepage | No reportado como hallazgo en DOC-01/DOC-09 (agosto) | No evaluado por el Informe 360 tampoco | DOC-14 (mayo) sí lo reportó como hallazgo #4 | Alcance distinto — DOC-14 auditó la homepage en detalle; DOC-01/DOC-09 auditan alcance técnico general y páginas de servicio/campaña, no vuelven a listar la homepage punto por punto | Diferencia de alcance, no contradicción | Baja | Confirmar en plataforma si el H1 de la homepage sigue siendo genérico — no resuelto por falta de evidencia reciente |
| Campaña CAE: "armada en un fin de semana, activa cerca de una semana" (relato del cliente en DOC-16) vs. gasto acumulado ~$1.000.000 CLP en 3 campañas CAE con miles de resultados (DOC-03) | Datos de plataforma vía MCP: gasto y resultados acumulados, sin fecha de inicio exacta más allá de "pausada desde abril 2026" | Caracterización cualitativa del propio cliente en conversación de revisión | DOC-03 (cifras), DOC-16 (cita textual del cliente) | No necesariamente contradictorio — "armado en un fin de semana" puede referirse al tiempo de producción del anuncio, no a la duración de la campaña activa; sin fecha de inicio exacta en ningún documento no se puede confirmar cuánto tiempo estuvo realmente activa | Contradicción aparente, no confirmada | Baja | Confirmar fecha de inicio exacta de las 3 campañas CAE en Ads Manager si se retoma el proyecto |
| Opportunity Score 96/100 (Meta) vs. puntuación de auditoría 43/100 (DOC-03) | Ambas cifras del propio corpus Claude Code | No evaluado por la agencia | DOC-03, DOC-08 | Escalas distintas — Opportunity Score es un checklist estructural de configuración, no mide eficiencia real; DOC-08 ya lo explica y reconcilia explícitamente | Diferencia metodológica (ya resuelta dentro del propio corpus Claude Code) | Baja | Ninguna — ejemplo de buena práctica interna de reconciliación, se mantiene el resto del reporte |

## 10. Auditoría de cifras

| Métrica | Valor | Unidad | Periodo | Fuente/Doc | Página/sección | Método de cálculo | Respaldo | Confiabilidad | Cifra comparable | Dif. absoluta | Dif. % | Explicación probable | Veredicto |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Gasto "Diagnósticos Gratuitos" | 5.338.077 | CLP | Hasta 17/18-08-2026 | DOC-03 | Tabla "Estructura de campañas" | Extracción directa Meta Ads MCP | Sí | Alta | 5.070.552 (DOC-16) | 267.525 | 5,3% | Diferencia temporal de captura (ver sección 9) | Metodológicamente distinta |
| Resultados "Diagnósticos Gratuitos" | 4.858 | conversaciones | Hasta 17/18-08-2026 | DOC-03 | ídem | ídem | Sí | Alta | 4.655 (DOC-16) | 203 | 4,4% | Diferencia temporal de captura | Metodológicamente distinta |
| Gasto Estrategia CAE Centralizada | 901.929 | CLP | Histórico, pausada abr-2026 | DOC-03 y DOC-16 | Tablas de campañas | Extracción directa Meta Ads | Sí, ambas fuentes | Alta | Idéntica en ambas fuentes | 0 | 0% | Campaña pausada, cifra estable en el tiempo — corroboración cruzada fuerte | Respaldada |
| Gasto Prescripción CAE y Defensa CAE | 50.000 c/u | CLP | Histórico, pausada abr-2026 | DOC-03 y DOC-16 | ídem | ídem | Sí, ambas fuentes | Alta | Idéntica en ambas fuentes | 0 | 0% | Corroboración cruzada fuerte | Respaldada |
| Inversión histórica total Meta | 6.138.657 | CLP | jun-2023–jul-2026 | DOC-16 | Sección 6 | Suma declarada por la agencia | Parcial | Media | No hay total explícito en DOC-03 para contrastar; suma manual de las filas de DOC-03 da ~6.406.027 | ~267.370 | ~4,4% | Consistente con la diferencia temporal ya identificada (DOC-03 más reciente, más gasto acumulado) + una fila adicional en DOC-16 ("Tráfico - Ley de alivio tributario Archivada", $155) no listada en DOC-03 | Parcialmente respaldada |
| Tasa de cierre real de leads | 2,3% | % | Histórico Pipedrive | DOC-16 | Sección 3 | 135 ganados / 5.950 tratos totales | Sí, con matiz reconocido por el propio cliente (¬70% de "Abiertos" son prospección histórica, no leads reales) | Media — la propia agencia señala la limitación | Sin cifra comparable en el corpus Claude Code | — | — | Sin fuente Claude Code para contrastar (sin acceso a CRM) | No verificable por este corpus (no hay segunda fuente) |
| Indexación del sitio | 45% | % (56/123 páginas) | Al momento de la auditoría (agosto 2026) | DOC-16 | Sección 8 | Datos de Search Console | Sí | Alta | Sin cifra directamente comparable en DOC-09 (que audita solo 14 URL, no el sitio completo) | — | — | Dato no comparable — universos distintos (14 URL de campaña vs. sitio completo) | Respaldada (dato no comparable con el corpus Claude Code, no contradictorio) |
| Rendimiento Lighthouse promedio (14 URL) | 75/100 | puntaje | 18-08-2026 | DOC-09 | Tabla resumen | Lighthouse, medición en frío por URL | Sí | Alta | Consistente cualitativamente con "100% de URL móviles necesita mejora" de DOC-16 (Search Console, datos de campo) | — | — | Metodologías distintas (laboratorio vs. campo) mismo diagnóstico direccional | Respaldada |

## 11. Jerarquización de hallazgos

### Alta

1. **Cerrar el circuito de medición de Meta: Pixel + CAPI + CTWA vía `ctwa_clid`.** Dependencias: bloquea toda optimización de campaña futura. Impacto: alto (hoy se optimiza a ciegas por volumen). Confianza: alta (2 fuentes independientes). *(DOC-03, DOC-08, DOC-16 → TASK-001 a TASK-004 en el backlog)*
2. **Resolver el bloqueo de acceso a Google Ads (upgrade developer token).** Dependencias: bloquea toda auditoría y corrección de Google Ads del lado Claude Code. Impacto: alto (autocanibalización de keywords, objetivo de conversión roto). Urgencia: alta (marcado P0 por la propia auditoría Claude Code). *(DOC-12 → TASK-005)*
3. **Corregir el objetivo de conversión "Cliente potencial cualificado" en Google Ads (estado "Configuración errónea").** Depende de la tarea anterior. Impacto: alto — sin esto Google no puede optimizar por calidad de lead. *(DOC-16 → TASK-006)*
4. **Marcar `form_submit_fiscalizacion_tributaria_cit` como conversión en GA4 y en Google Ads.** Esfuerzo mínimo (15 min), impacto alto (19 conversiones/mes hoy invisibles). Quick win, sin dependencias. *(DOC-05 → TASK-007, TASK-008)*
5. **Instrumentar GA4 completo en diagnostico.defensordelcontribuyente.cl.** Es el formulario de mayor intención del ecosistema y hoy no genera ni un evento medible. *(DOC-04, DOC-05 → TASK-009)*
6. **Ordenar Pipedrive hacia adelante: definir fuente de verdad para tasa de cierre y conectar con Meta/Google vía CAPI/API de conversión.** Impacto: el hallazgo de negocio más importante de todo el corpus. *(DOC-16 → TASK-010, TASK-011)*
7. **Refrescar o pausar "Video 22" y activar 2-3 creativos del banco de 70.** Fatiga confirmada con datos en vivo (-40,72% CTR). *(DOC-03, DOC-08 → TASK-012)*
8. **Consolidar dominios/GTM y decidir el futuro de servicios./diagnostico. como propiedades separadas o unificadas.** Bloquea la resolución de la fragmentación de indexación (45%). *(DOC-01, DOC-04, DOC-16 → TASK-013, TASK-014)*
9. **Autorizar y actualizar oferta CAE vigente antes de cualquier relanzamiento.** Bloquea la reactivación de las campañas más eficientes en costo por resultado. *(DOC-06 → TASK-015)*

### Media

1. Investigar el 57% de abandono de formulario (141 `form_start` vs. 61 `form_submit`). *(DOC-04, DOC-05, DOC-13 → TASK-016)*
2. Aplicar la recomendación "mixed_formats" en el ad set activo (acción gratuita, +4 pts Opportunity Score). *(DOC-08 → TASK-017)*
3. Corregir moneda (USD→CLP) y categoría de industria de la propiedad GA4 servicios. *(DOC-05 → TASK-018, TASK-019)*
4. Negativizar keywords cruzadas entre campañas propias de Google Ads (autocanibalización). *(DOC-16 → TASK-020)*
5. Reactivar las 3 audiencias lookalike como semilla de Advantage+ Audience (excluyendo naming CAE). *(DOC-07 → TASK-021)*
6. Combinar/minificar CSS de Elementor (37-51 hojas de estilo por página) y reducir JS no usado. *(DOC-01, DOC-13 → TASK-022, TASK-023)*
7. Mejorar metadata (title/meta description) para capturar más CTR en posiciones ya buenas (~7,7 promedio, CTR 1,4-1,6%). *(DOC-16 → TASK-024)*
8. Producir contenido sobre Convenios y Condonaciones y Ley 21.713 (gap de contenido con demanda normativa confirmada). *(DOC-16 → TASK-025)*
9. Crear checklist de compliance de copy (regla de tercera persona, ya definida como criterio de aceptación en DOC-07). *(DOC-07 → TASK-026)*

### Baja

1. Ajustar imagen Open Graph a 1200×630 y completar etiquetas Twitter Card. *(DOC-01, DOC-13, DOC-14 → TASK-027)*
2. Resolver favicon 404. *(DOC-01, DOC-14 → TASK-028)*
3. Corregir nomenclatura de campañas Meta (fechas inconsistentes). *(DOC-03 → TASK-029)*
4. Revisar compliance del creativo con cita de tercero (@rfantuzzih). *(DOC-03 → TASK-030)*
5. Implementar schema FAQPage y Review/AggregateRating. *(DOC-09 → TASK-031)*
6. Construir perfil de backlinks (hoy 8 enlaces externos, 6 del mismo dominio). *(DOC-16 → TASK-032)*

## 12. Recomendaciones 2026

**Acciones inmediatas (0-2 semanas):** cerrar el circuito de medición de Meta y Google Ads (Alta #1-#4 de la sección 11) — son, en conjunto, menos de un día de trabajo técnico y desbloquean todo lo demás.

**Corto plazo (mes 1):** resolver el acceso a Google Ads, ordenar Pipedrive hacia adelante, refrescar el anuncio activo de Meta, decidir la arquitectura de dominios/GA4.

**Mediano plazo (trimestre 1):** producción de contenido sobre el gap normativo identificado (Convenios/Condonaciones, Ley 21.713), consolidación de plataforma (WordPress/Elementor), construcción de perfil de backlinks, implementación de schema pendiente.

**Algoritmo/políticas de Meta (DOC-08):** priorizar CAPI de mensajería como prerrequisito antes de escalar presupuesto; usar avatar IA para prospección fría y testimonio real para remarketing (evidencia 2026: CPA similar en frío, testimonio real gana 20-25% en conversión en cálido); todo copy de ángulo miedo/urgencia debe pasar el filtro de "atributos personales implícitos" antes de publicarse.

**Medición:** el estándar 2026 (Enhanced Conversions, Consent Mode V2, AI Max de Google, Advantage+ de Meta) depende de señales de conversión de calidad — sin resolver Pixel/CAPI/objetivo de conversión, ninguna plataforma puede optimizar bien en 2026, independiente de cuánto se invierta en pauta (DOC-16, sección 10).

**SEO:** AI Overviews ya aparece en ~48% de las búsquedas (DOC-11) — la meta ya no es solo posicionar, es ser la fuente citada; esto conecta directamente con el hallazgo de DOC-04 de que ya hay 9 sesiones/30d desde "AI Assistant" y con el 42/100 de visibilidad IA de DOC-09. Generar `llms.txt` y reforzar FAQs con respuesta directa en el primer párrafo.

**Contenido:** usar el glosario de palabras clave de DOC-16 (organizado por intención/cluster) como brief editorial directo, cruzado con la cobertura ya medida en DOC-15 (SEO Public) para priorizar los 8 términos sin cobertura y los de mayor volumen entre los 40 de cobertura parcial.

**Gobernanza:** cerrar la aclaración de titularidad de las 3 cuentas de Google Ads no vinculadas (DOC-12) antes de dar acceso amplio a cualquier agencia nueva; verificar trimestralmente titularidad de todos los activos digitales, tal como ya establece DOC-10 (cláusula C18.c del contrato vigente).

**Riesgos de no implementación:** si no se cierra el circuito de medición antes de escalar presupuesto en campañas nuevas (Google/Meta), el diagnóstico de ambas fuentes coincide en que el resultado más probable es gastar más sin poder saber si funciona — y, según el hallazgo central del Informe 360, incluso si funciona, sin ordenar el proceso comercial en Pipedrive la tasa de cierre seguiría rondando el 2%.

## 13. Conclusión

El Informe 360 de la agencia es **confiable y metodológicamente honesto** — cuando se ajustó una conclusión por una aclaración del cliente, lo documentó explícitamente en vez de presentar el resultado como si siempre hubiera sido así, y reconoce con claridad los límites de sus propios datos (Pipedrive histórico "no confiable por sí solo"). Su cobertura de negocio (CRM, Google Ads, competencia) es información que las auditorías Claude Code simplemente no tenían — en el caso de Google Ads, por un bloqueo de acceso ya documentado, no por descuido.

Las auditorías Claude Code, por su parte, aportan una profundidad técnica de plataforma que el Informe 360 no alcanza — con la ventaja adicional de estar validadas con datos en vivo vía MCP directo a Meta y GA4, no solo revisión manual del panel.

**Grado de coincidencia:** alto donde ambas se superponen (Pixel, fragmentación de medición, rendimiento móvil) — sin una sola contradicción confirmada en todo el corpus, solo una diferencia de cifra explicable por fecha de captura y dos diferencias de alcance sin evidencia suficiente para resolver.

**Principal brecha:** la ausencia total de datos de Pipedrive del lado Claude Code, que es donde el Informe 360 sitúa el verdadero cuello de botella del negocio.

**Secuencia recomendada de implementación:** (1) medición Meta+Google (días), (2) acceso Google Ads + corrección de objetivo de conversión (semanas, depende de aprobación de Google), (3) Pipedrive hacia adelante (semanas, decisión ya tomada por el cliente), (4) creativo y campañas nuevas (mes 1 en adelante, una vez que medir tenga sentido), (5) contenido y SEO estructural (trimestre 1).

## 14. Anexos

### Matriz de trazabilidad
Ver columna "Fuente" en las secciones 5, 9, 10 y 11 — todo hallazgo de este reporte referencia su(s) documento(s) de origen por ID.

### Documentos no procesados
Ninguno resultó ilegible. `guiones-y-configuracion-7-temas.md` y el desglose completo de `estructura-tareas-clickup.md` (108 filas) se usaron como contexto de apoyo, no se extrajeron al detalle de cifras (ver nota en sección 4).

### Hallazgos no resueltos
- Duración exacta de las campañas CAE activas (sección 9).
- Si el H1 genérico de la homepage (DOC-14, mayo) sigue vigente o ya se corrigió (sección 9).
- Si las conversiones de búsquedas de marca sin registro ($205.000 CLP, DOC-16) efectivamente convierten por teléfono/WhatsApp sin quedar registradas.
- Total exacto de inversión histórica en Meta Ads (diferencia de ~4,4% entre fuentes, sección 10).

### Glosario
Ver `references/taxonomia-hallazgos.md` de la skill `auditoria-consolidada-marketing-360` para la tabla completa de normalización de términos usada en este análisis (Meta Pixel/CAPI, GA4, landing page, eventos vs. conversiones, etc.).

### Registro de validaciones pendientes en plataforma
Todos los hallazgos de la sección 6.7 (Google Ads) requieren validación directa una vez resuelto el acceso (DOC-12). El estado de ejecución de G1 (marcar conversión GA4) no fue verificado en vivo para este reporte.

### Fuentes web utilizadas
Ninguna búsqueda web nueva se ejecutó para este reporte — las fuentes oficiales citadas en la sección 12 (Meta, Google) provienen íntegramente de DOC-08 y DOC-11, ya consultadas y fechadas por las auditorías Claude Code originales (18-08-2026).

### Addendum WordPress (19-08-2026, ver nota 1.2 y sección 6.15)
La auditoría técnica WordPress (DOC-19/DOC-20) tampoco ejecutó búsquedas web — es documental (WXR + panel de plugins) y en vivo (HTML de 21 URL, sin JavaScript ejecutado, sin autenticación, sin pentesting). Limitación declarada: cualquier tag inyectado dinámicamente por GTM en el navegador (incluido un eventual Meta Pixel) no es detectable por fetch de HTML estático — no se investigaron vulnerabilidades (CVE) de plugins, pendiente de autorización expresa.
