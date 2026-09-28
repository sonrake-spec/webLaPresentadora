# Proyecto: web de Raquel (La Presentadora)

Este es un proyecto personal de Raquel (no de Coocrea/trabajo). El código vive en GitHub:
https://github.com/sonrake-spec/webLaPresentadora

Para el contenido, textos y decisiones de diseño de la web, ver `contenido-web.md` en esta
misma carpeta — es la fuente de verdad de esa parte, se actualiza a medida que se avanza.

## Estado de la gestión del hosting/dominio (a fecha de la última sesión)

- Hosting contratado en IONOS (plan Hosting Plus).
- Dominio lapresentadora.com: transferencia desde Web Artesanal (Carlos Doral) a IONOS
  **completada**.
- **28/9/2026: DNS cambiado por completo.** El dominio usaba servidores DNS propios del hosting
  antiguo (`ns12/ns10/ns11.servicio-online.net`) — esto significaba que el MX no se podía tocar
  solo desde IONOS, había que cambiar los servidores de nombres enteros. Se hizo así:
  1. Backup completo de la web antigua desde Plesk (archivos httpdocs comprimidos y BD
     `present_wp_2406` exportada en SQL) — descargados al navegador de Raquel antes del cambio.
  2. Subida de una web provisional "en construcción" (de `web-provisional/` en este repo:
     index.html, style.css, assets/logo.png) al espacio web de IONOS, carpeta `/public`.
  3. Conectado el dominio lapresentadora.com al espacio web de IONOS (carpeta `/public`) con la
     opción de IONOS de actualizar servidores de nombres — esto cambia TODO el DNS de golpe
     (MX de correo Y el registro A de la web) a la vez. Confirmado: "Se ha establecido la
     conexión del dominio con el espacio web."
  - Efecto: en cuanto se propague (horas), el correo entrante irá directo a IONOS y
    lapresentadora.com mostrará la web provisional en vez de la web antigua de Web Artesanal.
  - Pendiente de confirmar en los próximos días: que el correo nuevo llega a IONOS y que la web
    provisional se ve correctamente en el dominio.
- Correo raquel@lapresentadora.com: buzón nuevo **ya creado en IONOS** (plan Correo Profesional,
  50GB, dentro del contrato 300258385). El buzón antiguo (proveedor Carlos Doral) sigue intacto
  y operativo mientras tanto.
  - Datos del buzón antiguo (origen): IMAP `imap.servidor-correo.net` puerto 993 SSL/TLS, SMTP
    `smtp.servidor-correo.net` puerto 587 STARTTLS, usuario raquel@lapresentadora.com.
    Uso: ~14,3 GB de 29,3 GB de cuota.
  - **Migraciones de correo completadas dos veces, verificado**: la primera migración completa
    (11.08.2026, 9.602 correos) y una segunda de recuperación lanzada y completada el 28/9/2026
    para traer todo lo que llegó durante el verano. Confirmado el 28/9/2026: el job de migración
    marca "La solicitud de migración se ha completado" y el buzón de IONOS pasó de 4.145 a 4.370
    mensajes, con correos ya de hoy mismo — la migración trajo todo lo pendiente de agosto/
    septiembre.
- **Importante**: mientras el MX de lapresentadora.com siga sin cambiar (ver más abajo), el
  correo nuevo que llega a diario sigue entrando en el buzón antiguo, no en el de IONOS. El
  buzón de IONOS solo tiene lo que se le copia con estas migraciones — no es aún el buzón "en
  vivo". Por eso hace falta repetir la migración (o la "Migración-Delta") de vez en cuando hasta
  que se dé el paso de cambiar el MX.
- **Ojo con cambiar la contraseña del buzón de IONOS**: si se cambia, cualquier migración que
  esté en curso o la "Migración-Delta" fallará con "autenticación fallida" (ya pasó una vez,
  0 correos migrados aunque parecía haber ido bien). Tras cambiar la contraseña, hay que lanzar
  una migración nueva completa (no delta) desde cero, introduciendo la contraseña nueva a mano.
- Siguiente paso pendiente (DNS ya cambiado el 28/9/2026, backup hecho, web provisional subida):
  1. **Vigilar la propagación** (próximos días): confirmar que el correo nuevo entra en el
     webmail de IONOS y que lapresentadora.com muestra ya la web provisional (no la antigua).
  2. Confirmar la baja a Carlos Doral una vez verificado lo anterior (plan hablado: confirmar
     baja hacia el viernes de esta semana o principios de la que viene). Pendiente su respuesta
     sobre si factura el mes completo de octubre o lo prorratea.
  3. Cuando haya contenido definitivo, sustituir la web provisional por la web real (ver
     `contenido-web.md` para el estado del contenido).

## Flujo de trabajo en cada sesión

Al **empezar** a trabajar:
1. `git pull` — traer los últimos cambios antes de tocar nada.

Al **terminar** de trabajar:
1. `git add -A`
2. `git commit -m "mensaje breve de lo hecho"`
3. `git push`

Claude debe encargarse de estos comandos automáticamente en cada sesión; Raquel no necesita saber git.

## Si se retoma desde OTRO ordenador nuevo

Este ordenador tiene una "deploy key" SSH propia (en `.git-keys/`, no se sube al repositorio)
que le da permiso para hacer push. Un ordenador distinto no tiene esa clave, así que hay que:

1. Conectar una carpeta local en ese ordenador (fuera de cualquier carpeta OneDrive).
2. Clonar el repo: `git clone git@github.com:sonrake-spec/webLaPresentadora.git` — esto pedirá
   clave, así que primero hay que generar una clave SSH nueva en ese ordenador
   (`ssh-keygen -t ed25519 -f .git-keys/deploy_key -N "" -C "deploy-key"`) y añadirla en
   GitHub → repo → Settings → Deploy keys → Add deploy key (con "Allow write access").
3. Configurar `git config core.sshCommand "ssh -i <ruta>/.git-keys/deploy_key -o IdentitiesOnly=yes"`.
4. A partir de ahí, seguir el flujo normal (pull al empezar, commit/push al terminar).

## Notas importantes

- No usar una carpeta sincronizada por OneDrive/Dropbox para este repositorio: da problemas de
  bloqueos con los archivos internos de git. El código vive solo en local + GitHub.
- Cuenta de GitHub: `sonrake-spec` (creada con el Google de Raquel, sonrake@gmail.com).
- Para notas de diseño/contenido de la web (no código), se puede usar un Proyecto de Claude
  aparte, ligado a la cuenta y sincronizado automáticamente entre ordenadores.
