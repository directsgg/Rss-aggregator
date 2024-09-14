# RSS Aggregator

Este proyecto es un **agregador RSS** desarrollado en Go. Su objetivo es recopilar y mostrar contenido de múltiples fuentes RSS en un solo lugar, facilitando la lectura y gestión de artículos. Utiliza postgres como base de datos, sqlc y goose

## Características

- **Recopilación de Feeds**: Agrega y actualiza automáticamente feeds RSS de diversas fuentes.
- **Interfaz Sencilla**: Presenta los artículos de manera clara y organizada.
- **Configuración Flexible**: Permite agregar, eliminar y gestionar feeds fácilmente mediante la creacion de una API Rest.
- **Almacenamiento**: Guarda los artículos en una base de datos de postgres.
- **Autenticación**: Autenticacion gestionada por api keys

## Instalación

1. Clona este repositorio:
    ```sh
    git clone https://github.com/tu-usuario/rss-aggregator.git
    ```
2. Navega al directorio del proyecto:
    ```sh
    cd rss-aggregator
    ```
3. Compila el proyecto:
    ```sh
    go build
    ```

## Uso

1. Ejecuta el binario generado:
    ```sh
    ./rss-aggregator
    ```
2. Accede a la interfaz web en tu navegador:
    ```sh
    http://localhost:8080
    ```


### Uso de sqlc

`sqlc` es una herramienta que genera código Go a partir de consultas SQL, proporcionando interfaces de tipo seguro para interactuar con la base de datos.

1. Se definen los esquema de base de datos en `sql/queries`, tal como:
    ```sql
    CREATE TABLE feeds (
        id SERIAL PRIMARY KEY,
        title TEXT NOT NULL,
        url TEXT NOT NULL
    );
    ```

### Uso de Goose

`Goose` es una herramienta de migración de bases de datos que permite gestionar el esquema de la base de datos mediante cambios incrementales en SQL o funciones Go.

1. Las migraciones se localizan en `sql/schema`, un ejemplo como tal es:
    ```sql
    -- +goose Up
    CREATE TABLE feeds (
        id SERIAL PRIMARY KEY,
        title TEXT NOT NULL,
        url TEXT NOT NULL
    );

    -- +goose Down
    DROP TABLE feeds;
    ```
