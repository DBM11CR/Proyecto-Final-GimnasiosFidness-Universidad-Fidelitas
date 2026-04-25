Porgramacion cliente servidro concurrente
1. Temática del Proyecto GimnasioFidness
GimnasioFidness es un sistema de gestión para gimnasios que permite administrar:
•	Usuarios del sistema
•	Ejercicios clasificados por tipo (pierna, brazo, espalda)
•	Rutinas personalizadas
•	Series y repeticiones
•	Almacenamiento persistente en base de datos
•	Interacción mediante una aplicación de consola o GUI
El objetivo es ofrecer una herramienta modular, escalable y fácil de mantener para la administración de rutinas de entrenamiento.
2. Estructura General de la Solución
El proyecto se divide en tres capas principales:
✔ Capa de Datos (DAO + Base de Datos) Data Access Object
Encargada de:
•	Conexión a la base de datos Derby (NetBeans)
•	Inserción, consulta y actualización de datos
•	Gestión de tablas: usuarios, ejercicios, rutinas, detalle_rutina, series
✔ Capa de Lógica (Modelo + Controladores)
Incluye:
•	Clases de dominio: Ejercicio, Rutina, Serie
•	Subclases especializadas: EjercicioBrazo, EjercicioPierna, EjercicioEspalda
•	Validación y reglas de negocio
✔ Capa de Presentación (Consola o GUI)
Encargada de:
•	Menús
•	Interacción con el usuario
•	Flujo del sistema
3. Clases Utilizadas y Rol de Cada Una
ConexionBD
•	Administra la conexión JDBC a Derby.
•	Centraliza la URL, usuario y contraseña.
•	Permite que todos los DAOs reutilicen la misma conexión.
Ejercicio
•	Clase base para todos los ejercicios.
•	Contiene nombre, categoría y descripción.
EjercicioBrazo / EjercicioPierna / EjercicioEspalda
•	Subclases que heredan de Ejercicio.
•	Permiten clasificar ejercicios por grupo muscular.
EjercicioDAO
•	Inserta ejercicios en la base.
•	Consulta ejercicios.
•	Maneja la tabla ejercicios.
Rutina
•	Representa una rutina creada por un usuario.
•	Contiene lista de ejercicios.
UsuarioDAO
•	Maneja login y registro.
•	Inserta usuarios en la tabla usuarios.
GimnasiosFidness (Main)
•	Punto de entrada del sistema.
•	Controla el flujo principal del programa.

4. Interacción Entre Componentes
Flujo típico:
1.	El usuario abre el programa.
2.	GimnasiosFidness llama a UsuarioDAO para login o registro.
3.	Una vez autenticado, el usuario accede al menú principal.
4.	Para agregar ejercicios:
o	Se crea un objeto Ejercicio o subclase.
o	Se envía a EjercicioDAO para guardarlo en BD.
5.	Para crear rutinas:
o	Se crea un objeto Rutina.
o	Se insertan registros en rutinas y detalle_rutina.
6.	La base de datos almacena todo de forma persistente.
5. Subsistemas
✔ Subsistema de Usuarios
•	Registro
•	Login
•	Validación
✔ Subsistema de Ejercicios
•	Creación
•	Clasificación
•	Consulta
✔ Subsistema de Rutinas
•	Creación de rutina
•	Agregar ejercicios
•	Guardar series
✔ Subsistema de Persistencia
•	DAO
•	Conexión JDBC
•	Base de datos Derby
6. ¿Por qué se eligió Base de Datos en NetBeans (Derby)?
•	Integración nativa con NetBeans
•	Fácil de administrar desde Services → Databases
•	No requiere instalación externa
•	Ideal para proyectos académicos
•	Permite modo embebido y cliente-servidor
•	Compatible con JDBC estándar
7. Evidencia de Redes
Aunque el proyecto no usa sockets, sí usa comunicación cliente-servidor mediante JDBC, lo cual es evidencia válida de redes:
•	El programa actúa como cliente
•	Derby actúa como servidor
•	La comunicación ocurre por TCP/IP en el puerto 1527
•	Se usa el protocolo JDBC para enviar comandos SQL
•	Ejemplo de URL de conexión:
jdbc:derby://localhost:1527/fidnessdb
Esto demuestra:
•	Conexión remota
•	Transporte de datos
•	Comunicación bidireccional
•	Arquitectura distribuida


8. Resumen Total del Proyecto
GimnasioFidness es un sistema modular que permite:
•	Registrar usuarios
•	Iniciar sesión
•	Crear ejercicios
•	Consultar ejercicios
•	Crear rutinas personalizadas
•	Guardar series y repeticiones
•	Almacenar todo en una base de datos Derby
•	Mantener una arquitectura limpia con DAOs y modelos
El sistema es funcional, escalable y fácil de extender.
9. Conclusiones
•	La arquitectura modular permitió separar responsabilidades.
•	El uso de Derby simplificó la persistencia de datos.
•	Los DAOs facilitaron la comunicación con la base.
•	El sistema cumple con los requisitos académicos de:
o	Persistencia
o	Redes
o	Programación orientada a objetos
o	Modularidad
10. Recomendaciones de Mejora
✔ Optimización
•	Implementar pooling de conexiones JDBC
•	Usar índices en tablas con consultas frecuentes
•	Migrar a una BD más robusta (MySQL, PostgreSQL)
✔ Interfaz
•	Crear una GUI en JavaFX o Swing
•	Agregar validaciones visuales
•	Mejorar la experiencia del usuario
✔ Sistema Final para Cliente
•	Dashboard con estadísticas
•	Rutinas recomendadas por IA
•	Exportación de rutinas a PDF
•	Control de progreso del usuario
✔ Aplicación Móvil
•	Crear app Android/iOS con Flutter o React Native
•	Sincronización con servidor
•	Notificaciones de entrenamiento
•	Rutinas personalizadas desde el celular
