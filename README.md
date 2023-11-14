#include <stdio.h>

#define MAX_CONTATOS 100

// Definindo a estrutura para um contato
struct Contato {
    char nome[100];
    char telefone[20];
};

// Função para exibir o menu principal
void exibirMenu() {
    printf("\nMenu Principal:\n");
    printf("1. Adicionar Contato\n");
    printf("2. Visualizar Contatos\n");
    printf("3. Sair\n");
    printf("Escolha uma opção: ");
}

int main() {
    struct Contato contatos[MAX_CONTATOS];
    int opcao;
    int numContatos = 0;

    do {
        exibirMenu();
        scanf("%d", &opcao);

        switch (opcao) {
            case 1:
                if (numContatos < MAX_CONTATOS) {
                    printf("\nNome do Contato: ");
                    scanf(" %[^\n]", contatos[numContatos].nome); // Ler toda a linha, incluindo espaços
                    printf("Telefone do Contato: ");
                    scanf(" %[^\n]", contatos[numContatos].telefone); // Ler toda a linha, incluindo espaços
                    numContatos++;
                    printf("Contato adicionado com sucesso!\n");
                } else {
                    printf("Limite máximo de contatos atingido!\n");
                }
                break;
            case 2:
                printf("\nLista de Contatos:\n");
                for (int i = 0; i < numContatos; i++) {
                    printf("Nome: %s, Telefone: %s\n", contatos[i].nome, contatos[i].telefone);
                }
                break;
            case 3:
                printf("Saindo do programa. Até logo!\n");
                break;
            default:
                printf("Opção inválida. Tente novamente.\n");
        }

    } while (opcao != 3);

    return 0;
}
