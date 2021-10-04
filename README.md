# Semana-11
tarea

use Banco5
if object_id('dbo.Product', 'U') is not null
   drop table dbo.Banco4;
create table dbo.Banco4 (Transaciones varchar(20), Fecha VARCHAR (20), Monto varchar(20), Cuenta varchar(30));

Insert into dbo.Banco4(Transaciones, Fecha, Monto, Cuenta )
values ('Pensiones','05/02/2021','250', 'Luis@gmail.com'), ('Pago' ,'02/10/2020','300', 'Pedro@gmail.com');
Insert into dbo.Banco4(Transaciones, Fecha, Monto, Cuenta )
values ('Rembolso','03/10/2021','600', 'daniela@gmail.com'), ('Retiro' ,'09/06/2019','700', 'leslie@gmail.com');

if object_id('dbo.Product', 'U') is not null
   drop table dbo.Banco8;
create table dbo.Banco8 (Nombre varchar(20), edad VARCHAR (400), telefono varchar(20), correo varchar(30), departamento varchar(30),cuenta varchar(40),transacion varchar(30));

Insert into dbo.Banco8(Nombre, edad, telefono, correo, departamento,cuenta,transacion )
values ('luis','30',7044-4519, 'Luis@gmail.com','San Miguel','Luis@gmail.com','Pensiones'), ('pedro' ,'25',7035-6989, 'Pedro@gmail.com','San Miguel','Pedro@gmail.com','Pago');
Insert into dbo.Banco8(Nombre, edad, telefono, correo, departamento,cuenta,transacion )
values ('daniela','18',7025-5859, 'daniela@gmail.com','San Miguel','daniela@gmail.com','Rembolso'), ('Leslie' ,'21',7025-7847, 'leslie@gmail.com','San Miguel','leslie@gmail.com','Retiro');


   drop table dbo.Banco7;
create table dbo.Banco7 (Departamento varchar(20), Colonia VARCHAR (20),cuenta varchar(40));

Insert into dbo.Banco7(Departamento, Colonia,cuenta )
values ('San Miguel','El Jute','Pedro@gmail.com'), ('El Papalón' ,'San Andrés','Pedro@gmail.com');
Insert into dbo.Banco7(Departamento, Colonia, cuenta  )
values ('San Miguel','El Sitio','Pedro@gmail.com'), ('San Miguel','San Antonio Silva','Pedro@gmail.com');

--INNER JOIN 
SELECT
	r.Transaciones, r.Fecha, rc.Nombre Nombre 
FROM dbo.Banco4 r
INNER JOIN dbo.Banco5 rc
ON r.Cuenta = rc.correo;

--LEFT JOIN
SELECT
	p.Transaciones Producto, o.Nombre ORDEN
FROM dbo.Banco4 p
LEFT JOIN dbo.Banco8 o
ON p.Cuenta = o.cuenta AND o.edad=18
ORDER BY o.edad DESC;

--RIGHT JOIN
SELECT
	o.Transaciones ORDEN, p.Nombre Producto
FROM dbo.Banco4 o
RIGHT JOIN dbo.Banco8 p
ON o.Transaciones = p.transacion
WHERE o.Transaciones IS NULL

--FULL JOIN
SELECT
	od.Departamento, p.Transaciones, so.correo
FROM dbo.Banco4 p
FULL JOIN dbo.Banco7 od 
ON p.Cuenta = od.cuenta
FULL JOIN dbo.Banco8 so
ON od.Departamento = so.departamento;
