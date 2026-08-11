# Proyecto: web de Raquel (La Presentadora)

Este es un proyecto personal de Raquel (no de Coocrea/trabajo). El código vive en GitHub:
https://github.com/sonrake-spec/webLaPresentadora

Para el contenido, textos y decisiones de diseño de la web, ver `contenido-web.md` en esta
misma carpeta — es la fuente de verdad de esa parte, se actualiza a medida que se avanza.

## Estado de la gestión del hosting/dominio (a fecha de la última sesión)

- Hosting contratado en IONOS (plan Hosting Plus).
- Dominio lapresentadora.com: transferencia iniciada desde Web Artesanal (Carlos Doral) a
  IONOS, manteniendo el DNS actual sin cambios hasta que todo esté listo (así no se rompe el
  correo ni la web actual). Pendiente de que la transferencia se complete (varios días).
- Correo raquel@lapresentadora.com: sigue en el proveedor antiguo por ahora. Datos técnicos
  para migrarlo cuando toque: IMAP `imap.servidor-correo.net` puerto 993 SSL/TLS, SMTP
  `smtp.servidor-correo.net` puerto 587 STARTTLS, usuario raquel@lapresentadora.com.
  Uso actual del buzón: ~14,3 GB de 29,3 GB de cuota. Sin problema de espacio en IONOS (195 GB
  compartidos en el plan contratado).
- Siguiente paso pendiente: cuando el dominio aparezca activo en la cuenta de IONOS, crear el
  buzón de correo nuevo ahí e importar los mensajes del buzón antiguo antes de cambiar el MX.

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
