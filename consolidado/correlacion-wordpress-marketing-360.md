# Correlación — Auditoría Técnica WordPress × Auditorías de Marketing 360°

**Empresa/cliente:** Defensor del Contribuyente (defensordelcontribuyente.cl)
**Fecha de emisión:** 19 de agosto de 2026
**Versión:** v1.0
**Naturaleza:** documento complementario — generado con la skill `auditoria-consolidada-marketing-360` en modo correlación (no compara contra el Informe 360 de la agencia; cruza una auditoría técnica nueva de WordPress contra las auditorías de marketing ya vigentes en este repositorio).

## 1. Resumen ejecutivo

La auditoría técnica de WordPress (DOC-19) no contradice ninguno de los hallazgos ya documentados en SEO (DOC-01) y Landing/Meta Ads (DOC-02) — al contrario, **confirma con evidencia del propio panel de administración** varios de ellos (versiones exactas de Elementor, ausencia de plugin dedicado de tracking) y agrega **cuatro hallazgos completamente nuevos** que ninguna auditoría anterior había cubierto porque ninguna tuvo acceso al panel de plugins ni al contenido completo del blog: (1) no hay evidencia de backup activo, (2) canibalización SEO real en 7 posts publicados del blog, (3) un bug de título SEO en producción, y (4) una licencia vencida en el plugin que ejecuta código personalizado en todo el sitio.

El hallazgo de mayor impacto práctico es el de backup: **el punto 5 del "Orden de prioridad sugerido" del README (Actualización de plataforma) no debería ejecutarse hasta resolver el WPR-1** — actualizar WordPress/Elementor sin backup confirmado es el tipo de riesgo que un traspaso de agencia no puede permitirse.

## 2. Metodología

Fuentes analizadas: DOC-01, DOC-02, DOC-13 (ya vigentes en el repositorio) contra DOC-17, DOC-18 y DOC-19 (nuevas, incorporadas en esta sesión). Criterio de correlación: cada hallazgo de DOC-19 se contrastó primero para ver si ya existía en DOC-01/DOC-02 (confirmación cruzada), luego se marcó como hallazgo exclusivo si no aparecía en ninguna auditoría anterior. No hubo cifras irreconciliables — las pocas cifras compartidas (versión de Elementor, versión de Elementor Pro) coinciden exactamente entre fuentes independientes, lo que sube la confianza de ambas.

## 3. Inventario documental (extracto — IDs nuevos de esta sesión)

| ID | Documento | Ruta | Origen | Fecha |
|---|---|---|---|---|
| DOC-17 | Exportación WXR del sitio | Proporcionado por el cliente, no versionado (archivo binario grande, 9,5 MB) | Cliente (export nativo de WordPress) | 19-08-2026 |
| DOC-18 | Transcripción — Plugins y seguridad WordPress | Proporcionado por el cliente, no versionado (fuente ya resumida en DOC-19) | Cliente (transcripción IA + verificación humana) | 19-08-2026 |
| DOC-19 | Auditoría Técnica — WordPress (Plugins, Seguridad y Contenido) | `wordpress/auditoria-tecnica-wordpress-plugins-seguridad.md` | Claude Code | 19-08-2026 |

DOC-17 y DOC-18 no se suben al repositorio (uno es un binario de 9,5 MB sin valor de lectura directa, el otro es una transcripción intermedia ya consolidada en DOC-19) — se referencian por trazabilidad, no se versionan.

## 4. Correlaciones confirmadas

| Hallazgo | DOC-01 / DOC-02 (SEO / Landing) | DOC-19 (WordPress) | Veredicto |
|---|---|---|---|
| Versión de Elementor 4.1.4 / Elementor Pro 4.1.2, con updates a 4.2.2 / 4.2.1 | DOC-01, Prioridad 4: "Elementor (hoy 4.1.4)... Elementor Pro (hoy 4.1.2)" | Confirmado exacto en el panel de plugins (DOC-18) | **Coincidencia total** — dos fuentes independientes (HTML público vs. panel de administración) confirman el mismo dato, sube la confianza de ambas |
| WordPress desactualizado | DOC-01: "WordPress 6.8.8... persiste" | DOC-18 muestra "actualización disponible a 7.0.4" sin indicar la versión de origen exacta | **Coincidencia parcial** — mismo hallazgo, DOC-19 no puede confirmar la versión de origen (6.8.8) porque el panel de plugins no la transcribe, solo la de destino |
| GTM duplicado (Prioridad 1 crítica en DOC-01 y DOC-02) | Confirmado en el HTML público | **No hay ningún plugin dedicado de Google Tag Manager / Site Kit en el listado de 21 plugins** | **Hallazgo complementario que explica el "cómo":** los contenedores GTM casi con certeza están inyectados manualmente vía Code Snippets Pro o directo en el tema, no gestionados por un plugin — esto cambia la forma de resolver la tarea: hay que revisar los snippets activos en Code Snippets Pro, no desinstalar un plugin |
| Meta Pixel ausente (Prioridad 1 bloqueante en DOC-02) | Confirmado ausente en las 14 URL de campaña | Mismo patrón: no hay plugin dedicado de Meta Pixel (tipo PixelYourSite) en el listado | **Hallazgo complementario** — instalar el Pixel probablemente pasa por Code Snippets Pro o por el contenedor GTM ya consolidado, no por un plugin nuevo |
| 51 hojas de estilo CSS sin combinar (DOC-01, Prioridad 2) | "Revisar y activar la opción de combinación de CSS en WP Rocket" | WP Rocket está **activo** pero con auto-actualizaciones desactivadas | **Confirma la causa exacta**: el plugin correcto ya está instalado y activo, el problema es de configuración, no de instalación |
| Compatibilidad de plugins antes de actualizar Elementor (DOC-01, Prioridad 4, criterio de aceptación) | Recomendación genérica: "Confirmar compatibilidad de plugins activos antes de cada actualización" | El propio panel de Elementor identifica **exactamente 3 plugins** con compatibilidad no probada: Cool FormKit Lite, Dynamic Visibility for Elementor, Elementor Pro | **Precisa una recomendación genérica con evidencia concreta** — ya no es "revisar todo", es "revisar estos 3" |

## 5. Hallazgos nuevos — exclusivos de la auditoría WordPress

Ninguna auditoría anterior podía cubrir esto porque ninguna tuvo acceso al panel de plugins ni al WXR completo:

1. **Sin evidencia de backup activo** (WPR-1) — las dos herramientas de respaldo instaladas están inactivas. Riesgo que condiciona cualquier trabajo de actualización de plataforma.
2. **Licencia vencida en Code Snippets Pro** (WPR-2) — el plugin que ejecuta código personalizado en todo el sitio no recibe el parche de seguridad más reciente.
3. **Canibalización SEO en el blog** (WPR-3) — 3 posts publicados sobre "Auditoría Tributaria del SII" y 4 sobre "Prescripción Tributaria" compitiendo entre sí. DOC-01 evalúa la categoría "Contenido" en 60/100 pero solo audita la home — este hallazgo explica una causa concreta de deuda de contenido que la auditoría SEO no había cuantificado porque no llegó al blog.
4. **Bug de título SEO en producción** (WPR-7) — el post id=9097 muestra el título de otro post en los resultados de búsqueda.

## 6. Ajuste propuesto al orden de prioridad del README

El punto 5 actual ("Actualización de plataforma — WordPress/Elementor") debería subdividirse:

- **5a. Confirmar mecanismo de backup vigente** (WPR-1) — precondición, no se ejecuta nada de la 5b sin esto resuelto.
- **5b. Actualizar Elementor/Elementor Pro/WordPress** — como estaba, ahora con la lista concreta de 3 plugins a validar antes.

## 7. Jerarquización combinada (alta prioridad, con ID de tarea)

| Prioridad | Tarea | ID backlog | Depende de |
|---|---|---|---|
| Alta | Confirmar mecanismo de backup real vigente | WP-01 | — |
| Alta | Corregir título Yoast incorrecto (id 9097) | WP-04 | — |
| Alta | Ubicar y consolidar contenedores GTM (probablemente en Code Snippets Pro) | WP-10 | — |
| Alta | Resolver canibalización SEO — Prescripción Tributaria (incluye la página de mayor tráfico) | WP-06 | — |
| Alta | Renovar licencia de Code Snippets Pro | WP-02 | — |

## 8. Anexos — limitaciones

- No se verificaron vulnerabilidades (CVE) de ningún plugin contra fuentes externas — pendiente de autorización expresa, no incluido en esta correlación.
- DOC-17 (WXR) y DOC-18 (transcripción de plugins) no se versionan en el repo por ser un binario grande y una fuente intermedia ya consolidada en DOC-19, respectivamente.
- El nombre exacto del tema activo (inferido como Hello Elementor/Hello Biz en DOC-19) no se pudo confirmar al 100%.
