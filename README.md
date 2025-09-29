# Curso de SQL con IA
En este Espacio voy a subir todo lo que me va danto distintas IA para crear un curso de SQL que me sirve a mi. Aqui va a estar el codigo y las lecciones. 
Inicialmente se trabajara con consultas a la siguiente base:
```python
-- Crear la base de datos
CREATE DATABASE tienda;
USE tienda;
-- =============================
-- Tabla de clientes
-- =============================
CREATE TABLE clientes (
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50) NOT NULL,
    apellido VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    ciudad VARCHAR(50),
    telefono VARCHAR(20)
);
--
INSERT INTO clientes (nombre, apellido, email, ciudad, telefono) VALUES
('Ana', 'Gómez', 'ana.gomez@email.com', 'Buenos Aires', '1111-1111'),
('Luis', 'Pérez', 'luis.perez@email.com', 'Córdoba', '2222-2222'),
('María', 'López', 'maria.lopez@email.com', 'Rosario', NULL),
('Juan', 'Martínez', 'juan.martinez@email.com', 'Buenos Aires', '3333-3333'),
('Carla', 'Díaz', 'carla.diaz@email.com', 'Mendoza', NULL),
('Pedro', 'Fernández', 'pedro.fernandez@email.com', 'Córdoba', '4444-4444'),
('Lucía', 'Silva', 'lucia.silva@email.com', 'Buenos Aires', '5555-5555'),
('Diego', 'Torres', 'diego.torres@email.com', 'Rosario', '6666-6666'),
('Sofía', 'Morales', 'sofia.morales@email.com', 'Mendoza', '7777-7777'),
('Mateo', 'Ruiz', 'mateo.ruiz@email.com', 'Córdoba', '8888-8888');
--
-- =============================
-- Tabla de productos
-- =============================
CREATE TABLE productos (
    id_producto INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    categoria VARCHAR(50),
    precio DECIMAL(10,2) NOT NULL,
    stock INT DEFAULT 0
);
INSERT INTO productos (nombre, categoria, precio, stock) VALUES
('Notebook Lenovo', 'Electrónica', 350000.00, 15),
('Mouse Logitech', 'Electrónica', 12000.00, 50),
('Teclado Redragon', 'Electrónica', 25000.00, 30),
('Auriculares Sony', 'Electrónica', 45000.00, 20),
('Silla Gamer', 'Muebles', 90000.00, 10),
('Escritorio Office', 'Muebles', 70000.00, 5),
('Libro Python', 'Libros', 15000.00, 25),
('Libro SQL', 'Libros', 13000.00, 40),
('Impresora HP', 'Electrónica', 80000.00, 12),
('Lámpara LED', 'Hogar', 5000.00, 60);
--
-- =============================
-- Tabla de pedidos
-- =============================
CREATE TABLE pedidos (
    id_pedido INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT,
    fecha DATE NOT NULL,
    total DECIMAL(10,2),
    FOREIGN KEY (id_cliente) REFERENCES clientes(id_cliente)
);
--
INSERT INTO pedidos (id_cliente, fecha, total) VALUES
(1, '2025-09-01', 370000.00),
(3, '2025-09-02', 45000.00),
(5, '2025-09-03', 15000.00),
(2, '2025-09-04', 100000.00),
(7, '2025-09-05', 93000.00);
--
-- =============================
-- Tabla detalle de pedidos
-- =============================
CREATE TABLE detalle_pedido (
    id_detalle INT AUTO_INCREMENT PRIMARY KEY,
    id_pedido INT,
    id_producto INT,
    cantidad INT NOT NULL,
    subtotal DECIMAL(10,2),
    FOREIGN KEY (id_pedido) REFERENCES pedidos(id_pedido),
    FOREIGN KEY (id_producto) REFERENCES productos(id_producto)
);
--
INSERT INTO detalle_pedido (id_pedido, id_producto, cantidad, subtotal) VALUES
(1, 1, 1, 350000.00),  -- Ana compra 1 Notebook
(1, 2, 1, 20000.00),   -- y un Mouse
(2, 4, 1, 45000.00),   -- María compra 1 Auricular
(3, 7, 1, 15000.00),   -- Carla compra 1 Libro Python
(4, 5, 1, 90000.00),   -- Luis compra 1 Silla Gamer
(4, 2, 1, 10000.00),   -- y un Mouse
(5, 6, 1, 70000.00),   -- Lucía compra 1 Escritorio
(5, 10, 1, 23000.00);  -- y una Lámpara
```
