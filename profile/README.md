# Aprendizaje Automático (UAX) 👋

Bienvenidos a la organización de GitHub de la asignatura de **Aprendizaje Automático**. Aquí es donde vais a trabajar vuestras prácticas: entrenamiento de modelos de Deep Learning (CNN, RNN, RAG y similares), con un flujo de trabajo igual al que os vais a encontrar en cualquier equipo real de desarrollo.

## Por dónde empezar

1. Partid siempre de la plantilla del curso: **[base-github-template](https://github.com/UAX-VCMT-AA/base-github-template)**. Trae ya montada la estructura de carpetas, las tres formas de gestionar el entorno (Poetry, venv, Conda), `.gitignore`, integración continua y una guía completa en su propio README.
2. Cread vuestro repositorio de práctica a partir de esa plantilla (botón **"Use this template"** en GitHub), en vuestra propia cuenta.

## Normas del repositorio

- **Un repositorio por práctica**, creado a partir de la plantilla — no reutilicéis un mismo repo para prácticas distintas.
- **Commits con [Conventional Commits](https://www.conventionalcommits.org/es/v1.0.0/)**: `feat`, `fix`, `docs`, `chore`, `ci`, `test`... Un commit, un propósito. El detalle completo está en el README de la plantilla.
- **Nunca subáis secretos**: claves de API, tokens o contraseñas van en vuestro `.env` local, que nunca se versiona. Usad `.env.example` para documentar qué variables hace falta rellenar.
- **Nunca subáis datos ni modelos pesados** al repositorio: `data/` y `models/` están para uso local; si necesitáis compartir un modelo entrenado, subidlo al Hugging Face Model Hub (ver la guía en `app/README.md` de la plantilla).
- **README actualizado**: cada práctica debe explicar en su propio README qué hace, cómo instalarla y cómo ejecutarla.

---

¿Dudas sobre cómo montar el entorno, el `.gitignore`, la CI o cómo desplegar una demo? Todo eso está documentado en el README de la [plantilla base](https://github.com/UAX-VCMT-AA/base-github-template) — es vuestro punto de partida y de referencia durante todo el curso.
