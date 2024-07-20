import re

# Diccionario para almacenar los datos de los ciudadanos
ciudadanos = {}

def validar_nif(nif):
    """Valida que el NIF tenga la estructura correcta."""
    patron = re.compile(r'^\d{8}-[A-Z0-9]{3}$')
    return patron.match(nif) is not None

def grabar():
    """Graba los datos de una persona."""
    nif = input("Ingrese el NIF (formato 99999999-XXX): ")
    if not validar_nif(nif):
        print("NIF inválido. Debe tener el formato 99999999-RTX.")
        return
    nombre = input("Ingrese el nombre (mínimo 8 caracteres): ")
    if len(nombre) < 8:
        print("Nombre inválido. Debe tener al menos 8 caracteres.")
        return
    try:
        edad = int(input("Ingrese la edad (mayor o igual a 0): "))
        if edad < 0:
            print("Edad inválida. Debe ser mayor o igual a 0.")
            return
    except ValueError:
        print("Edad inválida. Debe ser un número.")
        return
    
    ciudadanos[nif] = {'nombre': nombre, 'edad': edad}
    print("Datos grabados correctamente.")

def buscar():
    """Busca una persona por su NIF y muestra su información."""
    nif = input("Ingrese el NIF a buscar: ")
    if nif in ciudadanos:
        datos = ciudadanos[nif]
        print(f"NIF: {nif}")
        print(f"Nombre: {datos['nombre']}")
        print(f"Edad: {datos['edad']}")
        if nif[8] in '0123456789':
            print("La persona pertenece a la Unión Europea.")
        else:
            print("La persona no pertenece a la Unión Europea.")
    else:
        print("No se encontró a la persona con el NIF proporcionado.")

def imprimir_certificados():
    """Imprime certificados con valores aleatorios ingresados desde el teclado."""
    nif = input("Ingrese el NIF para imprimir certificados: ")
    if nif in ciudadanos:
        nombre_certificado = input("Ingrese el nombre del certificado: ")
        datos = ciudadanos[nif]
        print(f"Certificado: {nombre_certificado}")
        print(f"NIF: {nif}")
        print(f"Nombre: {datos['nombre']}")
        print(f"Edad: {datos['edad']}")
    else:
        print("No se encontró a la persona con el NIF proporcionado.")

def salir():
    """Sale del programa."""
    print("Gracias por usar el programa. Nombre del desarrollador: [Tu Nombre]. Versión del programa: 1.0")

def menu():
    """Muestra el menú y maneja las opciones."""
    while True:
        print("\nMenú:")
        print("1. Grabar")
        print("2. Buscar")
        print("3. Imprimir certificados")
        print("4. Salir")
        opcion = input("Seleccione una opción: ")
        
        if opcion == "1":
            grabar()
        elif opcion == "2":
            buscar()
        elif opcion == "3":
            imprimir_certificados()
        elif opcion == "4":
            salir()
            break
        else:
            print("Opción inválida. Intente nuevamente.")

# Inicia el programa
menu()
# prueba
prueba 
