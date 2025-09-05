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
