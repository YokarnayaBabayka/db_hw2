# SQL-запросы, создающие спроектированную БД музыкального сервиса

CREATE TABLE IF NOT EXISTS Genres (
genre_id SERIAL PRIMARY KEY,
name VARCHAR(40) NOT NULL
);

CREATE TABLE IF NOT EXISTS Singers (
singer_id SERIAL PRIMARY KEY,
name VARCHAR(40) NOT NULL
);

CREATE TABLE IF NOT EXISTS GenresSingers (
genre_id INTEGER REFERENCES Genres(genre_id),
singer_id INTEGER REFERENCES Singers(singer_id),
CONSTRAINT pk PRIMARY KEY (genre_id, singer_id)
);

CREATE TABLE IF NOT EXISTS Albums (
album_id SERIAL PRIMARY KEY,
name VARCHAR(60) NOT NULL,
year INTEGER NOT NULL
);

CREATE TABLE IF NOT EXISTS SingersAlbums (
id SERIAL NOT NULL,
singer_id INTEGER REFERENCES Singers(singer_id),
album_id INTEGER REFERENCES Albums(album_id)
);

CREATE TABLE IF NOT EXISTS Tracks (
track_id SERIAL PRIMARY KEY,
name VARCHAR(60) NOT NULL,
length TIME NOT NULL,
album_id INTEGER NOT NULL REFERENCES Albums(album_id)
);

CREATE TABLE IF NOT EXISTS Collections(
collection_id SERIAL PRIMARY KEY,
name VARCHAR(60) NOT NULL,
year INTEGER NOT NULL
);

CREATE TABLE IF NOT EXISTS CollectionsTracks (
collection_id INTEGER REFERENCES Collections(collection_id),
track_id INTEGER REFERENCES Tracks(track_id),
CONSTRAINT pk1 PRIMARY KEY (collection_id, track_id)
)
