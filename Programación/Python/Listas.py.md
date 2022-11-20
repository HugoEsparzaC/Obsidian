# Listas

```python
lista = []

lista.append(5) #agrega elemento al final (valor)

lista.insert(2, 2.5) # agrega elemento (indice, valor)

lista.count(5) #te dice cuantas veces aparece en la lista el valor buscado (valor)

lista.index(3) #Te dice el indice del valor buscado, si hay más de uno, toma el primer (valor)

lista.sort() #ordena de menor a mayor

lista.reverse() #ordena al reves la lista

lista.pop() #elimina el ultimo elemento de la lista

lista.pop(3) #le dices que quieres eliminar el elemento del indice dado (indice)

lista.remove(5) #le dices que quieres eliminar el elemento de la lista (elemento)

print(lista[0 : 5]) #solo imprime los primeros 5 elementos de la lista

print(lista[ : 5]) #muestra desde el indice 0 al 4

print(lista[3 :  ]) #muestra del elemento en el indice 3 en adelante

print(lista[-1]) #muestra el ultimo elemento

print(lista[-5 : -2]) #muestra desde el elemento -5 al -2

print(len(lista)) #muestra el tamaño de la lista
```