# Auditoría Técnica — WordPress (Plugins, Seguridad y Contenido)

**Sitio:** defensordelcontribuyente.cl
**Fecha:** 19 de agosto de 2026
**Preparado para:** equipo de marketing entrante / traspaso de la presencia digital
**Método:** auditoría documental externa — sin conexión al panel de WordPress, sin escaneo del dominio, sin acceso a archivos del servidor. Basada en tres fuentes que Víctor exportó y entregó directamente:

1. Exportación WXR (`WordPress eXtended RSS`) del contenido completo del sitio, generada el 19-08-2026 desde Herramientas → Exportar.
2. Transcripción del panel de administración: listado de plugins instalados y panel de seguridad de Wordfence, capturada el 19-08-2026.
3. Captura del menú lateral del panel de administración (confirmación cruzada de plugins activos, sin nuevos hallazgos).

No se investigaron vulnerabilidades (CVE) en fuentes externas — queda pendiente de autorización expresa y se declara explícitamente en cada sección donde aplica.

---

## 1. Inventario de plugins

21 plugins instalados: 18 activos, 3 inactivos. Actualizaciones automáticas **deshabilitadas en los 21**, sin excepción. 8 plugins con actualización disponible. 1 drop-in sin identificar en la transcripción.

| Plugin | Versión | Estado | Función | Update disponible |
|---|---|---|---|---|
| All-in-One WP Migration and Backup | 7.106 | Inactivo | Migración/Respaldo | 7.109 |
| All-in-One WP Migration Unlimited Extension | 2.66 | Inactivo | Migración/Respaldo (extensión) | — |
| Code Snippets Pro (Premium) | 3.6.8 | Activo | Código personalizado | 3.8.0 (requiere licencia) |
| Cool FormKit Lite | 2.7.3 | Activo | Formularios / extensión Elementor | 2.7.7 |
| Duplicator Pro | 4.5.21 | Inactivo | Migración/Respaldo | — |
| Dynamic Visibility for Elementor | 6.0.4 | Activo | Extensión Elementor | — |
| Elementor | 4.1.4 | Activo (no desactivable) | Constructor visual | 4.2.2 |
| Elementor Pro | 4.1.2 | Activo | Extensión Elementor | 4.2.1 |
| Enable Media Replace | 4.2.2 | Activo | Gestión de medios | — |
| Imunify Security | 4.1.0 | Activo | Seguridad | — |
| JetEngine | 3.8.11.1 | Activo | Contenido dinámico (CPT/taxonomías) | 3.8.14.2 |
| Metricool | 2.0.2 | Activo | Analítica/RRSS | — |
| PublishPress Capabilities Pro | 2.18.1 | Activo | Roles y permisos | — |
| Simple Local Avatars | 2.8.6 | Activo | Experiencia editorial | — |
| Wordfence Security | 8.2.2 | Activo | Seguridad | 9.0.0 |
| WP Mail SMTP Pro | 3.9.0 | Activo | Correo | — |
| WP Rocket | 3.18 | Activo | Rendimiento | — |
| WPS Hide Login | 1.9.18 | Activo | Seguridad (acceso) | 1.9.19 |
| Yoast Duplicate Post | 4.7 | Activo | Experiencia editorial | — |
| Yoast SEO | 27.9 | Activo | SEO | — |
| Yoast SEO Premium | 27.9 | Activo | SEO | — |
| *Drop-in no identificado* | N/D | N/D | No determinado | — |

**Dependencias confirmadas en el panel:** Elementor es requerido por Cool FormKit Lite, Dynamic Visibility for Elementor y Elementor Pro (por eso no se puede desactivar). Yoast SEO es requerido por Yoast SEO Premium.

**Compatibilidad no verificada (dato del propio panel de Elementor, no una alarma generada por este análisis):** frente a la actualización a Elementor 4.2.2, tres plugins figuran como "Desconocido" — Cool FormKit Lite, Dynamic Visibility for Elementor y Elementor Pro. No es incompatibilidad confirmada, es ausencia de prueba.

## 2. Seguridad — panel de Wordfence

- Wordfence Security activo, versión gratuita (Premium desactivado, Wordfence Central sin conectar, registro de auditoría desactivado).
- Indicadores del escritorio: Cortafuegos 48%, Análisis 60%.
- **13 problemas detectados en el último escaneo — sin detalle de cuáles son** (el panel no lo transcribe). No verificable documentalmente; requiere entrar al panel para ver el listado.
- Estadísticas de bloqueo: 49 ataques/mes, 13/semana, 1/día. Esto mide intentos bloqueados por el firewall, no confirma ni descarta compromiso del sitio.
- **Imunify Security también está activo** junto con Wordfence — ambos declaran cobertura de firewall y escaneo de malware. Solapamiento parcial confirmado documentalmente; no se puede determinar si Imunify opera a nivel de hosting (uso común de CloudLinux/Imunify360, lo que reduciría la redundancia real) sin verificarlo en el panel de hosting.
- **Code Snippets Pro con licencia vencida:** la versión activa (3.6.8) no puede actualizar a 3.8.0 sin licencia. Es el plugin de mayor riesgo relativo del listado porque ejecuta código PHP arbitrario en todo el sitio — quedarse sin parches de seguridad ahí pesa más que en un plugin de alcance acotado.
- **Verificación de vulnerabilidades (CVE) — NO REALIZADA.** Ningún componente de este listado fue contrastado contra bases públicas de vulnerabilidades ni changelogs oficiales. Pendiente de autorización expresa para usar búsqueda web.

## 3. Copias de seguridad

Dos herramientas de backup/migración instaladas — **All-in-One WP Migration and Backup** y **Duplicator Pro** — y **ninguna de las dos está activa**. La instalación de estas herramientas no acredita que exista una copia de seguridad vigente ni probada. Este es el hallazgo más importante de esta auditoría: no hay evidencia documental de qué mecanismo de respaldo está operando hoy en el sitio.

## 4. Contenido del blog — inventario y hallazgos

25 entradas (`post_type=post`) en el WXR: 20 publicadas, 1 borrador, 4 en papelera. Las 25 están en una única categoría ("Blog"); no hay subcategorización. Las etiquetas casi no se usan (solo 2 posts las tienen). 10 comentarios en total, coincide exacto con el badge "Comentarios (10)" del panel.

### Canibalización SEO confirmada (posts publicados, no borradores)

| Tema | Posts publicados en competencia |
|---|---|
| Auditoría Tributaria del SII | id 1913 (2021), id 9505 (24-10-2025), id 9019 (01-06-2026) |
| Prescripción Tributaria | id 1302 (2020 — el de mayor tráfico histórico del sitio según DOC-01), id 7745 (27-05-2025), id 8302 (16-06-2025), id 9042 (07-09-2025) |

Tres y cuatro posts publicados respectivamente compitiendo por el mismo foco temático — Google no puede decidir cuál posicionar, y el problema es más grave en "Prescripción Tributaria" porque incluye la página de mayor tráfico real del sitio.

### Bug de SEO en producción

El post id=9097 ("Cumplimiento tributario y contabilidad: evita riesgos y multas") tiene el campo `yoast_title` con el título de **otro post** (id=9075, "Variable tributaria en operaciones..."). Google probablemente muestra el título equivocado para esa URL en resultados de búsqueda. Corrección de bajo esfuerzo y alto impacto.

### Contenido duplicado sin purgar

- "OLD - ¿Conoces la Auditoría Tributaria del SII?..." (id 9452) — en papelera.
- Duplicado adicional de "Auditoría Tributaria del SII 2025 | Etapas, Plazos y Defensas" (id 9668) — en papelera.
- "PRUEBA: ¿Conoces la Auditoría Tributaria del SII?..." (id 9383) — **sigue como borrador activo**, no en papelera.

## 5. Arquitectura de contenido (custom post types)

`servicio-tributario` (12), `page` (20), `elementor_library` (111 — plantillas/componentes de Elementor), `attachment` (476 — medios), `jet-engine` (9), `elementor_snippet` (9), `equipo-ddcon` (8), `caso-de-exito` (8), `agendas` (7), `servicio` (6). Cada tipo cumple un propósito distinto y no hay solapamiento entre ellos.

## 6. Tema activo

No confirmable al 100% sin abrir Apariencia → Temas. La presencia de un menú "Hello" separado de "Aspecto" en el panel es indicio fuerte de que el tema activo es **Hello Elementor / Hello Biz** (el tema complementario de Elementor). Inferencia de confianza media.

## 7. Matriz de riesgos

| ID | Componente | Hallazgo | Severidad | Confianza | Acción recomendada |
|---|---|---|---|---|---|
| WPR-1 | Backup | Dos herramientas de respaldo instaladas, ninguna activa | Alto | Baja (falta evidencia de qué respalda hoy) | Confirmar con hosting/agencia el mecanismo real vigente antes de cualquier actualización |
| WPR-2 | Code Snippets Pro | Licencia vencida bloquea parche de seguridad 3.8.0 | Alto | Media | Renovar licencia o migrar snippets críticos |
| WPR-3 | Blog — canibalización SEO | 3 y 4 posts publicados compitiendo por el mismo tema | Alto | Alta | Consolidar contenido, redirigir 301, mantener un solo post por tema |
| WPR-4 | Elementor / Elementor Pro | Update con "cambios sustanciales" + 3 plugins con compatibilidad no probada | Medio | Alta | No actualizar en producción sin staging y respaldo verificado |
| WPR-5 | Wordfence | 13 problemas detectados sin detalle disponible documentalmente | Informativo / hipótesis por validar | Baja | Revisar el detalle directo en el panel |
| WPR-6 | Wordfence + Imunify | Doble motor de seguridad activo sin evidencia de coordinación | Medio | Media | Confirmar si Imunify es capa de hosting; evaluar desactivar uno si es redundante |
| WPR-7 | Yoast SEO | Título Yoast incorrecto en post id=9097 | Medio | Alta | Corregir el campo directamente en el editor |
| WPR-8 | Papelera / contenido de prueba | 2 duplicados en papelera + 1 borrador de prueba sin purgar | Bajo | Alta | Purgar definitivamente |

## 8. Limitaciones declaradas

- No se verificaron vulnerabilidades (CVE) contra fuentes externas — pendiente de autorización.
- No hay acceso a archivos de `wp-content` ni a la base de datos — no se puede auditar malware/backdoors más allá de lo que Wordfence ya reporta en su panel.
- El drop-in sin identificar no se pudo determinar con la información disponible.
- El nombre exacto del tema activo es una inferencia, no una confirmación directa.
- Este documento es una foto puntual del 19-08-2026; puede no reflejar el estado si hubo cambios posteriores.
