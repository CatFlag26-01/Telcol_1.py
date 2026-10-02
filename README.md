Guia de Errores Comunes y Soluciones en Python
Este documento contiene la explicacion detallada de algunos de los errores mas comunes al iniciarse en la programacion con Python, tomando como base ejemplos practicos con estructuras condicionales (if/elif/else) e interaccion con el usuario (input).
1. Manejo de Tipos de Datos con input()
Error: TypeError por comparacion de tipos no compatibles
Por defecto, la funcion input() en Python siempre devuelve un texto (str), sin importar si el usuario escribe un numero. Intentar comparar una cadena de texto con un entero (int) genera un error de tipo.
Ejemplo con error:
nivel_magico_esperado = 10
# input() devuelve un 'str' (ejemplo: "15")
nivel_magico_person = input("Dime tu nivel magico: ")

# Intentar comparar 'str' con 'int' falla con TypeError:
if nivel_magico_person < nivel_magico_esperado:
    print("El elixir burbujea")


Solucion:
Convertir explicitamente el valor ingresado a entero usando int():
nivel_magico_person = int(input("Dime tu nivel magico: "))


2. Sintaxis de Booleanos (True y False)
Error: NameError por uso de minusculas
A diferencia de otros lenguajes como JavaScript o C++, en Python los valores booleanos deben escribirse obligatoriamente con la primera letra en mayuscula.
Ejemplo con error:
# 'true' y 'false' en minuscula provocan NameError
if edad_person > 15 and capa_person == true:
    print("Adelante")


Solucion:
Usar True y False:
if edad_person > 15 and capa_person == True:
    print("Adelante")


Buena practica (Codigo Idiomatico):
En Python no es necesario comparar un booleano directamente con == True o == False:
# En lugar de: if capa_person == True:
if capa_person:
    print("Tiene la capa")

# En lugar de: if capa_person == False:
if not capa_person:
    print("No tiene la capa")


3. Cobertura de Limites en Condiciones (<, >, <=, >=)
Error: Dejar valores fuera de las condiciones
Al usar operadores de comparacion estricta (< y >), los valores limite (como el numero exacto indicado) pueden quedar excluidos sin querer, cayendo de forma inesperada en el bloque else.
Ejemplo con vacios de logica:
# Si la edad es exactamente 15, no cumple > 15 ni < 15, por lo que cae en else.
if edad_person > 15 and capa_person:
    print("Acceso permitido")
elif edad_person < 15 and capa_person:
    print("Edad insuficiente")
else:
    print("Sin requisitos")  # Aqui caera una persona de 15 anos


Solucion:
Utilizar >= (mayor o igual) o <= (menor o igual) segun corresponda:
if edad_person >= 15 and capa_person:
    print("Acceso permitido")


Codigo Final Integrado y Corregido
# --- EJERCICIO 1: Elixir Magico ---
nivel_magico_esperado = 10
nivel_magico_necesario = 20

nivel_magico_person = int(input("Dime, mago, cual es tu nivel magico?: "))

if nivel_magico_person < nivel_magico_esperado:
    print("El elixir burbujea")
elif nivel_magico_person < nivel_magico_necesario:
    print("El elixir resplandece")
else:
    print("El elixir te rejuvenece")

print("-" * 40)

# --- EJERCICIO 2: Evaluacion del Mago ---
edad_person = int(input("Dime cual es tu edad: "))
capa_input = int(input("Tienes la capa de invisibilidad? (1 para Si, 0 para No): "))
capa_person = bool(capa_input)

print("\nMuy bien, vamos a evaluar tus resultados:")

if edad_person >= 15 and capa_person:
    print("Estas muy bien capacitado, adelante.")
elif edad_person >= 15 and not capa_person:
    print("Tienes la edad, pero te falta la capa de invisibilidad.")
elif edad_person < 15 and capa_person:
    print("Tienes la capa de invisibilidad, pero no cumples la edad suficiente.")
else:
    print("No cumples ningun requisito, espera un poco e intenta de nuevo.")

