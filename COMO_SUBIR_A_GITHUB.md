# Cómo subir este proyecto a GitHub (guía rápida)

Esta guía es para alguien con **poca experiencia en GitHub**. Elegí una de las dos opciones:

## Opción A — Sin usar la terminal (más simple)

1. Entrá a [github.com](https://github.com) y creá una cuenta si no tenés una.
2. Hacé clic en **"New repository"** (Nuevo repositorio).
3. Nombralo `GALAXY-046` y dejalo como público o privado, como prefieras. **No** marques "Add a README" (ya tenés uno).
4. Creá el repositorio.
5. En la página del repositorio recién creado, hacé clic en **"uploading an existing file"**.
6. Arrastrá toda la carpeta `GALAXY-046` (o su contenido) a esa página.
7. Escribí un mensaje de commit, por ejemplo: `Estructura inicial del proyecto GALAXY 046`.
8. Hacé clic en **"Commit changes"**.

## Opción B — Usando Git desde la terminal

```bash
cd GALAXY-046
git init
git add .
git commit -m "Estructura inicial del proyecto GALAXY 046"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/GALAXY-046.git
git push -u origin main
```

Reemplazá `TU-USUARIO` por tu nombre de usuario de GitHub.

## Después de subirlo

- Reemplazá los placeholders de imágenes (`media/.../*.jpg`) por tus fotos reales.
- Completá el firmware definitivo en `firmware/TX/TX.ino` y `firmware/RX/RX.ino`.
- Agregá tus mapas, diagramas y datos en las carpetas correspondientes.
- Los videos no se suben al repositorio: se enlazan desde Google Drive (ver sección correspondiente en el `README.md`).
