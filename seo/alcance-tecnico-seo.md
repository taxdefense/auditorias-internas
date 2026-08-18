# Alcance Técnico — SEO

**Sitio:** defensordelcontribuyente.cl
**Fecha:** 17 de agosto de 2026
**Preparado para:** equipo de marketing entrante

## Resumen del alcance

Este documento detalla las modificaciones técnicas de SEO que deben ejecutarse sobre defensordelcontribuyente.cl, ordenadas por prioridad. Corresponde a la línea base de trabajo previa a la toma de la cuenta.

## Prioridad 1 — Medición y tracking (crítico)

El sitio carga actualmente dos contenedores de Google Tag Manager en simultáneo, además de un tag de Google Ads fuera de ambos. Antes de cualquier optimización de contenido, se requiere:

- Consolidar la implementación de Google Tag Manager en un único contenedor.
- Migrar el tag de conversión de Google Ads (ID de conversión AW-593050363) dentro del contenedor consolidado.
- Verificar en el Asistente de Etiquetas de Google que no se disparen eventos duplicados en ninguna página.
- Documentar el contenedor GTM vigente y entregar acceso de administrador al equipo interno.

## Prioridad 2 — Rendimiento

- Combinar y minificar las hojas de estilo CSS de Elementor (actualmente se cargan 50 archivos por separado en la home).
- Revisar y activar la opción de combinación de CSS en WP Rocket, o ajustar el "print method" de Elementor si la fragmentación viene de ahí.
- Validar el resultado con PageSpeed Insights / Core Web Vitals después del cambio.

## Prioridad 3 — Accesibilidad e imágenes

- Completar el atributo `alt` en todas las imágenes de contenido (fotografías, ilustraciones) que actualmente lo tienen vacío. No modificar el `alt` vacío de imágenes puramente decorativas (curvas, iconos de fondo).
- Ampliar la cobertura de `loading="lazy"` a las imágenes fuera del primer scroll.

## Prioridad 4 — Actualización de plataforma

- Actualizar WordPress a la versión estable más reciente (previo respaldo completo y prueba en entorno de staging).
- Actualizar Elementor y Elementor Pro a la versión más reciente.
- Confirmar compatibilidad de plugins activos antes de cada actualización.

## Prioridad 5 — Datos estructurados y metadatos

- Implementar schema `LocalBusiness` para el negocio.
- Implementar schema `Service` en cada una de las 6 páginas de servicio.
- Ajustar la imagen Open Graph a proporción 1.91:1 (1200×630) en lugar de la imagen cuadrada actual.
- Completar las etiquetas `twitter:title`, `twitter:description` y `twitter:image`.
- Ampliar la meta description a 150–160 caracteres.

## Prioridad 6 — Otros ajustes

- Apuntar los enlaces del menú directamente a la URL canónica de `/servicios/` y `/blog/` para evitar el salto por redirección 301.
- Agregar la cabecera `Strict-Transport-Security`.
- Resolver la respuesta 404 de `/favicon.ico` en la raíz del dominio.

## Criterios de aceptación

| Punto | Cómo se valida |
|---|---|
| Tracking consolidado | Un solo contenedor GTM visible en el código fuente; sin eventos duplicados en el Asistente de Etiquetas |
| CSS combinado | Menos de 10 peticiones de hojas de estilo en la home |
| Imágenes con alt | 100% de imágenes de contenido con alt descriptivo |
| Plataforma actualizada | Versión de WordPress y Elementor al día, confirmable en el panel de administración |
| Schema implementado | Validación sin errores en el Rich Results Test de Google |
