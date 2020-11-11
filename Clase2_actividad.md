## Clase 2

### 1) Crear una nueva base de datos de un sistema de streaming de video (ej. Netflix, Flow, Amazon Prime) que permita almacenar movies.
`use netflix`

### 2) Para cada movie, se debería guardar información como título (String), year (Number), rating (Number, entre 1.0 y 5.0), genre (String), description (String), actors (Array), country (String), income (Number), duration (Number)
`db.createCollection("movies")`

### 3) Agregar películas usando insert(), insertOne() & insertMany()
~~~
db.movies.insert(
    {
        "titulo": "El Ángel",
        "year": 2018,
        "rating": 4.1,
        "genre": "History",
        "description": "El rostro angelical de Carlos, un adolescente de 17 años, esconde una oscura faceta de robos, mentiras y asesinatos.",
        "actors": ["Lorenzo Ferro", "Mercedes Morán", "Malena Villa"],
        "country": "Argentina",
        "income": 30000,
        "duration": 125
    })
    
    WriteResult({ "nInserted" : 1 })
    
    db.movies.insertOne(
    {
        "titulo": "Contratiempo",
        "year": 2016,
        "rating": 4.2,
        "genre": "Suspenso",
        "description": "Un joven empresario despierta en un hotel junto al cadáver de su amante. Para demostrar su inocencia, contrata a la mejor abogada criminalista del país. Ambos tienen una noche para preparar su defensa y evitar que sea declarado culpable.",
        "actors": ["Mario Casas", "Barbara Lennie", "José Coronado"],
        "country": "España",
        "income": 823003000,
        "duration": 210
    })

{
        "acknowledged" : true,
        "insertedId" : ObjectId("5f9330da66c104b67b22dbca")
}

db.movies.insertMany([
    {
        "titulo": "Los Simpsons",
        "year": 2007,
        "rating": 4.9,
        "genre": "Comedia",
        "description": "La combinación de Homero, su nuevo puerco mascota, y un silo lleno de excremento podrían provocar un desastre que amenace no sólo a Springfield, sino al mundo entero. ",
        "actors": ["Homero", "Bart", "Lisa"],
        "country": "USA",
        "income": 49859893,
        "duration": 125
    },
    {
        "titulo": "Escuela de Rock",
        "year": 2003,
        "rating": 4.0,
        "genre": "Comedia",
        "description": "Despedido por su banda y en problemas económicos, un guitarrista desempleado se hace pasar por maestro en una escuela.",
        "actors": ["Jack Black", "Mike White", "Joan Cusack"],
        "country": "USA",
        "income": 338992812,
        "duration": 100
    }
])

{
        "acknowledged" : true,
        "insertedIds" : [
                ObjectId("5f9332b366c104b67b22dbcb"),
                ObjectId("5f9332b366c104b67b22dbcc")
        ]
}
~~~

### 4) Actualizar películas agregando el field highlighted=true a aquellas con rating > 4.5
~~~
db.movies.updateMany({rating: {$gt: 4.5}}, {$set: {highlighted: true}})

{ "acknowledged" : true, "matchedCount" : 2, "modifiedCount" : 2 }
~~~

### 5) Actualizar películas cambiando el genre “drama” por “bored”
~~~
db.movies.updateMany({genre: "Drama"} , {$set: {genre: "Bored"}})

{ "acknowledged" : true, "matchedCount" : 1, "modifiedCount" : 1 }
~~~

### 6) Borrar todas las películas que tengan más de 30 años
~~~
db.movies.deleteMany({year: {$lt: 2020-30}})

{ "acknowledged" : true, "deletedCount" : 1 }
~~~

### 7) Buscar todas las películas argentinas
`db.movies.find({country: "Argentina"})`

### 8) Buscar todas las películas de acción con un buen rating (ej. > 4.0) que hayan salido los últimos 2 años
~~~
db.movies.find(
    {
        genre: "Accion",
	      rating: {$gt: 4.0},
	      year: {$gt: 2020-2}
    })
    ~~~
