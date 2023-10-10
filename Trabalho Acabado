#include <stdio.h>
#include <stdlib.h>
#include <conio.h>

typedef struct no
{
    int valor;
    struct no *proximo;
} No;

typedef struct{
    No *inicio;
    No *fim;
    int tam;
}Lista;

void criar_lista(Lista *lista){
    lista->inicio = NULL;
    lista->fim = NULL;
    lista->tam = 0;
}

// aqui vamos colocar elementos no inicio da lista

void inserir_inicio(Lista *lista, int num)
{
    No *novo = malloc(sizeof(No));

    if (novo)
    {
        novo->valor = num;
        novo->proximo = lista->inicio; // aqui o nosso NO vai apontar para o começo da nossa lista
        lista->inicio = novo; // aqui o nosso inicio vai apontar para o nosso novo NO
        if(lista->fim == NULL)
            lista->fim = novo;
        lista->fim->proximo = lista->inicio;
        lista->tam++;
    }
    else{
        printf("Erro ao alocar memoria!\n");
    }
}

// aqui vamos colocar elementos no final da lista

void inserir_fim(Lista *lista, int num)
{
    No *aux, *novo = malloc(sizeof(No));

    if (novo)
    {
        novo->valor = num;
        

        // é o primeiro?
        if (lista-> inicio == NULL){
            lista-> inicio = novo;
            lista-> fim = novo;
            lista-> fim->proximo = lista->inicio;
        }
        else
        {
            lista->fim->proximo = novo;
            lista->fim = novo;
            lista->fim->proximo = lista->inicio;
        }
    }
    else
    {
        printf("Erro ao alocar na memoria!\n");
    }
}

No* remover(Lista *lista, int num){

    No *aux,*remover = NULL;

    if(lista->inicio){
        if(lista->inicio == lista->fim && lista-> inicio->valor == num){
            remover = lista->inicio;
            lista-> inicio = NULL;
            lista-> fim = NULL;
            lista-> tam--;
        }
        else if(lista-> inicio-> valor == num){
            remover = lista->inicio;
            lista->inicio = remover->proximo;
            lista-> fim->proximo = lista->inicio;
            lista-> tam--;
        }
        else{
            aux = lista-> inicio;
            while(aux->proximo != lista-> inicio && aux->proximo->valor != num)
                aux = aux->proximo;
            if(aux-> proximo-> valor == num){
                if(lista->fim == aux-> proximo){
                    remover = aux->proximo;
                    aux->proximo = remover-> proximo;
                    lista->fim = aux;
                }
                else{
                    remover = aux-> proximo;
                    aux->proximo = remover-> proximo;
                }
                lista-> tam--;
            }
        }
    }
   
}
    
No* buscar(Lista *lista, int num){

    No *aux = lista->inicio;

    if(aux){
        do{
            if(aux->valor == num)
                return aux;
            aux = aux-> proximo;
        }while(aux != lista->inicio);
    }
    return NULL;
}


void imprimir(Lista lista){
    No *no = lista.inicio;
    printf("\n\tLista tam %d: ", lista.tam);
    if(no){
        do{
            printf("%d ", no->valor);
            no = no->proximo;
        }while(no != lista.inicio);
        printf("\nInicio: %d", no->valor);
    }
    
    printf("\n\n");
}

int main(){
    int opc,valor;
    Lista lista;
    No *removido;
    criar_lista(&lista);




    
    do{
        printf("|------------------------------------------------|\n");
        printf("|---1-Inserir um elemento no inicio--------------|\n");
        printf("|---2-Inserir um elemento no final da lista------|\n");
        printf("|---3-Remover um elemento com valor especifico---|\n");
        printf("|---4-Buscar elemento----------------------------|\n");
        printf("|---5-Exibir todos os elementos da lista---------|\n");
        printf("|------------------------------------------------|\n");
        scanf("%d", &opc);
        switch (opc)
        {
        case 1:
            printf("Digite um valor: ");
            scanf("%d" , &valor);
            inserir_inicio(&lista, valor);
            break;

        case 2:
            printf("Digite um valor:  ");
            scanf("%d", &valor);
            inserir_fim(&lista, valor);
            break;

        case 3:
            printf("Digite o valor para ser removido:  ");
            scanf("%d", &valor);
            removido = remover(&lista, valor);
            if(removido){
                printf("elemento a ser removido: %d\n", removido->valor);
                free(remover);
            }
            else{
                printf("elemento nao encontrado!\n");
            }
            break;

        case 4:
            printf("Digite o valor para ser buscado:  ");
            scanf("%d", &valor);
            removido = buscar(&lista, valor);
            if(removido){
                printf("elemento a ser buscado: %d\n", removido->valor);
            }
            else{
                printf("elemento nao encontrado!\n");
            }

            break;

        case 5:
            imprimir(lista);
            break;

        default:
            if (opc != 0)
                printf("opcao invalida!\n");
        }
    } while (opc != 0);
    return 0;
}
