# PROYECTO FINAL BASES DE DATOS

En el siguiente repositorio se demostrara el trabajo realizado por un grupo de estudiantes de la escuela itc en el cual se ilustrara su trabajo realizado de acuerdo con las tematicas explicadas en la clase de bases de datos las cuales a medida del avance del proyecto se explicaran.


<div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/logo.png?raw=true.png" width="90%">
</div>

Tomado de [AdministracionPescaderia]
https://github.com/KevinD008/AdministracionPescaderia/blob/main/logo.png.

## Objetivo general

Desarrollar una página web funcional que permita a "Marbel" gestionar eficientemente su inventario y ejecutar estrategias de marketing digital, con el propósito de potenciar su estrategia comercial y facilitar la venta y distribución de sus productos.



### 1. ¿Cuál es el nombre de todos los países registrados en la base de datos?
SELECT nombre_pais FROM PAIS;

- *Consulta en SQL:*
 <div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/consu1.PNG?raw=true" width="90%">
</div>

  

  
### 2. ¿Cuáles son los departamentos que pertenecen a Colombia?

SELECT nombre_estado FROM DEPARTAMENTOS WHERE id_pais = 1;

- *Consulta en SQL:*
<div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/consu2.PNG?raw=true" width="90%">
</div>

  

### 3. ¿Qué ciudades están registradas en el sistema?

SELECT nombre_ciudad FROM CIUDAD;

  <div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/consu3.PNG?raw=true" width="90%">
</div>

### 4.¿Cuál es la dirección asociada al proveedor "Pescados del Norte"?

SELECT direccion 
FROM DIRECCION 
WHERE id_direccion = (SELECT id_direccion FROM PROVEEDOR WHERE nombre_proveedor = 'Pescados del Norte');

- *Consulta en SQL:*
  <div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/consu4.PNG?raw=true" width="90%">
</div>

### 5. ¿Qué productos vende el proveedor con el NIT '900123456-3'?

SELECT producto 
FROM PRODUCTOS 
WHERE nit = '900123456-3';

- *Consulta en SQL:*
<div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/consu5.PNG?raw=true" width="90%">
</div>

### 6. ¿Qué proveedor tiene el correo 'peste@gmail.com'?

SELECT nombre_proveedor 
FROM PROVEEDOR 
WHERE email_proveedor = 'peste@gmail.com';

  <div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/consu6.PNG?raw=true" width="90%">
</div>

### 7. ¿Cuántas ciudades están registradas en el departamento de Antioquia?

SELECT COUNT(*) AS total_ciudades 
FROM CIUDAD 
WHERE id_estado = (SELECT id_estado FROM DEPARTAMENTOS WHERE nombre_estado = 'Antioquia');

- *Consulta en SQL:*
 <div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/consu7.PNG?raw=true" width="90%">
</div>

consultas nivel medio (8)

### 8. ¿Cuáles son las ciudades del departamento "Cundinamarca" y sus direcciones asociadas?

SELECT c.nombre_ciudad, d.direccion 
FROM CIUDAD c
JOIN DIRECCION d ON c.id_ciudad = d.id_ciudad
WHERE c.id_estado = (SELECT id_estado FROM DEPARTAMENTOS WHERE nombre_estado = 'Cundinamarca');

- *Consulta en SQL:*
 <div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/consu8.PNG?raw=true" width="90%">
</div>

### 9. ¿Qué proveedores están asociados a la ciudad de "Bogotá"?

SELECT p.nombre_proveedor 
FROM PROVEEDOR p
JOIN DIRECCION d ON p.id_direccion = d.id_direccion
JOIN CIUDAD c ON d.id_ciudad = c.id_ciudad
WHERE c.nombre_ciudad = 'Bogotá';

- *Consulta en SQL:*
  <div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/consu9.PNG?raw=true" width="90%">
</div>

### 10. ¿Qué productos son vendidos por proveedores ubicados en "Medellín"?

SELECT pr.producto 
FROM PRODUCTOS pr
JOIN PROVEEDOR p ON pr.nit = p.nit
JOIN DIRECCION d ON p.id_direccion = d.id_direccion
JOIN CIUDAD c ON d.id_ciudad = c.id_ciudad
WHERE c.nombre_ciudad = 'Medellín';

- *Consulta en SQL:*
  <div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/consu10.PNG?raw=true" width="90%">
</div>

### 11.¿Cuáles son los departamentos que tienen más de una ciudad registrada?

SELECT d.nombre_estado, COUNT(c.id_ciudad) AS total_ciudades
FROM DEPARTAMENTOS d
JOIN CIUDAD c ON d.id_estado = c.id_estado
GROUP BY d.nombre_estado
HAVING COUNT(c.id_ciudad) > 1;

- *Consulta en SQL:*
  <div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/consu11.PNG?raw=true" width="90%">
</div>

### 12.  ¿Qué productos se venden y cuáles son sus respectivos proveedores y ciudades?

SELECT pr.producto, p.nombre_proveedor, c.nombre_ciudad 
FROM PRODUCTOS pr
JOIN PROVEEDOR p ON pr.nit = p.nit
JOIN DIRECCION d ON p.id_direccion = d.id_direccion
JOIN CIUDAD c ON d.id_ciudad = c.id_ciudad;

- *Consulta en SQL:*
  <div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/consu12.PNG?raw=true" width="90%">
</div>

### 13.¿Cuántos proveedores están asociados a cada ciudad?

SELECT c.nombre_ciudad, COUNT(p.nit) AS total_proveedores 
FROM CIUDAD c
JOIN DIRECCION d ON c.id_ciudad = d.id_ciudad
JOIN PROVEEDOR p ON d.id_direccion = p.id_direccion
GROUP BY c.nombre_ciudad;

- *Consulta en SQL:*
  <div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/consu13.PNG?raw=true" width="90%">
</div>

### 14.  ¿Qué proveedores venden "Langosta"?

SELECT p.nombre_proveedor 
FROM PRODUCTOS pr
JOIN PROVEEDOR p ON pr.nit = p.nit
WHERE pr.producto = 'Langosta';

- *Consulta en SQL:*
  <div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/consu14.PNG?raw=true" width="90%">
</div>

### 15.¿Qué ciudades tienen proveedores que venden "Atún"?

SELECT DISTINCT c.nombre_ciudad 
FROM PRODUCTOS pr
JOIN PROVEEDOR p ON pr.nit = p.nit
JOIN DIRECCION d ON p.id_direccion = d.id_direccion
JOIN CIUDAD c ON d.id_ciudad = c.id_ciudad
WHERE pr.producto = 'Atún';

- *Consulta en SQL:*
 <div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/consu15.PNG?raw=true" width="90%">
</div>

### CREACION DE USUARIOS

-- Como ultimo paso creamos usuarios con sus distintas acciones
CREATE USER 'admimarbel'@'%' IDENTIFIED BY 'Pepa1974';

-- Otorgar todos los privilegios al administrador
GRANT ALL PRIVILEGES ON . TO 'admimarbel'@'%' WITH GRANT OPTION;

-- Crear usuario cliente
CREATE USER 'clientemarbel'@'%' IDENTIFIED BY '12345';

-- Otorgar permisos al cliente para solo consultas y registro
GRANT SELECT, INSERT ON PAIS TO 'clientemarbel'@'%';
GRANT SELECT, INSERT ON DEPARTAMENTOS TO 'clientemarbel'@'%';
GRANT SELECT, INSERT ON CIUDAD TO 'clientemarbel'@'%';
GRANT SELECT, INSERT ON DIRECCION TO 'clientemarbel'@'%';
GRANT SELECT, INSERT ON PROVEEDOR TO 'clientemarbel'@'%';
GRANT SELECT, INSERT ON PRODUCTOS TO 'clientemarbel'@'%';

-- Aplicar los cambios de privilegios
FLUSH PRIVILEGES;

- *Consulta en SQL:*
<div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/crearusu1.PNG?raw=true" width="90%">
</div>
<div align="center">
  <img src="https://github.com/KevinD008/AdministracionPescaderia/blob/main/imagenes_consultas/crearusu2.PNG?raw=true" width="90%">
</div>
</div>
