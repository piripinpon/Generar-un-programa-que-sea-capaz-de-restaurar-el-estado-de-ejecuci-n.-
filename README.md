# Carrito de Compras 

## 📌 Descripción
Este proyecto implementa un **carrito de compras en PHP** que utiliza el concepto de **application checkpointing**.  
La idea principal es que el estado de la aplicación (los productos del carrito) se **guarda en la base de datos** cada vez que ocurre un cambio.  
De esta manera, si el sistema falla o se reinicia, el usuario no pierde su progreso: el carrito se **restaura automáticamente** desde el último estado guardado.

## ⚙️ Funcionamiento del Código
- El archivo `carrito.php` recibe el **id del pedido** y consulta en la base de datos los productos que pertenecen a ese pedido.
- Cada producto muestra:
  - Nombre
  - Cantidad
  - Costo unitario
  - Costo total
- Además, se calcula un **gran total** del pedido.
- Existe la opción de **eliminar productos**, lo cual actualiza la base de datos y, por lo tanto, genera un nuevo **checkpoint**.
- Al volver a abrir `carrito.php`, se ejecuta la consulta SQL y se **reconstruye el carrito desde la base de datos**, restaurando el estado previo.

## 📖 Relación con Application Checkpointing
- **Checkpoint:** Cada vez que se agrega o elimina un producto, el nuevo estado del carrito se guarda en la base de datos.
- **Restauración:** Si el sistema se cierra, al abrir de nuevo `carrito.php` el estado anterior se recupera automáticamente desde la base de datos.
- Esto garantiza **tolerancia a fallos**, ya que el sistema puede retomar desde el último punto guardado sin que el usuario pierda información.

## 🚀 Tecnologías usadas
- PHP
- MySQL
- HTML

Como funcionamiento visual, primero entramos a la pagina desarrollada, donde elegimos un articulo.

<img width="462" height="649" alt="image" src="https://github.com/user-attachments/assets/0b5895a7-9a92-456b-b921-1684b4e5c2a1" />

Seguido agregamos ese producto al carrito

<img width="1735" height="330" alt="image" src="https://github.com/user-attachments/assets/94512765-1ff2-4305-bc88-27bc86fb8be1" />

Cerramos sesion para comprobar que se realizo el checkpoint de mis ultimos movimientos en compras.

<img width="684" height="496" alt="image" src="https://github.com/user-attachments/assets/fd784d18-ac95-4707-8804-080ca412b12f" />

Volvemos a entrar con el mismo usuario y revisamos el carrito donde todavia indica mis productos en carro.

<img width="1661" height="387" alt="image" src="https://github.com/user-attachments/assets/f60268de-98de-40d3-b536-9256dcb02bbc" />



