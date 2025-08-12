¡Claro! Manejar variables de entorno en PHP es una práctica muy útil para mantener la configuración de tu aplicación separada del código. Aquí te dejo una guía sencilla para hacerlo:

1. Crear un archivo .env

Primero, crea un archivo llamado .env en la raíz de tu proyecto. Este archivo contendrá tus variables de entorno. Por ejemplo:

DB_HOST=localhost
DB_USER=root
DB_PASS=secret

2. Instalar vlucas/phpdotenv

Para manejar las variables de entorno en PHP, puedes usar la librería vlucas/phpdotenv. Instálala usando Composer:

composer require vlucas/phpdotenv

3. Cargar las variables de entorno en tu aplicación

En tu archivo principal de PHP (por ejemplo, index.php), carga las variables de entorno usando Dotenv:

<?php
require 'vendor/autoload.php';

use Dotenv\Dotenv;

$dotenv = Dotenv::createImmutable(__DIR__);
$dotenv->load();

// Ahora puedes acceder a las variables de entorno
$dbHost = $_ENV['DB_HOST'];
$dbUser = $_ENV['DB_USER'];
$dbPass = $_ENV['DB_PASS'];

// Ejemplo de uso
$mysqli = new mysqli($dbHost, $dbUser, $dbPass);

if ($mysqli->connect_error) {
    die('Error de conexión (' . $mysqli->connect_errno . ') ' . $mysqli->connect_error);
}

echo 'Conexión exitosa a la base de datos';
?>

4. Asegúrate de que el archivo .env no se suba al repositorio

Para evitar que el archivo .env se suba a tu repositorio de control de versiones, añade una entrada en tu archivo .gitignore:

.env

Resumen
Crea un archivo .env con tus variables de entorno.
Instala vlucas/phpdotenv usando Composer.
Carga las variables de entorno en tu aplicación con Dotenv.
Añade .env a tu .gitignore.

¡Y eso es todo! Ahora tienes una forma segura y eficiente de manejar variables de entorno en tu aplicación PHP. Si necesitas más ayuda, no dudes en preguntar. ¡Buena suerte con tu proyecto!