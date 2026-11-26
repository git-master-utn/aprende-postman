# 📋 Cheatsheet de Postman

Todo lo del curso en una sola página.

## Métodos HTTP

| Método | Para qué | Lleva body | Responde |
|:-:|---|:-:|:-:|
| `GET` | Leer | No | `200` |
| `POST` | Crear | Sí | `201` |
| `PUT` | Reemplazar completo | Sí | `200` |
| `PATCH` | Cambiar una parte | Sí | `200` |
| `DELETE` | Borrar | No | `200` o `204` |

## Códigos de estado

| Código | Significa |
|:-:|---|
| `200` OK | Todo bien |
| `201` Created | Se creó algo |
| `204` No Content | Bien, sin nada que regresar |
| `400` Bad Request | La petición está mal hecha |
| `401` Unauthorized | Falta iniciar sesión o un token |
| `403` Forbidden | No tienes permiso |
| `404` Not Found | No existe |
| `500` Internal Server Error | Falló el servidor |

## API de práctica (JSONPlaceholder)

| Petición | Qué hace |
|---|---|
| `GET {{base_url}}/posts` | Lista de publicaciones |
| `GET {{base_url}}/posts/1` | Una publicación |
| `GET {{base_url}}/posts?userId=1` | Publicaciones del usuario 1 |
| `GET {{base_url}}/posts/1/comments` | Comentarios de una publicación |
| `POST {{base_url}}/posts` | Crear (simulado) → `201` |
| `PUT {{base_url}}/posts/1` | Reemplazar (simulado) |
| `PATCH {{base_url}}/posts/1` | Cambiar una parte (simulado) |
| `DELETE {{base_url}}/posts/1` | Borrar (simulado) |

`base_url` = `https://jsonplaceholder.typicode.com`

## Atajos

| Atajo | Qué hace |
|---|---|
| `Ctrl + Enter` | Send |
| `Ctrl + S` | Guardar la petición |
| `Ctrl + T` | Pestaña nueva |
| `Ctrl + W` | Cerrar pestaña |

## Variables

| Código | Qué hace |
|---|---|
| `{{base_url}}` | Usa una variable en URL, headers o body |
| `pm.environment.set("nombre", valor)` | Guarda una variable de entorno |
| `pm.environment.get("nombre")` | Lee una variable de entorno |
| `pm.collectionVariables.set("nombre", valor)` | Guarda una variable de colección |

## Pruebas (Scripts → Post-response)

```javascript
// Código de estado
pm.test("Responde 200", function () {
    pm.response.to.have.status(200);
});

// Tiempo de respuesta
pm.test("Menos de 1 segundo", function () {
    pm.expect(pm.response.responseTime).to.be.below(1000);
});

// Lista no vacía
pm.test("Lista con datos", function () {
    pm.expect(pm.response.json()).to.be.an("array").that.is.not.empty;
});

// Valor de un campo
pm.test("Título correcto", function () {
    pm.expect(pm.response.json().title).to.eql("Mi primera publicación");
});

// Existe un campo
pm.test("Tiene id", function () {
    pm.expect(pm.response.json()).to.have.property("id");
});

// Guardar un dato de la respuesta
pm.environment.set("post_id", pm.response.json().id);
```

## Exportar y subir a GitHub

```text
Colección: ⋯ → Export → Collection v2.1
Entorno:   Environments → ⋯ → Export
```

```bash
git add .
git commit -m "Actualizo mi colección"
git push
```

## Newman

```bash
npm install -g newman
newman run "Mi blog.postman_collection.json" -e "Desarrollo.postman_environment.json"
```

## 🧯 Problemas comunes en Git Bash

| Ves esto | Qué pasó | Solución |
|---|---|---|
| `command not found` con símbolos raros, como `$'\302\226cd'` | Copiaste el comando de WhatsApp, un PDF o una página y se pegó un carácter invisible | Borra la línea y **escribe el comando a mano** |
| `No such file or directory` al hacer `cd` | La ruta está mal escrita o usaste `\` | En Git Bash las rutas van con `/`: `cd ~/Downloads/mi-carpeta`. Usa `ls` para ver qué carpetas hay |
| `fatal: not a git repository` | No estás dentro de la carpeta del repo | Entra con `cd`. Arriba de donde escribes debe decir `(main)` |
| Pegar con **Ctrl + V** no hace nada | Git Bash usa otro atajo | Clic derecho → **Paste**, o **Shift + Insert** |
| Una pantalla llena de `~` donde no puedes escribir | Git abrió el editor **Vim** | Escribe `:wq` y presiona **Enter** |
| `Permission denied` o error `403` con el nombre de **otra** cuenta | La compu tiene guardada la cuenta de otra persona | `git credential-manager github logout USUARIO-QUE-APARECE` y repite el `git push` |
| `! [rejected] ... (fetch first)` | GitHub tiene cambios que tu compu no | `git pull --no-edit` y luego `git push` |
| `nothing to commit, working tree clean` | No hay cambios nuevos, o no guardaste el archivo | Guarda con **Ctrl + S** en el Bloc de notas y revisa con `git status` |
| `remote origin already exists` | Ya habías conectado el repo con GitHub | No pasa nada: sigue con el siguiente comando |
| El Bloc de notas guardó `archivo.json.txt` | Windows agregó `.txt` al nombre | Crea los archivos con `notepad nombre.json` desde Git Bash, como dice el curso |

---

[🏠 Inicio](README.md)
