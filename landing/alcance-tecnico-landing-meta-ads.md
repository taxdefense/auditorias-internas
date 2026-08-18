# Alcance Técnico — Landing Page y Meta Ads

**Sitio:** defensordelcontribuyente.cl
**Fecha:** 17 de agosto de 2026
**Preparado para:** equipo de marketing entrante

## Resumen del alcance

Este documento detalla las modificaciones requeridas en la landing page y la puesta a punto necesaria antes de operar campañas en Meta Ads, ordenadas por prioridad.

## Prioridad 1 — Tracking y medición (crítico, bloqueante para pautar)

- Instalar el Meta Pixel en la totalidad del sitio.
- Configurar el evento `Lead` para que se dispare al enviar el formulario de consulta (y, si existe, el formulario de contacto por WhatsApp).
- Resolver la duplicidad de Google Tag Manager (ver Alcance Técnico — SEO, Prioridad 1) — afecta también la medición de campañas.
- Confirmar el estado actual de la cuenta de Meta Business Manager: campañas activas, históricas, y auditorías previas si existieran.

## Prioridad 2 — Optimización de conversión (CRO)

- Diseñar y probar una versión simplificada del formulario (nombre + teléfono) específica para tráfico frío proveniente de Meta.
- Variar el texto del CTA entre las distintas secciones de la página en lugar de repetir el mismo texto.
- Reforzar la propuesta de valor específica (deuda con el SII/Tesorería) desde el primer bloque visible de la página.

## Prioridad 3 — Prueba social

- Incorporar prueba social numérica (casos resueltos, años de operación) en la home, complementando los testimonios en video ya existentes.

## Prioridad 4 — Campañas

- Publicar el set de anuncios del Anexo A (5 variantes con ángulos distintos) como primera tanda de testing.
- Reportar estructura de campañas, presupuesto y resultados de forma quincenal: CTR, CPC, ROAS y costo por lead, segmentado por campaña.

## Anexo A — Anuncios listos para publicar

### 1. Ángulo resultado / testimonio
- **Hook:** "Eduardo pensó que el SII le iba a quitar la empresa. Hoy sigue funcionando."
- **Copy:** "Cuando la deuda con el SII empieza a crecer, el miedo no te deja pensar con claridad. Eduardo pasó por eso — y encontró una salida. Mira su historia y agenda tu diagnóstico gratuito."
- **CTA:** Agendar diagnóstico gratuito
- **Formato:** Video (testimonio existente, recortado a 30–45s)

### 2. Ángulo problema / urgencia
- **Hook:** "Si te llegó una notificación del SII y la estás dejando pasar, cada día que espera cuesta más caro."
- **Copy:** "Una fiscalización o una deuda tributaria no se resuelve sola — y mientras más tiempo pasa, más intereses y multas se acumulan. Habla hoy con un equipo especializado en defensa del contribuyente."
- **CTA:** Quiero mi diagnóstico gratuito
- **Formato:** Imagen o carrusel

### 3. Ángulo prueba social
- **Hook:** "[completar con el número real] pymes ya resolvieron su deuda con el SII con nosotros."
- **Copy:** "No estás solo enfrentando esto. Emprendedores de todo Chile han recuperado su tranquilidad financiera con Defensor del Contribuyente. Conoce cómo podemos ayudarte."
- **CTA:** Ver cómo podemos ayudarte
- **Formato:** Carrusel con 3–4 testimonios en video existentes
- **Uso sugerido:** Retargeting de visitantes del sitio

### 4. Ángulo curiosidad
- **Hook:** "La mayoría de las pymes no sabe que existe la prescripción tributaria. Puede que tu deuda ya no sea exigible."
- **Copy:** "Muchos contribuyentes pagan deudas que legalmente ya prescribieron, solo por desconocimiento. Revisa tu caso gratis con un abogado tributario."
- **CTA:** Revisar mi caso
- **Formato:** Imagen simple, texto grande

### 5. Ángulo contraste (antes/después)
- **Hook:** "Antes: llamadas de Tesorería todos los meses. Ahora: un plan de pago que sí puede cumplir."
- **Copy:** "Convenios y condonaciones bien negociados cambian por completo la relación de una pyme con su deuda fiscal. Conversemos sobre tu situación, sin costo."
- **CTA:** Conversar por WhatsApp
- **Formato:** Imagen — destino WhatsApp, no el formulario largo

## Criterios de aceptación

| Punto | Cómo se valida |
|---|---|
| Meta Pixel activo | Evento visible en el Administrador de Eventos de Meta al probar el formulario |
| Formulario corto probado | Reporte de test A/B con al menos 2 semanas de datos |
| Prueba social numérica | Visible en la home sin necesidad de scroll adicional |
| Reporte de campañas | Entrega quincenal con las métricas indicadas |
