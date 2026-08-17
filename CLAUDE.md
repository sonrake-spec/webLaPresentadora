# Proyecto: web de Raquel (La Presentadora)

Este es un proyecto personal de Raquel (no de Coocrea/trabajo). El código vive en GitHub:
https://github.com/sonrake-spec/webLaPresentadora

Para el contenido, textos y decisiones de diseño de la web, ver `contenido-web.md` en esta
misma carpeta — es la fuente de verdad de esa parte, se actualiza a medida que se avanza.

## Estado de la gestión del hosting/dominio (a fecha de la última sesión)

- Hosting contratado en IONOS (plan Hosting Plus).
- Dominio lapresentadora.com: transferencia desde Web Artesanal (Carlos Doral) a IONOS
  **completada**. DNS sin cambios todavía (sigue apuntando igual, no se ha tocado el MX), así
  que el correo y la web antiguos siguen funcionando con normalidad.
- Correo raquel@lapresentadora.com: buzón nuevo **ya creado en IONOS** (plan Correo Profesional,
  50GB, dentro del contrato 300258385). El buzón antiguo (proveedor Carlos Doral) sigue intacto
  y operativo mientras tanto.
  - Datos del buzón antiguo (origen): IMAP `imap.servidor-correo.net` puerto 993 SSL/TLS, SMTP
    `smtp.servidor-correo.net` puerto 587 STARTTLS, usuario raquel@lapresentadora.com.
    Uso: ~14,3 GB de 29,3 GB de cuota.
  - **Migración de correo en curso** (lanzada vía la herramienta de migración de IONOS/audriga):
    copia todos los mensajes del buzón antiguo al nuevo sin borrar nada del origen. Se ejecuta
    en segundo plano; IONOS avisa por email (a sonrake@gmail.com) cuando termina. Se puede
    consultar el estado desde IONOS → Correo → Portafolio de correo electrónico →
    lapresentadora.com → "Migrar los correos electrónicos a IONOS".
- **Importante**: mientras el MX de lapresentadora.com siga sin cambiar (ver más abajo), el
  correo nuevo que llega a diario sigue entrando en el buzón antiguo, no en el de IONOS. El
  buzón de IONOS solo tiene lo que se le copia con estas migraciones — no es aún el buzón "en
  vivo". Por eso hace falta repetir la migración (o la "Migración-Delta") de vez en cuando hasta
  que se dé el paso de cambiar el MX.
- **Ojo con cambiar la contraseña del buzón de IONOS**: si se cambia, cualquier migración que
  esté en curso o la "Migración-Delta" fallará con "autenticación fallida" (ya pasó una vez,
  0 correos migrados aunque parecía haber ido bien). Tras cambiar la contraseña, hay que lanzar
  una migración nueva completa (no delta) desde cero, introduciendo la contraseña nueva a mano.
- Siguiente paso pendiente (cuando la migración termine y se confirme que todo llegó bien):
  1. Vincular el dominio al espacio web de IONOS (tarea aparte, para la web nueva).
  2. Cambiar el MX de lapresentadora.com para que el correo nuevo entrante vaya a IONOS (esto
     es lo que hace que el buzón nuevo quede "activo" de verdad, sin más migraciones manuales).
  3. Avisar a Carlos Doral para cancelar el servicio antiguo antes de fin de septiembre (evitar
     el borrado irrecuperable de octubre).

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
