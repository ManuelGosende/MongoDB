## Clase 1

### 1) Instalar MongoDB en ambiente local.

### 2) Conectarse a MongoDB vía CLI
`mongo`

### 3) Crear una nueva base de datos llamada futbolfifa
`use futbolfifa`

### 4) Crear una nueva collection llamada players
`db.createCollection("players")`

### 5) Insertar 5 documentos en la collection players con datos básicos (nombre, apellido, posición, fecha de nacimiento, etc)
`db.players.insert({"name": "Javier", "lastname": "Marcherano", "position": "cmd", "age": 36})`

`db.players.insert({"name": "Mariano", "lastname": "Andújar", "position": "gk", "age": 37})`

`db.players.insert({"name": "Martín", "lastname": "Cauteruccio", "position": "dc", "age": 33})`

`db.players.insert({"name": "Darío", "lastname": "Sarmiento", "position": "mpo", "age": 17})`

`db.players.insert({"name": "Nazareno", "lastname": "Colombo", "position": "cb", "age": 21})`

### 6) Listar todos los documentos de la collection players
`db.players.find()`

### 7) Crear otras collections con documentos (ej. teams, games, etc)
`db.createCollection("teams")`

`db.createCollection("leagues")`
