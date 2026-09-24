# Autenticación con GitHub para clonar en VSCode

Antes de poder trabajar con vuestro repositorio de práctica desde un ordenador del laboratorio (compartido con más gente), necesitáis un modo de autenticaros con GitHub que no dependa de guardar vuestra contraseña en la máquina. La forma recomendada es un **token de acceso personal (PAT) de tipo *fine-grained***, con permisos mínimos y una fecha de caducidad corta — así, aunque quede olvidado en el ordenador, deja de funcionar pasado un tiempo.

Esta guía cubre desde crear ese token hasta dejar VSCode conectado a vuestro repositorio.

## 1. Crear un nuevo token

Entra en **[github.com/settings/personal-access-tokens](https://github.com/settings/personal-access-tokens)** — es la sección de tu cuenta donde se gestionan todos los tokens de acceso personal. Si es la primera vez que entras, verás la lista vacía; pulsa **Generate new token** para empezar a crear uno.

![Página de fine-grained personal access tokens](./images/01-tokens-page.png)

## 2. Rellenar el formulario del token

En el formulario de creación:
- **Token name**: ponle un nombre que te ayude a identificarlo luego (por ejemplo, el nombre del ordenador o del laboratorio donde lo vas a usar).
- **Expiration**: elige una fecha de caducidad corta. Es la clave de que sea "temporal" — pasado ese tiempo, el token deja de servir por sí solo.
- **Repository access**: selecciona *Only select repositories* y elige únicamente el repositorio con el que vas a trabajar, en lugar de dar acceso a todos tus repos.

![Formulario del nuevo token](./images/02-form-token.png)

## 3. Dar permiso de Contents: Read and write

Baja hasta la sección **Permissions**. Por defecto el token no tiene permisos sobre el contenido del repo, así que hay que activarlo explícitamente: en **Contents**, cambia el acceso de *No access* a **Read and write**. Esto es lo que le permite tanto descargar (clonar/pull) como subir cambios (push, commits). El permiso **Metadata** viene marcado como *Read-only* y es obligatorio — no hace falta tocarlo.

Cuando lo tengas, pulsa **Generate token**.

![Permisos](./images/03-permissions.png)

## 4. Copiar el token

GitHub te enseña el token completo justo después de generarlo, con un aviso de que **no se volverá a mostrar nunca más**. Cópialo en este mismo momento con el botón de al lado; si recargas la página o navegas a otro sitio antes de guardarlo, tendrás que borrar este token y generar uno nuevo.

![Token generado](./images/04-token-generado.png)

> ⚠️ Trata el token como si fuera una contraseña: no lo pegues en chats, capturas de pantalla que vayas a compartir, ni lo subas a ningún repositorio.

## 5. Clonar el repositorio

Aquí tienes dos formas de hacerlo, según si quieres meter el token ya desde este paso o dejarlo para después:

**Opción A — clonar en plano** (sin credenciales todavía):
```bash
git clone https://github.com/usuario/nombre-repo.git
```

**Opción B — clonar con el token ya incluido** (te ahorra el paso 8 más adelante):
```bash
git clone https://TU_USUARIO:TU_TOKEN@github.com/usuario/nombre-repo.git
```

## 6. Abrir la carpeta en VSCode

Desde la terminal, ya dentro de la carpeta que se acaba de crear con el clone:
```bash
code nombre-repo
```

## 7. Configurar usuario y email — solo para esta carpeta

En la terminal integrada de VSCode, dentro del repo, configura tu identidad de Git con el flag `--local`. Esto es importante en un ordenador compartido: `--local` guarda estos datos únicamente en el `.git/config` de esta carpeta, sin tocar la configuración global del sistema ni afectar a otras personas que usen el mismo ordenador.
```bash
git config --local user.name "Usuario de GitHub"
git config --local user.email "email-github@ejemplo.com"
```
> Si no conoces tu email de GitHub, puedes verlo en **[github.com/settings/emails](https://github.com/settings/emails)** — ahí aparecen todos los correos asociados a tu cuenta, incluido el que usas para hacer commits.

## 8. Conectar el remoto con el token *(solo si no lo hiciste en el paso 5)*

Si en el paso 5 elegiste la **Opción A** (clonar en plano), ahora es cuando añades el token, reemplazando la URL del remoto `origin` por una que ya lo incluya:
```bash
git remote set-url origin https://TU_USUARIO:TU_TOKEN@github.com/usuario/nombre-repo.git
```
Si ya clonaste con la **Opción B**, este paso no hace falta — el remoto ya tiene el token desde el principio.

A partir de aquí, `git push` funciona sin pedirte usuario ni contraseña cada vez.

## Resumen de comandos

```bash
git clone https://github.com/usuario/nombre-repo.git
code nombre-repo
git config --local user.name "Usuario de GitHub"
git config --local user.email "email-github@ejemplo.com"
git remote set-url origin https://TU_USUARIO:TU_TOKEN@github.com/usuario/nombre-repo.git
```
