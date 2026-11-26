<img src="../img/08.svg" width="90" align="right" alt="">

# 08 · Runner y exportar a GitHub

**Objetivo:** correr toda tu colección de un jalón y subirla a GitHub para entregarla.

## 1. Collection Runner

El **Runner** manda todas las peticiones de una colección en orden y te muestra
el resultado de todas las pruebas juntas.

1. Pasa el mouse sobre `Mi blog` → **⋯** → **Run collection** (o **Run**).
2. Revisa el orden de las peticiones; puedes arrastrarlas para cambiarlo.
3. Revisa que arriba a la derecha esté seleccionado el entorno **Desarrollo**.
4. Clic en **Run Mi blog**.
5. Verás cada petición con sus pruebas en ✅ o ❌ y un resumen al final.

> [!NOTE]
> La cuenta gratis de Postman tiene un **límite mensual de ejecuciones** del Runner.
> No lo gastes: córrelo cuando ya hayas probado cada petición por separado.
> Al final del módulo verás **Newman**, una opción sin ese límite.

## 2. Exporta tu colección y tu entorno

**Primero, 💻 crea la carpeta donde vas a guardarlos.** En Git Bash:

```bash
mkdir -p ~/Downloads/mi-coleccion-postman
```

✔️ En el Explorador de Windows, dentro de **Descargas**, ya existe la carpeta `mi-coleccion-postman`.

**🟠 Exporta la colección:**
1. En la barra lateral → **Collections** → pasa el mouse sobre `Mi blog` → **⋯**
   → **More** → **Export** (en algunas versiones sale directo **Export**).
2. Elige **Collection v2.1** → botón **Export**.
3. Se abre la ventana de Windows para guardar: entra a **Descargas** →
   **mi-coleccion-postman** → **Guardar**. No le cambies el nombre al archivo.

**🟠 Exporta el entorno:**
1. En la barra lateral → **Environments** → pasa el mouse sobre `Desarrollo` →
   **⋯** → **Export**.
2. Guárdalo en la **misma** carpeta: **Descargas** → **mi-coleccion-postman** → **Guardar**.

> [!WARNING]
> Antes de exportar, revisa que tu entorno **no tenga tokens ni contraseñas**.
> Lo que subas a un repo público lo puede ver cualquier persona.

**💻 Comprueba que están los dos:**

```bash
cd ~/Downloads/mi-coleccion-postman
ls
```

✔️ Deben salir dos archivos: `'Mi blog.postman_collection.json'` y
`Desarrollo.postman_environment.json`. Las comillas aparecen porque el nombre
tiene un espacio; es normal.

## 3. Súbelos a GitHub

Lo mismo que aprendiste en `aprende-github`:

**1. 🌐 Crea el repo:** en GitHub → **+** → **New repository** → nombre
**exactamente** `mi-coleccion-postman` → **Public** → **no marques** ninguna
casilla → **Create repository**.

**2. 💻 Sube tus archivos** (en Git Bash, dentro de `~/Downloads/mi-coleccion-postman`;
cambia `TU-USUARIO` por el tuyo):

```bash
echo "# Mi colección de Postman" > README.md
git init
git add .
git commit -m "Agrego mi colección y mi entorno de Postman"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/mi-coleccion-postman.git
git push -u origin main
```

Si te pide iniciar sesión, elige **Sign in with your browser**, entra con **tu**
cuenta y da clic en **Authorize**.

✔️ **Resultado esperado:** Git Bash termina con `main -> main`, y 🌐 en
`github.com/TU-USUARIO/mi-coleccion-postman` aparecen `README.md` y tus dos `.json`.

**Si después cambias algo en Postman:** guarda (**Ctrl + S**), vuelve a exportar
en la misma carpeta con el mismo nombre (Windows pregunta si quieres
**reemplazar** el archivo: di que **Sí**) y sube los cambios:

```bash
cd ~/Downloads/mi-coleccion-postman
git add .
git commit -m "Actualizo mi colección"
git push
```

## 4. Importar: el camino de regreso

Cualquier persona puede usar tu colección: en Postman, **Import** → arrastra el
archivo `.json`. Así se comparten las colecciones en un equipo de trabajo.

> [!TIP]
> Prueba importar la colección de un compañero desde su repo
> `mi-coleccion-postman` y córrela con tu entorno.

## 5. Extra: Newman (correr la colección desde la terminal)

**Newman** corre colecciones de Postman desde la terminal, sin abrir Postman y
sin el límite del Runner. Es lo que usan las empresas para probar sus APIs
automáticamente. Necesitas tener instalado [Node.js](https://nodejs.org).

```bash
npm install -g newman
newman run "Mi blog.postman_collection.json" -e "Desarrollo.postman_environment.json"
```

Verás en la terminal cada petición con sus pruebas y una tabla de resumen.

## ✏️ Ejercicio

1. Corre tu colección completa con el Runner; todas las pruebas deben pasar.
2. Exporta la colección (v2.1) y el entorno `Desarrollo`.
3. Crea el repo `mi-coleccion-postman` y sube los dos archivos.
4. (Opcional) Corre tu colección con Newman.

## 🔎 Evidencia para el reto final

> [!IMPORTANT]
> En tu repo **público** `mi-coleccion-postman` deben estar tu **colección
> exportada en formato v2.1** y tu **entorno** con la variable `base_url`.

> [!TIP]
> **¿Ya quedó bien?** Haz `git push` y comenta `/revisar` en tu Issue de avance.
> Si todavía no lo tienes, ábrelo aquí: [📈 Revisar mi avance](https://github.com/git-master-utn/aprende-postman/issues/new?template=revisar-avance.md&title=Revisar+mi+avance).

## ✅ Antes de continuar

- [ ] Mi colección pasa todas sus pruebas en el Runner
- [ ] Exporté la colección y el entorno
- [ ] Mi repo `mi-coleccion-postman` es público y tiene los dos `.json`

---

[⬅️ Anterior: 07 · Pruebas](../07-pruebas/) · [🏠 Inicio](../README.md) · [Siguiente: 🏆 Reto final ➡️](../reto-final/)
