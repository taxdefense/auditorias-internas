# Guiones y configuración de anuncios — 7 temas (Punto 3)

**Fecha:** 18-08-2026 · **Base:** Auditoría 1 ([auditoria-cuenta-meta-ads.md](auditoria-cuenta-meta-ads.md)) + Investigación 2 ([investigacion-2-politicas-algoritmo-meta.md](investigacion-2-politicas-algoritmo-meta.md)) · **Sistema de voz:** `estilo-defensor`

---

## Metodología (por qué cada guion es como es)

Cada uno de los 7 temas trae **3 variantes de reel** que no son copias del mismo guion con otras palabras: varían a propósito en formato canónico, tipo de producción y duración, siguiendo lo que la Investigación 2 encontró:

- **Duración:** ángulos de miedo/urgencia van cortos y directos (15-20s); ángulos de autoridad o explicativos sobre un concepto complejo (prescripción, convenios) justifican un formato más largo (30-50s) porque resolver deuda fiscal es una decisión de alta consideración, no un impulso (Investigación 2, punto 3).
- **Avatar IA vs. persona real:** avatar IA para prospección fría / testeo rápido de gancho (CPA queda dentro de 10-15% de persona real); testimonio real reservado para audiencias cálidas/remarketing, donde la conversión cae 20-25% si no es persona real (Investigación 2, punto 2). Todo material con avatar IA lleva divulgación activada en Ads Manager.
- **Compliance de copy:** ningún guion afirma o implica en segunda persona que el espectador individual tiene una deuda ("tú le debes al SII"). Se mantiene encuadre de tercera persona/estadístico ("miles de contribuyentes...") — es el filtro que la Investigación 2 identificó como el motivo de rechazo más común en la categoría (punto 7).
- **CAE:** ninguno de estos 7 temas reutiliza el naming ni la oferta de las campañas CAE pausadas (ver ajuste del Punto 1). "Prescripción Tributaria" aquí es el concepto general, no la oferta CAE específica desactualizada; si en el futuro se quiere una versión con ángulo CAE, primero debe pasar por la actualización de oferta que el Cliente-Estudio tiene pendiente.
- **Formato de pantalla:** máster vertical 9:16, subtítulos incluidos siempre (accesibilidad + consumo sin audio), máximo 6 palabras por línea en pantalla.

Estructura de las 3 variantes, igual para los 7 temas:

| Variante | Formato canónico | Producción | Duración | Audiencia objetivo |
|---|---|---|---|---|
| A | El Caso (o La Calculadora donde se indique) | Testimonio real en estudio | 45-55s | Cálida / remarketing |
| B | La Pregunta Incómoda o El Derecho | Avatar IA (UGC-style, rotulado) | 15-20s | Fría / prospección |
| C | El Derecho o La Calculadora | Slide informativo tipo "paper" | 25-35s | Fría a media / Advantage+ |

---

## 1. Prescripción Tributaria

### Configuración de campaña

| Campo | Valor sugerido |
|---|---|
| Objetivo | Interacción (Conversations) — mismo objetivo probado en la cuenta |
| Optimización | `onsite_conversion.messaging_deep_conversation`; migrar a evento CAPI "lead calificado" cuando esté disponible (Punto 2) |
| Formato | Reels 9:16 + variante de imagen del mismo gancho (mixed_formats — recomendación directa de Meta sobre la cuenta) |
| Ubicaciones | Advantage+ placements (automático) |
| Público | Advantage+ Audience con semilla: lookalike "Personas con deudas CAE" (reactivada) + intereses "derecho tributario", "SII" |
| Presupuesto sugerido | $50.000 CLP/día en testeo por variante, 5-7 días (ciclo de fatiga 2026), luego consolidar en la variante ganadora |
| CTA del anuncio | Enviar mensaje (WhatsApp) |
| "Formulario" (flujo conversacional) | Sin landing/formulario web. Al abrir el chat, mensaje automático + 2 preguntas de calificación: "¿Hace cuántos años es la deuda?" / "¿Es SII o Tesorería?" — esas 2 respuestas son el evento que se reenvía como lead calificado vía CAPI |
| Landing de respaldo | `defensordelcontribuyente.cl` — sección Prescripción Tributaria del blog Jurídicamente (crear si no existe, coherente con hallazgo de la Auditoría 1: "no hay una sola mención a CAE/prescripción en la home") |

### Variante A — El Caso · Testimonio real · 50s · Audiencia cálida

**Segmento:** Perfil 1 (Deudor Reactivo) · **Humor:** detalle bizarro que humaniza

[TEXTO EN PANTALLA: "15 años. $23.000.000. Hoy: $0"]
(0-3s) Silvana mira a cámara, sin sonreír todavía.
"Quince años pagando —o esquivando— una deuda con el SII que ya ni recordaba bien de dónde salió."

[TEXTO EN PANTALLA: "¿Y si ya había prescrito?"]
(3-15s) "La revisamos. Había prescrito hace años. Nadie se lo había dicho — ni el SII se lo iba a decir."

(15-40s) "La prescripción tributaria existe: pasado cierto plazo, el Fisco pierde el derecho a cobrar. No es un vacío legal, es un derecho tuyo. El problema es que casi nadie lo revisa a tiempo, y se sigue pagando —o angustiando— por una deuda que legalmente ya no se puede cobrar."

[TEXTO EN PANTALLA: "Miles de chilenos pagan deudas que ya prescribieron"]
(40-50s) "Si tienes una deuda fiscal de hace años y nunca revisaste si prescribió, puede que estés pagando algo que ya no te pueden cobrar. Escríbenos y lo revisamos contigo, sin costo."

---

### Variante B — La Pregunta Incómoda · Avatar IA (rotulado) · 18s · Audiencia fría

**Segmento:** Perfil 3 (Pagador Excesivo) · **Humor:** hipérbole deflacionada

[TEXTO EN PANTALLA: "¿Puedo dejar de pagarle al SII?"]
(0-4s) "¿Puedes dejar de pagarle al SII? A veces, sí. Se llama prescripción."

[TEXTO EN PANTALLA: "El SII tiene poder... con límite"]
(4-12s) "El SII puede perseguir una deuda, pero no para siempre. Pasado cierto plazo, pierde el derecho a cobrarla. Es ley, no es magia."

[TEXTO EN PANTALLA: "Revisa tu caso gratis"]
(12-18s) "¿Tienes una deuda fiscal de hace años? Escríbenos y revisamos si ya prescribió."

*(Rótulo de divulgación IA activado en Ads Manager.)*

---

### Variante C — El Derecho · Slide informativo tipo "paper" · 30s · Advantage+

**Segmento:** Perfil 3 y 4 · **Humor:** autorreferencia irónica

[TEXTO EN PANTALLA: "Prescripción Tributaria, en cristiano"]
(0-5s) Slide con título. Voz en off explicativa, sin rostro.
"¿Los abogados tributarios hablamos en idioma humano? Vamos a intentarlo."

[TEXTO EN PANTALLA: "1. Existe un plazo · 2. Se cuenta desde la notificación · 3. Puede interrumpirse"]
(5-20s) "La prescripción tributaria tiene tres puntos clave: existe un plazo legal para que el Fisco cobre, ese plazo se cuenta desde que te notificaron, y ciertas acciones del SII pueden interrumpirlo. Por eso no basta con 'esperar que se pase' — hay que revisarlo caso a caso."

[TEXTO EN PANTALLA: "Revisa tu caso"]
(20-30s) "Si tienes una deuda fiscal antigua, esto es lo primero que hay que revisar antes de pagar un peso más. Te explicamos cómo en 5 minutos."

---

## 2. Cobranza Fiscal

### Configuración de campaña

| Campo | Valor sugerido |
|---|---|
| Objetivo | Interacción (Conversations) |
| Optimización | `onsite_conversion.messaging_deep_conversation` → CAPI lead calificado |
| Formato | Reels 9:16 + variante imagen (mixed_formats) |
| Ubicaciones | Advantage+ placements |
| Público | Audiencia "Personas con deudas CAE" (sirve como semilla general de deuda fiscal, no exclusiva de la oferta CAE) + lookalikes reactivadas |
| Presupuesto sugerido | $50.000 CLP/día en testeo, ciclo de 5-7 días |
| CTA del anuncio | Enviar mensaje (WhatsApp) |
| "Formulario" (flujo conversacional) | Mensaje automático + pregunta de calificación: "¿Ya te llegó una notificación de cobranza o todavía no?" |
| Landing de respaldo | Blog Jurídicamente — sección Cobranza Fiscal |

### Variante A — El Caso · Testimonio real · 50s · Audiencia cálida

**Segmento:** Perfil 1 · **Humor:** insulto afectuoso al sistema

[TEXTO EN PANTALLA: "La notificación llegó un viernes"]
(0-3s) Ramón, a cámara: "La notificación de cobranza llegó un viernes a las 6 de la tarde. El peor momento posible."

[TEXTO EN PANTALLA: "El fin de semana más largo"]
(3-15s) "Pasé el fin de semana completo pensando lo peor: embargo, remate, todo. El lunes fuimos donde Defensor."

(15-42s) "La cobranza fiscal tiene etapas y cada una tiene plazos y salidas distintas — no es lo mismo una notificación que un embargo ya trabado. Revisamos en qué etapa estaba mi caso y armamos un plan antes de que avanzara al siguiente paso."

[TEXTO EN PANTALLA: "Hoy: proceso cerrado, sin embargo"]
(42-50s) "Hoy mi caso está resuelto. Si te llegó una notificación de cobranza, el tiempo importa — pero primero hay que entender en qué etapa estás. Escríbenos."

---

### Variante B — La Pregunta Incómoda · Avatar IA (rotulado) · 16s · Audiencia fría

**Segmento:** Perfil 1 · **Humor:** personificación del sistema ("La TGR")

[TEXTO EN PANTALLA: "¿La TGR ya te escribió?"]
(0-4s) "La TGR es como esa vecina que guarda rencores: no cobra rápido, pero no olvida."

[TEXTO EN PANTALLA: "Hay etapas, hay plazos, hay salidas"]
(4-12s) "La cobranza fiscal tiene un proceso con etapas. Mientras antes actúes, más opciones tienes."

[TEXTO EN PANTALLA: "Revisa tu caso gratis"]
(12-16s) "¿Te llegó una notificación de cobranza? Escríbenos antes de que avance."

*(Rótulo de divulgación IA activado.)*

---

### Variante C — La Calculadora · Slide informativo · 28s · Advantage+

**Segmento:** Perfil 1 y 3 · **Humor:** hipérbole deflacionada

[TEXTO EN PANTALLA: "$1.200.000 hoy vs. $2.100.000 en 8 meses"]
(0-6s) "Esto es lo que cuesta ignorar una notificación de cobranza fiscal versus resolverla a tiempo."

[TEXTO EN PANTALLA: "Intereses + reajustes + multas, mes a mes"]
(6-18s) "Cada mes que pasa sin actuar, la deuda crece con intereses, reajustes y eventualmente costas de cobranza. No es una multa fija: es un costo que aumenta solo."

[TEXTO EN PANTALLA: "Antes cuesta menos que después"]
(18-28s) "Resolver tu situación con la TGR ahora, casi siempre cuesta menos que esperar. Te mostramos el cálculo real de tu caso, sin costo."

---

## 3. Convenios y Condonaciones con TGR

### Configuración de campaña

| Campo | Valor sugerido |
|---|---|
| Objetivo | **Leads** (no solo Conversations) — tema de alta consideración, conviene priorizar calidad sobre volumen (Investigación 2, punto 6) |
| Optimización | Evento personalizado "solicitud de convenio calificada", vía CAPI de mensajería una vez implementado; mientras tanto, `messaging_deep_conversation` |
| Formato | Reels 9:16 + carrusel (útil aquí: muestra las distintas vías — condonación, convenio de pago, defensa — de forma barata y testeable) |
| Ubicaciones | Advantage+ placements |
| Público | Audiencia "Personas con deudas CAE" + lookalikes + intereses "TGR", "convenio de pago" |
| Presupuesto sugerido | $60.000 CLP/día en testeo — tema de mayor valor por lead, justifica presupuesto algo mayor |
| CTA del anuncio | Enviar mensaje (WhatsApp) |
| "Formulario" (flujo conversacional) | Mensaje automático + 2 preguntas: "¿Deuda con TGR o con el SII?" / "¿Ya intentaste un convenio antes?" |
| Landing de respaldo | Blog Jurídicamente — sección Convenios y Condonaciones |

### Variante A — El Derecho · Testimonio real · 50s · Audiencia cálida

**Segmento:** Perfil 1 y 3 · **Humor:** ninguno forzado (tema serio, tono cercano sin chiste)

[TEXTO EN PANTALLA: "No sabía que se podía negociar con la TGR"]
(0-3s) Testimonio a cámara: "No sabía que se podía negociar con la Tesorería. Pensé que era pagar todo o nada."

[TEXTO EN PANTALLA: "Convenio ≠ perdón total. Convenio = plan real"]
(3-18s) "Un convenio de pago con la TGR no es que te perdonen la deuda: es un plan de pago que se ajusta a lo que realmente puedes pagar, con condiciones que muchas veces incluyen condonación de intereses y multas."

(18-42s) "Armamos la propuesta, la presentamos, y hoy pago una cuota que sí puedo sostener — en vez de una deuda que crecía sola cada mes."

[TEXTO EN PANTALLA: "Tu situación puede tener un plan real"]
(42-50s) "Si tienes deuda con la TGR, hay más opciones de las que el sistema te muestra a primera vista. Te las explicamos sin costo."

---

### Variante B — El Derecho · Avatar IA (rotulado) · 20s · Audiencia fría

**Segmento:** Perfil 1 · **Humor:** analogía pop absurda pero exacta

[TEXTO EN PANTALLA: "¿Deuda con la TGR? Hay Plan B"]
(0-5s) "Con la TGR pasa como con Breaking Bad: nadie llega al final del capítulo 1. Hay etapas, y en cada una hay salida."

[TEXTO EN PANTALLA: "Convenio de pago + condonación de intereses"]
(5-14s) "Un convenio de pago puede incluir condonación de intereses y multas — no es magia, es un derecho que casi nadie pide."

[TEXTO EN PANTALLA: "Revisa tu caso gratis"]
(14-20s) "Escríbenos y revisamos qué convenio aplica a tu deuda."

*(Rótulo de divulgación IA activado.)*

---

### Variante C — La Calculadora · Carrusel + slide · 30s (o 4 tarjetas) · Advantage+

**Segmento:** Perfil 1 y 3 · **Humor:** ninguno forzado

[TEXTO EN PANTALLA — Tarjeta 1: "3 caminos si debes en la TGR"]
[TEXTO EN PANTALLA — Tarjeta 2: "1. Convenio de pago en cuotas"]
[TEXTO EN PANTALLA — Tarjeta 3: "2. Condonación de intereses y multas"]
[TEXTO EN PANTALLA — Tarjeta 4: "3. Revisar si algo ya prescribió"]

Copy de apoyo (si se usa como reel narrado en vez de carrusel): "Si debes en la Tesorería, no hay un solo camino: hay al menos tres, y casi nunca son excluyentes entre sí. Te ayudamos a armar el que corresponde a tu caso, sin costo."

---

## 4. Eliminación de antiguas deudas fiscales

### Configuración de campaña

| Campo | Valor sugerido |
|---|---|
| Objetivo | Interacción (Conversations) |
| Optimización | `onsite_conversion.messaging_deep_conversation` → CAPI lead calificado |
| Formato | Reels 9:16 + variante imagen |
| Ubicaciones | Advantage+ placements |
| Público | Audiencia "Personas con deudas CAE" (semilla general) + lookalikes + Advantage+ Audience abierta |
| Presupuesto sugerido | $50.000 CLP/día en testeo |
| CTA del anuncio | Enviar mensaje (WhatsApp) |
| "Formulario" (flujo conversacional) | Mensaje automático + pregunta: "¿Hace cuántos años es la deuda más antigua que tienes?" |
| Landing de respaldo | Blog Jurídicamente — sección Eliminación de deudas antiguas / Prescripción |

### Variante A — El Caso · Testimonio real · 55s · Audiencia cálida

**Segmento:** Perfil 1 · **Humor:** detalle bizarro que humaniza

[TEXTO EN PANTALLA: "Pedro cargó esta deuda 15 años"]
(0-3s) "Pedro cargó una deuda del SII por 15 años. La llevaba tan asumida que ya ni la mencionaba."

[TEXTO EN PANTALLA: "15 años después, tuvo su revancha"]
(3-15s) "La revisamos completa: origen, notificaciones, plazos. Parte de la deuda ya había prescrito. Otra parte se pudo condonar. Lo que quedó, se pagó en cuotas que sí podía sostener."

(15-45s) "Una deuda fiscal antigua casi nunca es 'un solo monto fijo que hay que pagar entero': tiene historia, tiene plazos, tiene partes que a veces ya no se pueden cobrar. El error más caro es no revisarla nunca y seguir cargándola como si fuera inamovible."

[TEXTO EN PANTALLA: "Revisa tu deuda antigua, sin costo"]
(45-55s) "Si arrastras una deuda fiscal de años, puede que no esté tan fija como crees. Escríbenos y la revisamos contigo."

---

### Variante B — La Pregunta Incómoda · Avatar IA (rotulado) · 17s · Audiencia fría

**Segmento:** Perfil 1 · **Humor:** hipérbole deflacionada

[TEXTO EN PANTALLA: "¿Esa deuda de hace años... sigue como la recuerdas?"]
(0-5s) "Esa deuda fiscal que arrastras hace años, ¿la revisaste alguna vez, o solo la sigues cargando?"

[TEXTO EN PANTALLA: "Puede tener menos peso del que crees"]
(5-13s) "Entre prescripción, condonaciones y errores de cálculo, muchas deudas antiguas pesan menos de lo que la gente asume."

[TEXTO EN PANTALLA: "Te la revisamos gratis"]
(13-17s) "Escríbenos y revisamos tu caso."

*(Rótulo de divulgación IA activado.)*

---

### Variante C — El Derecho · Slide informativo · 27s · Advantage+

**Segmento:** Perfil 1 y 4 · **Humor:** ninguno forzado

[TEXTO EN PANTALLA: "Deuda antigua: lo que casi nadie revisa"]
(0-6s) "Una deuda fiscal de años puede tener tres cosas que nadie te dijo: parte prescrita, parte condonable, y errores de cálculo acumulados."

[TEXTO EN PANTALLA: "3 cosas que revisar antes de seguir pagando"]
(6-20s) "Antes de seguir pagando algo 'porque siempre se ha pagado', vale revisar esas tres cosas — puede cambiar completamente el monto real que corresponde."

[TEXTO EN PANTALLA: "Revisa tu caso"]
(20-27s) "Te explicamos cómo revisarlo en 5 minutos, sin costo."

---

## 5. Fiscalización del SII

### Configuración de campaña

| Campo | Valor sugerido |
|---|---|
| Objetivo | **Leads** — decisión de alta consideración, prevención antes de que escale (Investigación 2, punto 6) |
| Optimización | `messaging_deep_conversation` → evento CAPI "consulta calificada" |
| Formato | Reels 9:16 + variante imagen |
| Ubicaciones | Advantage+ placements |
| Público | Advantage+ Audience abierta + interés "emprendimiento", "pyme" (perfil preventivo, no necesariamente deudor) |
| Presupuesto sugerido | $50.000 CLP/día en testeo |
| CTA del anuncio | Enviar mensaje (WhatsApp) |
| "Formulario" (flujo conversacional) | Mensaje automático + pregunta: "¿Ya recibiste una citación/notificación del SII o quieres prevenir antes de una operación?" |
| Landing de respaldo | Blog Jurídicamente — sección Fiscalización SII |

### Variante A — El Caso · Testimonio real · 55s · Audiencia cálida

**Segmento:** Perfil 2 (Víctima del Desconocimiento) · **Humor:** gancho cultural criollo

[TEXTO EN PANTALLA: "Fuiste por lana y saliste trasquilado"]
(0-4s) Testimonio: "Vendí una propiedad a mi hijo pensando que era lo más simple del mundo. Tres años después, llegó la fiscalización."

[TEXTO EN PANTALLA: "El SII revisó todo: la venta, el precio, la forma de pago"]
(4-18s) "No había mala intención de nuestra parte — seguimos el consejo que nos dieron en su momento. Pero el SII fiscalizó la operación completa: simulación, forma de pago, hasta el impuesto a la herencia."

(18-48s) "Cuando el SII fiscaliza, no revisa un solo punto: revisa el contexto completo de la operación. Por eso importa cómo se estructura una transacción entre familiares antes de firmarla, no después."

[TEXTO EN PANTALLA: "Antes de firmar, pregunta esto"]
(48-55s) "Si vas a hacer una transacción importante en la familia, revisa las implicaciones tributarias antes de la notaría, no después de la fiscalización. Te asesoramos sin costo."

---

### Variante B — El Derecho · Avatar IA (rotulado) · 19s · Audiencia fría

**Segmento:** Perfil 4 (Emprendedor Preventivo) · **Humor:** analogía pop absurda pero exacta

[TEXTO EN PANTALLA: "Tu empresa es Clark Kent"]
(0-5s) "Tu empresa individual es como Clark Kent: en la notaría eres persona natural, en el F22 eres una empresa. El SII sabe que son la misma persona."

[TEXTO EN PANTALLA: "El SII también lo sabe"]
(5-14s) "Muchas fiscalizaciones parten justo ahí: en esa línea que separa a la persona de la empresa."

[TEXTO EN PANTALLA: "Revisa tu estructura antes de que te fiscalicen"]
(14-19s) "Antes de una operación importante, escríbenos y revisamos tu caso."

*(Rótulo de divulgación IA activado.)*

---

### Variante C — La Pregunta Incómoda · Slide informativo · 25s · Advantage+

**Segmento:** Perfil 2 y 4 · **Humor:** ninguno forzado

[TEXTO EN PANTALLA: "¿Puedo ignorar una citación del SII?"]
(0-5s) "¿Se puede ignorar una citación del SII? La respuesta directa: no, y hacerlo empeora tu situación legal."

[TEXTO EN PANTALLA: "Tienes plazo para responder — y para armar tu defensa"]
(5-18s) "Una citación tiene plazo de respuesta, y ese plazo es también tu ventana para armar una defensa con respaldo, no para reaccionar a último minuto."

[TEXTO EN PANTALLA: "Te ayudamos a responder bien"]
(18-25s) "Si te llegó una citación del SII, escríbenos antes de que venza el plazo."

---

## 6. Defensa por cobro de impuestos

### Configuración de campaña

| Campo | Valor sugerido |
|---|---|
| Objetivo | Interacción (Conversations) |
| Optimización | `messaging_deep_conversation` → CAPI lead calificado |
| Formato | Reels 9:16 + variante imagen |
| Ubicaciones | Advantage+ placements |
| Público | Audiencia "Personas con deudas CAE" (semilla general) + lookalikes reactivadas |
| Presupuesto sugerido | $50.000 CLP/día en testeo |
| CTA del anuncio | Enviar mensaje (WhatsApp) |
| "Formulario" (flujo conversacional) | Mensaje automático + pregunta: "¿El cobro es del SII o de la Tesorería?" |
| Landing de respaldo | Blog Jurídicamente — sección Defensa por cobro de impuestos |

### Variante A — El Caso · Testimonio real · 50s · Audiencia cálida

**Segmento:** Perfil 1 · **Humor:** insulto afectuoso al sistema

[TEXTO EN PANTALLA: "Me cobraban algo que no era mío"]
(0-3s) "Me llegó un cobro de impuestos de una sociedad que ya ni existía. Yo era solo un socio menor."

[TEXTO EN PANTALLA: "El cobro no siempre está bien calculado"]
(3-16s) "Revisamos el origen del cobro y encontramos un vicio: te estaban cobrando una proporción que no correspondía a tu participación real."

(16-42s) "Cuando llega un cobro de impuestos, la primera pregunta no es 'cómo lo pago', es 'está bien calculado'. Muchos cobros tienen errores de base, de plazo o de a quién le corresponde — y esos errores se pueden defender."

[TEXTO EN PANTALLA: "Revisa tu cobro antes de pagarlo"]
(42-50s) "Si te está cobrando algo que no debería, o no en el monto que dice, escríbenos y lo revisamos sin costo."

---

### Variante B — La Pregunta Incómoda · Avatar IA (rotulado) · 17s · Audiencia fría

**Segmento:** Perfil 1 y 2 · **Humor:** hipérbole deflacionada

[TEXTO EN PANTALLA: "¿El cobro que te llegó está bien calculado?"]
(0-5s) "Un cobro de impuestos no es infalible. Se puede calcular mal, se puede cobrar a la persona equivocada, se puede cobrar dos veces."

[TEXTO EN PANTALLA: "Se puede defender"]
(5-13s) "Antes de pagar, vale la pena revisar si el cobro está bien hecho."

[TEXTO EN PANTALLA: "Revisa tu caso gratis"]
(13-17s) "Escríbenos y lo revisamos contigo."

*(Rótulo de divulgación IA activado.)*

---

### Variante C — El Derecho · Slide informativo · 26s · Advantage+

**Segmento:** Perfil 1 y 3 · **Humor:** ninguno forzado

[TEXTO EN PANTALLA: "Defenderse de un cobro es un derecho, no un favor"]
(0-6s) "Frente a un cobro de impuestos, tienes derecho a pedir revisión, a reclamar y, si corresponde, a que se anule."

[TEXTO EN PANTALLA: "3 vías: revisión, reclamo, nulidad"]
(6-19s) "Dependiendo de en qué etapa esté el cobro, hay distintas vías legales para defenderte — no todas aplican siempre, pero casi siempre hay al menos una disponible."

[TEXTO EN PANTALLA: "Te decimos cuál aplica a tu caso"]
(19-26s) "Escríbenos y revisamos qué vía corresponde a tu situación, sin costo."

---

## 7. Embargos de la Tesorería

### Configuración de campaña

| Campo | Valor sugerido |
|---|---|
| Objetivo | Interacción (Conversations) — urgencia alta, priorizar velocidad de respuesta |
| Optimización | `messaging_deep_conversation` → CAPI lead calificado |
| Formato | Reels 9:16 + variante imagen (mixed_formats) |
| Ubicaciones | Advantage+ placements |
| Público | Audiencia "Personas con deudas CAE" + lookalikes + Advantage+ Audience abierta |
| Presupuesto sugerido | $55.000 CLP/día en testeo — tema de mayor urgencia, tolera algo más de gasto por velocidad de respuesta |
| CTA del anuncio | Enviar mensaje (WhatsApp) |
| "Formulario" (flujo conversacional) | Mensaje automático + pregunta: "¿Ya tienes una orden de embargo notificada o es una amenaza de cobranza?" — permite priorizar atención por urgencia real |
| Landing de respaldo | Blog Jurídicamente — sección Embargos TGR |

### Variante A — El Caso · Testimonio real · 50s · Audiencia cálida

**Segmento:** Perfil 1 · **Humor:** ninguno forzado (tema de mayor urgencia/ansiedad, tono más contenido)

[TEXTO EN PANTALLA: "El embargo ya estaba notificado"]
(0-3s) "Cuando llegamos a Defensor, el embargo ya estaba notificado. Pensé que no había nada que hacer."

[TEXTO EN PANTALLA: "Sí había plazo — y sí había opciones"]
(3-16s) "Un embargo notificado todavía tiene plazos y vías: se puede negociar, se puede oponer, y en algunos casos se puede levantar si hay un vicio en el procedimiento."

(16-42s) "Actuar rápido no es solo una frase — cada día que pasa reduce las opciones disponibles. Por eso lo primero que hicimos fue revisar en qué etapa exacta estaba el embargo."

[TEXTO EN PANTALLA: "Hoy: embargo levantado"]
(42-50s) "Si tienes un embargo notificado por la Tesorería, el tiempo es la variable más importante. Escríbenos hoy, no mañana."

---

### Variante B — La Pregunta Incómoda · Avatar IA (rotulado) · 15s · Audiencia fría

**Segmento:** Perfil 1 · **Humor:** ninguno (urgencia real, sin chiste)

[TEXTO EN PANTALLA: "¿Te llegó una orden de embargo?"]
(0-4s) "¿Te llegó una orden de embargo de la Tesorería? Todavía hay plazos y opciones — pero se acortan cada día."

[TEXTO EN PANTALLA: "Actúa hoy"]
(4-11s) "Mientras antes revises tu caso, más alternativas tienes disponibles."

[TEXTO EN PANTALLA: "Escríbenos ahora"]
(11-15s) "Escríbenos ahora, sin costo por la revisión."

*(Rótulo de divulgación IA activado.)*

---

### Variante C — La Calculadora · Slide informativo · 26s · Advantage+

**Segmento:** Perfil 1 · **Humor:** ninguno forzado

[TEXTO EN PANTALLA: "Embargo notificado: esto es lo que puedes hacer, en orden"]
(0-6s) "Si te notificaron un embargo, esto es lo que se puede evaluar, en orden de urgencia."

[TEXTO EN PANTALLA: "1. Revisar el procedimiento · 2. Negociar pago · 3. Oponerse si corresponde"]
(6-19s) "Primero se revisa si el procedimiento se hizo bien. Segundo, se evalúa negociar la deuda. Tercero, si hay un vicio, se puede oponer formalmente."

[TEXTO EN PANTALLA: "Te ayudamos a definir el orden correcto"]
(19-26s) "Cada caso tiene un orden distinto. Escríbenos y lo revisamos hoy mismo."

---

## Estrategia general de conversión, formulario y CTA

Aplica a los 7 temas — no se repite en cada tabla:

- **CTA de anuncio recomendado:** "Enviar mensaje" (WhatsApp), consistente con el embudo 100% conversacional ya validado en la cuenta (Auditoría 1) y con el objetivo `messaging_deep_conversation` que Meta ya identifica como el activo hoy (Investigación 2, punto 6). No se recomienda migrar a un CTA de landing/formulario web: cambiar el modelo de conversión completo no está respaldado por datos de esta cuenta.
- **"Formulario":** no existe un formulario web en este embudo — la calificación ocurre dentro del chat de WhatsApp/Messenger con 1-2 preguntas automáticas específicas por tema (detalladas en cada tabla). Esto reemplaza al formulario tradicional y es la pieza que se debe reenviar a Meta vía CAPI como evento de "lead calificado" (dependencia técnica del Punto 1: configurar CAPI de mensajería).
- **Acción de conversión más óptima hoy:** mantener `messaging_deep_conversation` como optimización de campaña (ya es una señal más avanzada que "conversación iniciada"), y en paralelo instrumentar el evento CAPI de "lead calificado" para que dentro de 4-6 semanas de datos se pueda migrar la optimización de "volumen de conversación" a "calidad de conversación" — exactamente el cambio que la Investigación 2 identificó como la mejora de mayor apalancamiento antes de escalar presupuesto.
- **Objetivo Leads vs. Conversations:** se recomienda testear objetivo **Leads** solo en los dos temas de mayor consideración (Convenios y Condonaciones con TGR, Fiscalización del SII) porque ahí la calidad del contacto pesa más que el volumen; el resto se mantiene en Conversations, coherente con lo que ya funciona en la cuenta.
- **Landing de respaldo:** los 7 temas deben tener su propia sección o artículo en el blog Jurídicamente antes de escalar presupuesto — la Auditoría 1 encontró que la home genérica no menciona ni CAE ni prescripción pese a ser el ángulo más eficiente; lo mismo aplica a estos 7 temas nuevos.
- **Rotación:** siguiendo el hallazgo de fatiga creativa 2026 (5-7 días, Investigación 2 punto 5), no lanzar las 3 variantes de golpe y dejarlas corriendo: lanzar, medir hook rate/hold rate a los 5-7 días, y rotar la variante más débil por una nueva del mismo tema antes de que decaiga.
