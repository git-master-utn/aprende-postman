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

**Colección:**
1. **⋯** sobre `Mi blog` → **More** → **Export** (o directamente **Export**).
2. Elige **Collection v2.1** → **Export**.
3. Guárdala en una carpeta nueva llamada `mi-coleccion-postman`. El archivo se llama
   algo como `Mi blog.postman_collection.json`.

**Entorno:**
1. Barra lateral → **Environments** → **⋯** sobre `Desarrollo` → **Export**.
2. Guárdalo en la misma carpeta. El archivo se llama `Desarrollo.postman_environment.json`.

> [!WARNING]
> Antes de exportar, revisa que tu entorno **no tenga tokens ni contraseñas**.
> Lo que subas a un repo público lo puede ver cualquier persona.

## 3. Súbelos a GitHub

Lo mismo que aprendiste en `aprende-github`:

1. En GitHub: **+** → **New repository** → nombre **exactamente**
   `mi-coleccion-postman`, **Public**, sin marcar nada → **Create repository**.
2. Abre Git Bash **dentro de tu carpeta `mi-coleccion-postman`** (clic derecho →
   **Open Git Bash here**) y revisa con `ls` que estén tus dos archivos `.json`.
3. Crea un README y sube todo (cambia `TU-USUARIO`):

```bash
echo "# Mi colección de Postman" > README.md
git init
git add .
git commit -m "Agrego mi colección y mi entorno de Postman"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/mi-coleccion-postman.git
git push -u origin main
```

4. Recarga tu repo en GitHub: deben aparecer `README.md` y tus dos archivos `.json`.

**Si después cambias algo** en Postman, vuelve a exportar encima de los mismos
archivos y sube los cambios:

```bash
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

## ✅ Antes de continuar

- [ ] Mi colección pasa todas sus pruebas en el Runner
- [ ] Exporté la colección y el entorno
- [ ] Mi repo `mi-coleccion-postman` es público y tiene los dos `.json`

---

[⬅️ Anterior: 07 · Pruebas](../07-pruebas/) · [🏠 Inicio](../README.md) · [Siguiente: 🏆 Reto final ➡️](../reto-final/)
