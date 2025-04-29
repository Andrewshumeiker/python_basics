```python
    suma = 0
for i in range (10):
    valor = float(input(f"ingrese el valor de {i+1}: "))
    suma += valor
promedio = suma / 10
print(f"el valor de la suma es {suma}")
print(f"el valor del promedio es {promedio}")
```
```python
suma = 0
for i in range(3):
    calificacion = float(input(f"ingrese la {i+1} calificacion: "))
    suma += calificacion
promedio = suma/3
print(f"el promedio es {promedio}")
print (f"las calificaciones son {calificacion}")
```

```python
#Ejericio 1 - 🧩 Gestión de Biblioteca

#Contexto:
#Una pequeña biblioteca necesita registrar sus libros en un sistema muy simple.
#Tareas:
#Crear: Agrega nuevos libros al diccionario. Cada libro tendrá: ID, Título, Autor, Año de publicación.
#Leer: Muestra todos los libros almacenados. Permite buscar un libro por su ID o Título.
#Actualizar: Modifica la información de un libro dado su ID. Ejemplo: cambiar el autor o el año de publicación.
#Eliminar: Elimina un libro de la biblioteca usando su ID.
biblioteca = {
    "001": {"título": "La vorágine", "autor": "José Eustasio Rivera", "año": 1924},
    "002": {"título": "Las intermitencias de la muerte", "autor": "José Saramago", "año": 2005},
    "003": {"título": "El club Dumas", "autor": "Arturo Pérez-Reverte", "año": 1993},
    "004": {"título": "Cien años de soledad", "autor": "Gabrel García Márquez", "año": 1967},
    "005": {"título": "La fiesta del chivo", "autor": "Mario Vargas Llosa", "año": 2000}
}
#Menu de opciones
menu = {
    "opción1": "agregar libro", "opción2": "buscar libro", "opción3": "actualizar", "opción4": "eliminar"
}
#Confirmación para acceder al menú
acceder_menu = input("¿Desea acceder al menú?: ")
if acceder_menu.lower() == "si":
    print(f"Estas son las opciones: \n{menu}")
    accion_usuario = input("Ingrese por favor, la acción que desea llevar a cabo ")
#Condicional que activa las acciones en caso de seleccionar la acción 1
    if accion_usuario == "1" or accion_usuario.lower() == "opcion 1":
        id_nuevo = input("Ingrese el nuevo ID del nuevo libro: ")
        titulo_nuevo = input("Ingrese el titulo ")
        autor_nuevo = input("Ingrese el autor: ")
        año_nuevo = input("Ingrese el año de publicación: ")
#se usa el método "setdefault" para crear una nueva "key" y posteriormente agregar la primer pareja "key" y "value"
        biblioteca.setdefault(id_nuevo,{}).setdefault("título", titulo_nuevo)
#se agrega el resto de la información del nuevo libro
        biblioteca[id_nuevo]["autor"] = autor_nuevo
        biblioteca[id_nuevo]["año"] = año_nuevo
        print(f"Se muestra la biblioteca actualizada: /n{biblioteca}")
#Opción 2 del menú
    elif accion_usuario == "2" or accion_usuario.lower() == "opcion 2":
        formato_busqueda = input("Ingrese \"1\" si desea buscar por ID. Ingrese \"2\" si desea buscar por título")
#Se ofrecen dos opciones de modo de búsqueda, dependiendo de cual elija, se da la información. 
        if formato_busqueda == "1":
            busqueda_usuario = input("Ingrese el ID del libro: ")
            titulo_buscado =  biblioteca[busqueda_usuario]["título"]
            print(f"El libro con el ID {busqueda_usuario}, corresponde al libro {titulo_buscado} y se encuentra disponible")
        elif formato_busqueda == "2":
           busqueda_usuario = input("Ingrese el título del libro: ")
#como no sabemos el ID del libro usamos for para que busque el titulo ingresado, a partir de una lista de los valores del diccionario
            lista_valores_diccionario = biblioteca.values()
            for valor in lista_valores_diccionario:
                 if valor == busqueda_usuario:
                     print(f"El libro {busqueda_usuario} se encuentra en el inventario")
                break
else:
    print("Gracias vuelva pronto")
```
```python
print("!!!Bienvenido al Menú!!!")
#se crea una lista vacia en la cual se almacenaran datos
productos = []
continuar = True
# Se utiliza el el bucle white que permitira crear un ciclo para ingresar nuevos productos
while continuar:
# Se crean cariables en las cuales se le pide al usuario ingresar ciertos datos que se requieren para agregar a la lista
    print("\nPor favor ingresa los siguientes datos:")
    producto = input("Nombre del producto: ")
    cantidad = int(input("Cantidad del producto: "))
    precio_unitario = float(input("Precio unitario del producto: "))
    descuento = float(input("Descuento en % (ej. 10 para 10%): "))
# Se crean variable las cuales se utilizan para generar la operacion que nos indica cual es el valor unitario + la suta total y el descuento
    subtotal = precio_unitario * cantidad
    monto_descuento = subtotal * (descuento / 100)
    total_con_descuento = subtotal - monto_descuento
# Se cra un diccionario el cual permite mantener un orden y permite acceder dinamicamente
    producto_info = {
        "nombre": producto,
        "cantidad": cantidad,
        "precio_unitario": precio_unitario,
        "descuento": descuento,
        "subtotal": subtotal,
        "descuento_aplicado": monto_descuento,
        "total_con_descuento": total_con_descuento
    }

    productos.append(producto_info)
# Se cierra el bucle white con la condicion N si no desea regitrar mas productos
    salir = input("¿Deseas registrar más productos? (N para salir): ").lower()
    if salir == "n":
        continuar = False

# Se muestra el resumen de la compra
print("\n--- Resumen de la compra ---")
total_final = 0
total_descuentos = 0
# Se utiliza el bucle for para recorrer el diccionario y imprima los datos solicitados
for p in productos:
    print(f"\nProducto: {p['nombre']}")
    print(f"Cantidad: {p['cantidad']}")
    print(f"Precio unitario: ${p['precio_unitario']:.2f}")
    print(f"Subtotal: ${p['subtotal']:.2f}")
    print(f"Descuento: {p['descuento']}% -> ${p['descuento_aplicado']:.2f}")
    print(f"Total con descuento: ${p['total_con_descuento']:.2f}")

    total_final += p['total_con_descuento']
    total_descuentos += p['descuento_aplicado']
# Se muestra resumen de descuento
print("\n----------------------------")
print(f"Total de descuentos aplicados: ${total_descuentos:.2f}")
print(f"Total a pagar: ${total_final:.2f}")
```
