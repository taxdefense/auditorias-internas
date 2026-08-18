# Prompt de ejecución — Ajuste CAE + 3 entregables Meta Ads

**Fecha:** 18-08-2026 · **Repositorio:** `taxdefense/auditorias-internas` · **Base:** [`auditoria-cuenta-meta-ads.md`](auditoria-cuenta-meta-ads.md) (Auditoría 1 de Meta, 17-08-2026)

---

## Contexto

La Auditoría 1 de Meta Ads (17-08-2026) recomendaba como acción de **impacto alto** reactivar las 3 campañas CAE pausadas (Estrategia Centralizada, Prescripción, Defensa), por ser 2-3x más eficientes en costo por conversación que la única campaña activa ("Diagnósticos Gratuitos").

Víctor marcó esa recomendación: **las campañas CAE ya no pueden correr tal como están, porque su oferta/creativo quedó desactualizado** (las condiciones de la deuda CAE que citan esos anuncios corresponden a abril de 2026 y antes; a agosto de 2026 ese contenido ya no es preciso). Verificado además contra la cuenta real vía Meta MCP: las 3 campañas siguen en `PAUSED`/`delivery: off`, sin errores de entrega ni rechazo de Meta — es decir, no es un bloqueo técnico de la plataforma, es una decisión de negocio: el contenido no está vigente.

**Regla de ajuste (aplica a todo lo que sigue):** la campaña CAE **no se elimina** del historial ni del banco de aprendizaje — sigue siendo el mejor dato de eficiencia probado de la cuenta y el ángulo con mejor costo por conversación. Pero **se descuenta como palanca de alcance inmediato**: no cuenta como "mejora" ni "activación de servicio" disponible hoy. Solo vuelve a ser una acción ejecutable cuando el Cliente-Estudio actualice oferta y creativos a las condiciones CAE vigentes — momento en que pasa a ser campaña nueva, no reactivación. Todo el resto de los hallazgos de la Auditoría 1 (tracking, frescura creativa, medición, audiencias, landing) se mantiene sin cambios.

## Rol

Actuar como consultor senior de Meta Ads + estratega editorial de marca del Estudio (sistema `estilo-defensor`), para producir 3 entregables encadenados: informe/planificación operativa → investigación de políticas y algoritmo → guiones y configuración de campaña.

## Tarea (3 puntos, en orden, cada uno depende del anterior)

1. **Reporte ajustado + backlog ClickUp.** Descontar el alcance CAE del informe. Entregar registro de cambios y lista de tareas planificable en ClickUp, con responsable individualizado por tarea: **Agencia-prestador** (ejecución técnica: Ads Manager, GTM, Pixel, creativos) vs. **Cliente-Estudio** (decisiones de negocio, oferta, compliance, aprobación de contenido). Basado **exclusivamente** en la Auditoría 1 de Meta — sin incorporar hallazgos de los puntos 2 o 3.
2. **Investigación profunda — políticas y algoritmo Meta 2026.** Cambios recientes al Pixel/Conversions API, contenido generado con IA vs. sin IA, video de personas reales vs. video editado, formatos sugeridos, funcionamiento del algoritmo de entrega, configuraciones de cuenta/campaña — todo lo no cubierto en la Auditoría 1. Cierra con puntos fuertes y débiles de DDC frente a esas políticas, antes de generar contenido nuevo.
3. **Guiones + configuración de anuncios.** Con base en lo que sugiere el algoritmo, los datos del Ads Manager (Auditoría 1) y los hallazgos de alcance de la investigación 2 — usando el sistema `estilo-defensor` sin contradecir lo levantado en 1 y 2 — crear 3 variantes de reel por cada uno de 7 temas (Prescripción Tributaria, Cobranza Fiscal, Convenios y Condonaciones con TGR, Eliminación de antiguas deudas fiscales, Fiscalización del SII, Defensa por cobro de impuestos, Embargos de la Tesorería). Añadir configuración completa de anuncio por tema (objetivo, formato, ubicaciones, público, presupuesto sugerido), descripciones de formulario/landing, y CTA de conversión óptimo según el contenido general de defensordelcontribuyente.cl.

## Especificaciones

- Fuente de verdad de datos de cuenta: Meta Ads MCP (cuenta 949295082543787) — consultar en vivo, no asumir desde el HTML/MD si hay discrepancia con la cuenta real.
- Punto 1 no debe citar ni apoyarse en investigación externa — solo Auditoría 1.
- Punto 2 debe citar fuentes oficiales de Meta (Meta Business Help Center, Meta for Business, Ads Manager) y buenas prácticas de Meta Business Partners/comunidad, con fecha de consulta.
- Punto 3 no puede violar ninguna regla de voz/formato de `estilo-defensor` (fórmula STOP, vocabulario prohibido, técnicas de humor, 6 formatos canónicos) ni contradecir los hallazgos de fuerzas/debilidades del punto 2.
- Todos los cambios se suben al repositorio `taxdefense/auditorias-internas` (commit + push).
- Cada uno de los 3 puntos se entrega además como Word editable (`.docx`) en `descargables/`.

## Criterios de calidad

- Accionable en el ecosistema chileno (SII, TGR, portal del contribuyente) y ejecutable por un estudio boutique con recursos acotados.
- Tareas de ClickUp con responsable único por tarea (no "compartido").
- Investigación 2 con hallazgos verificables, no genéricos ("usa más video" no vale sin el porqué ligado a datos de la cuenta o política citada).
- Guiones de punto 3 publicables tal cual, sin relleno corporativo, con marcación de pantalla para reels.
- Coherencia total entre los 3 puntos: nada del punto 3 puede pedir un formato o config que el punto 2 identificó como débil o no recomendado.

## Formato de respuesta

- 3 archivos Markdown en el repo (uno por punto) + actualización de los archivos base de la Auditoría 1 (`.md` y `.html`) reflejando el ajuste CAE.
- 3 archivos Word editables en `descargables/`, con identidad visual DDC (Nunito Sans, naranja/turquesa/azul).
- 1 commit (o serie de commits) con push a `main`.
- Resumen ejecutivo en el chat al cerrar cada punto, sin repetir el detalle que ya está en el Word.
