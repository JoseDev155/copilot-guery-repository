Sí, al ejecutar todos esos comandos, cambiarías el puerto en el que Db2 escucha para conexiones TCP/IP y reiniciarías el servicio para aplicar los cambios. Aquí está un desglose de lo que hace cada comando:

1. **Cambiar el Puerto del Servicio**:
   ```sh
   db2 update dbm cfg using svcename 50001
   ```
   - Este comando actualiza la configuración de Db2 para utilizar el puerto `50001` en lugar del puerto predeterminado para el servicio.

2. **Habilitar TCP/IP (si no está ya habilitado)**:
   ```sh
   db2set db2comm=tcpip -i
   ```
   - Este comando configura Db2 para utilizar el protocolo TCP/IP. Si ya está configurado, este paso puede ser innecesario, pero no causa problemas ejecutarlo nuevamente.

3. **Detener el Servicio Db2**:
   ```sh
   db2stop
   ```
   - Este comando detiene el servicio de Db2 para que puedas aplicar los cambios de configuración.

4. **Iniciar el Servicio Db2**:
   ```sh
   db2start
   ```
   - Este comando reinicia el servicio de Db2, aplicando los nuevos cambios de configuración, incluyendo el nuevo puerto.

### Flujo de Ejecución:
Al ejecutar estos comandos en secuencia, Db2 debería cambiar a escuchar en el nuevo puerto `50001` y estar listo para aceptar conexiones una vez que se reinicie el servicio.

Si necesitas más detalles o tienes alguna otra pregunta, ¡házmelo saber! 😊🚀