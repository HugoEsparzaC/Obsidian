```python
diccionario = {llave0:  valor0, llave1: valor1}
diccionario2 = {llave2: valor2, llave3: valor3}

print(diccionario.keys()) #muestra solo las llaves

print(diccionario.values()) #muestra solo los valores

print(diccionario[llave0]) #muestra el valor0

diccionario[llave2] = valor2  #agrega esa llave y valor al diccionario

diccionario[llave0] = valor00 #reemplaza el valor de la llave

diccionario.pop(llave1)

diccionario.clear()

diccionario.get(llave0)

diccionario.setdefault(llave2, valor2)

diccionario.update(diccionario2) #se le agregan los datos del diccionario 2 al 1
```