# Programación Orientada a Objetos
```python
class FabricaTelefonos():
    def __init__(self, marca, color):
        self.marca = marca
        self.color = color
        print(f"El objeto {self.marca} ha sido creado")
    def __str__(self):
        return f"El objeto es {self.marca}"
    def __del__(self):
        print(f"El objeto {self.marca} ha sido destruido")

telefono = FabricaTelefonos('Huawei', 'Negro')
print(telefono.marca)
print(telefono)
print(telefono.color)
```
