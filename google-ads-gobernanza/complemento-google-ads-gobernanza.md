# Complemento — Acceso a Google Ads y Gobernanza de Cuentas

**Generado:** 18-08-2026 · **Alcance:** este documento **complementa** la línea de auditorías ya en curso en este repositorio (Meta Ads, GA4, SEO/Landing, backlogs ClickUp) — no la reemplaza ni repite sus hallazgos. Cubre exclusivamente dos cosas que no aparecían documentadas hasta ahora: el estado de acceso a Google Ads, y un mapa consolidado de gobernanza de cuentas entre las 4 plataformas conectadas (Meta, Google Ads, GA4, sitio web).

**Fuente:** Google Ads API (vía MCP conectado), Google Analytics Data API, Meta Ads MCP — acceso directo y autorizado, mismo día.

> Nota: la [auditoría de cuenta Meta Ads](../campanas-ads/auditoria-cuenta-meta-ads.md) y el [ajuste de alcance CAE](../campanas-ads/plan-ajustes-post-cae-clickup.md) siguen vigentes tal como están documentados. Este complemento no vuelve a evaluar campañas de Meta.

## Hallazgo principal: el acceso programático a Google Ads está bloqueado

Al intentar consultar las cuentas de Google Ads conectadas a este workspace, la API respondió:

> "The developer token is only approved for use with test accounts. To access non-test accounts, apply for Basic or Standard access."

Esto significa que **ninguna herramienta conectada a este entorno puede leer ni gestionar datos reales de Google Ads** — ni esta auditoría, ni futuras automatizaciones — hasta que se apruebe el nivel de acceso Basic o Standard del token de desarrollador en el Centro de API de Google Ads (trámite que hace Google, no la agencia).

**Cuentas visibles pero no consultables:**

| Customer ID | Vinculada a GA4 | Estado |
|---|---|---|
| 8985279729 | Sí — vinculada a la propiedad `defensordelcontribuyente.cl` (creada 05-05-2025 por tributariodefensor@gmail.com) | Datos bloqueados |
| 2856806495 | No detectada | Datos bloqueados |
| 5789067229 | No detectada | Datos bloqueados |
| 5020760344 | No detectada | Datos bloqueados |

Por qué importa: según los datos de Google Analytics ya auditados en este repositorio, **Paid Search es el canal de mayor volumen** del sitio principal (muy por encima de cualquier otro canal). Es el canal más grande del negocio y hoy nadie puede auditar su estructura de campañas, palabras clave, Quality Score ni gasto real de forma programática — solo a través de la interfaz de Google Ads Manager directamente.

**Acción recomendada:** solicitar la aprobación de acceso Basic/Standard del developer token en el Google Ads API Center antes de que la agencia entrante intente automatizar reportes o gestión de Google Ads.

## Mapa de gobernanza de accesos

| Sistema | Estado de acceso (18-08-2026) | Detalle |
|---|---|---|
| Meta Business Manager / Ad Account | OK | Cuenta activa, pago al día, sin errores de entrega |
| Meta Page | Parcial | Términos de Lead Generation no aceptados (no bloqueante hoy: la estrategia actual no usa Lead Ads nativos) |
| Google Ads API | **Bloqueado** | Developer token solo aprobado para cuentas de prueba |
| Google Analytics 4 | OK | Acceso de edición confirmado a las 2 propiedades de la cuenta 350833440 |
| GTM | No auditable por API | Requiere acceso directo a la interfaz de Google Tag Manager |
| WordPress / hosting / DNS | Fuera de alcance | Sin conector disponible en este entorno; solicitar credenciales directamente al traspasar accesos a la agencia entrante |

## Checklist (para ClickUp)

Ver detalle con estimación de tiempos y responsables sugeridos en [`/descargables/Complemento-Google-Ads-Gobernanza-ClickUp.docx`](../descargables/Complemento-Google-Ads-Gobernanza-ClickUp.docx).

| Prioridad | Acción |
|---|---|
| P0 | Solicitar aprobación Basic/Standard del developer token de Google Ads |
| Medio | Confirmar responsable de acceso/administración de cada una de las 4 plataformas antes del traspaso formal a la agencia entrante |
| Bajo | Revisar si las 3 cuentas de Google Ads no vinculadas a GA4 (2856806495, 5789067229, 5020760344) son relevantes para Defensor del Contribuyente o corresponden a otros clientes visibles por el mismo token compartido |
