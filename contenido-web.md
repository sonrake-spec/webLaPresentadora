# Contenido y diseño de la web — La Presentadora

Notas de trabajo para el diseño y redacción de la web nueva de Raquel (lapresentadora.com).
Sigue este documento como fuente de verdad del contenido; el archivo CLAUDE.md tiene el
contexto técnico (git, hosting, dominio).

## Enfoque de diseño

- Raquel es diseñadora profesional (Art Director, especialista en presentaciones). Ella dirige
  el criterio de diseño; Claude ejecuta en código con precisión, iterando sobre su feedback.
- No usar Claude Design (es para presentaciones/PowerPoint, no para webs) ni ChatGPT. Todo el
  código de la web se escribe directamente en esta conversación/repositorio.
- Partir de la identidad de marca ya existente si se puede (paleta turquesa/verde azulado +
  rosa/magenta, con ilustraciones, visible en linkedin.com/in/raquelgarcíacarrillo y en la web
  actual). Pendiente: pedir a Raquel manual de marca o códigos de color exactos si los tiene.
- Web estática (HTML/CSS, sin base de datos, sin formulario de contacto) — encaja con hosting
  básico y con que las actualizaciones sean sencillas (Claude las hace vía git).

## Mapa de la web

1. **Inicio** — presentación + selección de trabajos destacados.
2. **Trabajos / Portfolio** — grid de fichas (no slider). Cada ficha es un vídeo corto en bucle
   (5-8s, sin sonido, se reproduce solo al entrar en pantalla al hacer scroll) con título y
   entradilla superpuestos. Opcional a futuro: popup/lightbox al hacer clic con más detalle
   (cliente, reto, resultado). Un grid (no slider) para que todo el contenido sea visible e
   indexable por Google.
3. **Sobre mí** — bio de Raquel (texto ya redactado, ver abajo).
4. **Publicaciones** — reescritura para web de los "PowerTrucos" que Raquel publica en LinkedIn
   (posts cortos y prácticos sobre PowerPoint/diseño). Refuerza SEO/GEO reutilizando contenido
   que ya funciona bien ahí.
5. **Contacto** — sin formulario, solo email/teléfono.

Mantenimiento del portfolio: para añadir un trabajo nuevo, Raquel solo tiene que pasar el vídeo
y el texto (título + entradilla) a Claude, que añade la ficha y hace commit/push. No requiere
que ella toque código.

## Tono de redacción

Tono de La Presentadora en LinkedIn: cercano, directo, seguro, con algún toque de humor y
alguna pregunta retórica. Nunca guiones largos (—): usar dos puntos o punto y coma en su lugar.

## Texto "Sobre mí" (versión aprobada)

Llevo años mirando las presentaciones desde los dos lados: como agencia y como cliente. Y
aprendí algo que no se me olvida: una presentación nunca es "un PowerPoint bonito", es la
primera impresión que alguien tiene de tu empresa, tu producto o tu proyecto, y a veces tu
única bala para convencer.

Ayudo a marcas como Grünenthal, Banco Santander, Novo Nordisk, Cupra o Marqués de Riscal a
convertir sus presentaciones en piezas claras y visuales que ordenan ideas y simplifican lo
complicado. Trabajo casi siempre en PowerPoint, sin trucos raros: para que luego puedas tocar y
modificar tú misma lo que haga falta. Eso sí, con IA de por medio para ir más rápido y llegar
más lejos, nunca como atajo.

¿Tu próxima presentación tiene que convencer a alguien de algo importante? Hablemos.

## Bloques de servicios (aprobados)

**1. Creación de presentaciones**
Presentaciones visuales de alto impacto: comerciales, corporativas, para eventos, farma,
interactivas o animadas. Ordeno y simplifico contenidos complejos, y convierto datos en
gráficos que se entienden a la primera.

**2. Materiales de comunicación interna**
Diseño también los materiales que usan tus equipos por dentro: informes, manuales, documentos
de formación. Con la misma exigencia visual que una presentación de cliente.

**3. Formación en presentaciones**
Formo a equipos para que mejoren sus propias presentaciones, desde el diseño, el uso real de
PowerPoint y también la IA aplicada a presentaciones, que ahora está en boca de todos. Nada de
teoría abstracta: trucos que se aplican al día siguiente.

## Material de referencia disponible

- Web actual: lapresentadora.com (WordPress/Divi, contenido desde ~2020, poco texto/SEO).
- LinkedIn de Raquel: linkedin.com/in/raquelgarcíacarrillo — 533 seguidores, activa con la
  serie "PowerTruco". Buena fuente de contenido para reutilizar en Publicaciones.
- Clientes mencionables: Grünenthal, Banco Santander, Novo Nordisk, Cupra, Marqués de Riscal.

## Pendiente / siguiente paso

- Definir el resto de secciones con Raquel (Trabajos, Publicaciones, Contacto) igual que se
  hizo con Sobre mí y los bloques de servicios.
- Bocetar visualmente la home cuando haya contenido suficiente.
- Confirmar paleta de color / tipografías de marca con Raquel.
