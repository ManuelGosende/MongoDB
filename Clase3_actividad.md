## Clase 3

### 1) Utilizar la misma base de datos de películas e insertar varias películas con distinto contenido
~~~
db.movies.insertMany([
    {
        "titulo": "Volver al futuro",
        "year": 2003,
        "rating": 4.7,
        "genre": "Comedia",
        "description": "Una máquina del tiempo transporta a un adolescente a los años 50, cuando sus padres todavía estudiaban en la secundaria.",
        "actors": ["Michael Fox", "Claudia Wells"],
        "country": "USA",
        "income": 203434514,
        "duration": 109
    },
    {
        "titulo": "Terminator",
        "year": 1985,
        "rating": 5.0,
        "genre": "Accion",
        "description": "Un asesino cibernético del futuro es enviado a Los Ángeles para matar a la mujer que procreará a un líder.",
        "actors": ["Arnold Schwarzenegger", "Michael Biehn", "Lance Henriksen"],
        "country": "USA",
        "income": 2139200,
        "duration": 135
    },
    {
        "titulo": "El secreto de sus ojos",
        "year": 2009,
        "rating": 4.9,
        "genre": "Drama",
        "description": "Un juez tiene dudas acerca de los planes de un oficial de justicia recientemente retirado que intenta descubrir al culpable de la violación y el asesinato de una joven, crimen ocurrido varias décadas atrás.",
        "actors": ["Ricardo Darín", "Soledad Villamil", "Pablo Rago"],
        "country": "Argentina",
        "income": 324983838,
        "duration": 120
    }
])
~~~

### 2) Listar todas las películas del año 2018
`db.movies.find({year: 2018})`

### 3) Listar las 10 primeras películas de Hollywood
`db.movies.find({country: "USA"}).limit(10).sort({rating: -1})`

### 4) Listar las 5 películas más taquilleras
`db.movies.find().limit(5).sort({income: -1})`

### 5) Listar el 2do conjunto de 5 películas más taquilleras
`db.movies.find().skip(5).limit(5).sort({income: -1})`

### 6) Repetir query 3 y 4 pero retornando sólo el título y genre
~~~
db.movies.find({country: "USA"}, {titulo: 1, genre: 1, _id: 0}).limit(10).sort({rating: -1})

db.movies.find({}, {titulo: 1, genre: 1, _id: 0}).limit(5).sort({income: -1})
~~~

### 7) Mostrar los distintos países que existen en la base de datos
`db.movies.distinct("country")`
