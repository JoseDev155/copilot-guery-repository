¡Claro! Aquí tienes un ejemplo de cómo crear una aplicación CRUD (Crear, Leer, Actualizar, Eliminar) en C utilizando MySQL:

1. Configuración Inicial

Primero, asegúrate de tener instaladas las bibliotecas necesarias para trabajar con MySQL en C. Puedes instalar libmysqlclient en tu sistema.

2. Conexión a la Base de Datos

```c
#include <mysql/mysql.h>
#include <stdio.h>
#include <stdlib.h>

MYSQL *con;

void finish_with_error(MYSQL *con) {
    fprintf(stderr, "%s\n", mysql_error(con));
    mysql_close(con);
    exit(1);
}

void connect_to_db() {
    con = mysql_init(NULL);
    if (con == NULL) {
        fprintf(stderr, "mysql_init() failed\n");
        exit(1);
    }

    if (mysql_real_connect(con, "localhost", "usuario", "contraseña", "nombre_base_datos", 0, NULL, 0) == NULL) {
        finish_with_error(con);
    }
}
```

3. Crear

```c
void create_record(const char *name, int age) {
    char query[256];
    snprintf(query, sizeof(query), "INSERT INTO users(name, age) VALUES('%s', %d)", name, age);

    if (mysql_query(con, query)) {
        finish_with_error(con);
    }
}
```

4. Leer

```c
void read_records() {
    if (mysql_query(con, "SELECT * FROM users")) {
        finish_with_error(con);
    }

    MYSQL_RES *result = mysql_store_result(con);
    if (result == NULL) {
        finish_with_error(con);
    }

    int num_fields = mysql_num_fields(result);
    MYSQL_ROW row;

    while ((row = mysql_fetch_row(result))) {
        for (int i = 0; i < num_fields; i++) {
            printf("%s ", row[i] ? row[i] : "NULL");
        }
        printf("\n");
    }

    mysql_free_result(result);
}
```

5. Actualizar

```c
void update_record(int id, const char *name, int age) {
    char query[256];
    snprintf(query, sizeof(query), "UPDATE users SET name='%s', age=%d WHERE id=%d", name, age, id);

    if (mysql_query(con, query)) {
        finish_with_error(con);
    }
}
```

6. Eliminar

```c
void delete_record(int id) {
    char

```