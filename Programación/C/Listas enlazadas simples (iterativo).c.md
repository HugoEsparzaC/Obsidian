# Listas enlazadas simples (iterativo)

## Librerias
```c
#include <stdio.h>
#include <stdlib.h>
```
## Struct nodo
```c
struct nodo{
    int info;
    struct nodo *sig;
};
typedef struct nodo nodo_t;
```
## nodo_t *crea_nodo();
```c
nodo_t *crea_nodo(){
    nodo_t *nodo = NULL;
    nodo = (nodo_t*)malloc(sizeof(nodo_t));
    if(nodo == NULL){
        printf("Error: no hay memoria suficiente");
        exit(EXIT_FAILURE);
    }
    nodo->info = 0;
    nodo->sig = NULL;
    return nodo;
}
```
## Menu
```c
int selecciona_opcion(){
    puts("Selecciona una opcion");
    puts("0. Salir");
    puts("1. Insertar inicio");
    puts("2. Insertar al final");
    puts("3. Eliminar al inicio");
    puts("4. Eliminar al final");
    puts("5. Imprimir toda la lista");
    puts("6. Eliminar nodo arbitrario");
    puts("7. Eliminar/Liberar toda la lista");
    puts("8. Buscar dato");
    int opcion;
    scanf("%d", &opcion);
    return opcion;
}
```
## void insertar inicio(nodo_t **, int);
```c
void insertar_inicio(nodo_t **cab, int dato){
    nodo_t *nodo = crea_nodo();
    nodo->info = dato;
    nodo->sig = *cab;
    *cab = nodo;
}
```
## void insertar_final(nodo_t **, int);
```c
void insertar_final(nodo_t **cab, int dato){
    nodo_t *nodo = crea_nodo();
    nodo->info = dato;
    if(*cab == NULL){
        *cab = nodo;
    }
    else{
        nodo_t *ultimo = *cab;
        while(ultimo->sig != NULL){
            ultimo = ultimo->sig;
        }
        ultimo->sig = nodo;
    }
}
```
## void imprimir_lista(nodo_t *);
```c
void imprimir_lista(const nodo_t *cab){
    const nodo_t *it = cab;
    while(it != NULL){
        printf("%d ", it->info);
        it = it->sig;
    }
    printf("\n");
}
```
## void eliminar_inicio(nodo_t **);
```c
void eliminar_inicio(nodo_t **cab){
    nodo_t *tmp;
    if(*cab != NULL){
        tmp = *cab;
        *cab = (*cab)->sig;
        free(tmp);
    }
}
```
## void eliminar_final(nodo_t **);
```c
void eliminar_final(nodo_t **cab){
    if(*cab == NULL){
        return;
    }
    else if((*cab)->sig == NULL){
        nodo_t *tmp = *cab;
        free(tmp);
        *cab = NULL;
    }
    else{
        nodo_t *ultimo = *cab;
        nodo_t *penultimo = NULL;
        while(ultimo->sig != NULL){
            penultimo = ultimo;
            ultimo = ultimo->sig;
        }
        free(ultimo);
        penultimo->sig = NULL;
    }
}
```
## void elimina_nodo(nodo_t **, int);
```c
void elimina_nodo(nodo_t **cab, int x){
    if(*cab == NULL){
        return;
    }
    else if((*cab)->info == x){
        nodo_t *tmp = *cab;
        *cab = (*cab)->sig;
        free(tmp);
        return;
    }
    else{
        nodo_t *prev = *cab, *it = (*cab)->sig;
        while(it != NULL && it->info != x){
            prev = it;
            it = it->sig;
        }
        if(it != NULL){
            prev->sig = it->sig;
            free(it);
        }
    }
}
```
## void liberar_lista(nodo_t **);
```c
void liberar_lista(nodo_t **cab){
    nodo_t *it = *cab;
    while(it != NULL){
        nodo_t *tmp = it;
        it = it->sig;
        free(tmp);
    }
    *cab = NULL;
}
```
## nodo_t *buscar_dato(const nodo_t *, int);
```c
nodo_t *buscar_dato(const nodo_t *cab, int dato){
    for(const nodo_t *it = cab; it != NULL; it = it->sig){
        if(it->info == dato){
            return (nodo_t *)it;
        }
    }
    return NULL;
}
```
## int main()
```c
int main(){
    nodo_t *lista = NULL;
    int opcion = 0, num = 0;
    do{
        opcion = selecciona_opcion();
        switch(opcion){
            case 1: printf("Valor del numero: ");
                scanf("%d", &num);
                insertar_inicio(&lista, num);
                break;
            case 2: printf("Valor del numero: ");
                scanf("%d", &num);
                insertar_final(&lista, num);
                break;
            case 3: eliminar_inicio(&lista);
                break;
            case 4: eliminar_final(&lista);
                break;
            case 5: imprimir_lista(lista);
                break;
            case 6: printf("Valor del numero: ");
                scanf("%d", &num);
                elimina_nodo(&lista, num);
                break;
            case 7: liberar_lista(&lista);
                break;
            case 8: printf("Valor del numero: ");
                scanf("%d", &num);
                printf("%p\n", buscar_dato(lista, num));
                break;
            default: puts("Opcion no valida");
                break;
        }
    }while(opcion != 0);
    liberar_lista(&lista);
    return 0;
}
```
## Codigo completo
```c
#include <stdio.h>
#include <stdlib.h>
struct nodo{
    int info;
    struct nodo *sig;
};
typedef struct nodo nodo_t;
int selecciona_opcion();
void insertar_inicio(nodo_t **, int);
void insertar_final(nodo_t **, int);
void imprimir_lista(const nodo_t *);
void eliminar_inicio(nodo_t **);
void eliminar_final(nodo_t **);
void elimina_nodo(nodo_t **, int);
nodo_t *buscar_dato(const nodo_t *, int);
void liberar_lista(nodo_t **);
nodo_t *crea_nodo();
int main(){
    nodo_t *lista = NULL;
    int opcion = 0, num = 0;
    do{
        opcion = selecciona_opcion();
        switch(opcion){
            case 1: printf("Valor del numero: ");
                scanf("%d", &num);
                insertar_inicio(&lista, num);
                break;
            case 2: printf("Valor del numero: ");
                scanf("%d", &num);
                insertar_final(&lista, num);
                break;
            case 3: eliminar_inicio(&lista);
                break;
            case 4: eliminar_final(&lista);
                break;
            case 5: imprimir_lista(lista);
                break;
            case 6: printf("Valor del numero: ");
                scanf("%d", &num);
                elimina_nodo(&lista, num);
                break;
            case 7: liberar_lista(&lista);
                break;
            case 8: printf("Valor del numero: ");
                scanf("%d", &num);
                printf("%p\n", buscar_dato(lista, num));
                break;
            default: puts("Opcion no valida");
                break;
        }
    }while(opcion != 0);
    liberar_lista(&lista);
    return 0;
}

nodo_t *crea_nodo(){
    nodo_t *nodo = NULL;
    nodo = (nodo_t*)malloc(sizeof(nodo_t));
    if(nodo == NULL){
        printf("Error: no hay memoria suficiente");
        exit(EXIT_FAILURE);
    }
    nodo->info = 0;
    nodo->sig = NULL;
    return nodo;
}

int selecciona_opcion(){
    puts("Selecciona una opcion");
    puts("0. Salir");
    puts("1. Insertar inicio");
    puts("2. Insertar al final");
    puts("3. Eliminar al inicio");
    puts("4. Eliminar al final");
    puts("5. Imprimir toda la lista");
    puts("6. Eliminar nodo arbitrario");
    puts("7. Eliminar/Liberar toda la lista");
    puts("8. Buscar dato");
    int opcion;
    scanf("%d", &opcion);
    return opcion;
}

void insertar_inicio(nodo_t **cab, int dato){
    nodo_t *nodo = crea_nodo();
    nodo->info = dato;
    nodo->sig = *cab;
    *cab = nodo;
}

void insertar_final(nodo_t **cab, int dato){
    nodo_t *nodo = crea_nodo();
    nodo->info = dato;
    if(*cab == NULL){
        *cab = nodo;
    }
    else{
        nodo_t *ultimo = *cab;
        while(ultimo->sig != NULL){
            ultimo = ultimo->sig;
        }
        ultimo->sig = nodo;
    }
}

void imprimir_lista(const nodo_t *cab){
    const nodo_t *it = cab;
    while(it != NULL){
        printf("%d ", it->info);
        it = it->sig;
    }
    printf("\n");
}

void eliminar_inicio(nodo_t **cab){
    nodo_t *tmp;
    if(*cab != NULL){
        tmp = *cab;
        *cab = (*cab)->sig;
        free(tmp);
    }
}

void liberar_lista(nodo_t **cab){
    nodo_t *it = *cab;
    while(it != NULL){
        nodo_t *tmp = it;
        it = it->sig;
        free(tmp);
    }
    *cab = NULL;
}

void eliminar_final(nodo_t **cab){
    if(*cab == NULL){
        return;
    }
    else if((*cab)->sig == NULL){
        nodo_t *tmp = *cab;
        free(tmp);
        *cab = NULL;
    }
    else{
        nodo_t *ultimo = *cab;
        nodo_t *penultimo = NULL;
        while(ultimo->sig != NULL){
            penultimo = ultimo;
            ultimo = ultimo->sig;
        }
        free(ultimo);
        penultimo->sig = NULL;
    }
}

void elimina_nodo(nodo_t **cab, int x){
    if(*cab == NULL){
        return;
    }
    else if((*cab)->info == x){
        nodo_t *tmp = *cab;
        *cab = (*cab)->sig;
        free(tmp);
        return;
    }
    else{
        nodo_t *prev = *cab, *it = (*cab)->sig;
        while(it != NULL && it->info != x){
            prev = it;
            it = it->sig;
        }
        if(it != NULL){
            prev->sig = it->sig;
            free(it);
        }
    }
}

nodo_t *buscar_dato(const nodo_t *cab, int dato){
    for(const nodo_t *it = cab; it != NULL; it = it->sig){
        if(it->info == dato){
            return (nodo_t *)it;
        }
    }
    return NULL;
}
```
