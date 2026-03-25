%%writefile main.c
#include <stdio.h>
#include <ctype.h> // Para toupper
#include <string.h> // Para manipular strings

int main() {
    char nomes[3][30];    // Vetor de strings (Matriz de caracteres)
    float notas[3][2];    // Matriz de notas: 3 alunos, 2 notas cada
    float medias[3];      // Vetor para armazenar as médias
    int i, j;

    printf("--- SISTEMA DE GESTAO ESCOLAR ---\n\n");

    // 1. Entrada de dados e Processamento com FOR
    for (i = 0; i < 3; i++) {
        printf("Digite o sobrenome do aluno %d: ", i + 1);
        scanf("%s", nomes[i]);

        // Converter sobrenome para MAIÚSCULAS usando ctype.h
        for (j = 0; nomes[i][j] != '\0'; j++) {
            nomes[i][j] = toupper(nomes[i][j]);
        }

        // Entrada das notas para a Matriz
        float soma = 0;
        for (j = 0; j < 2; j++) {
            printf("Digite a nota %d do aluno %s: ", j + 1, nomes[i]);
            scanf("%f", &notas[i][j]);
            soma += notas[i][j]; // Acumulador
        }
        medias[i] = soma / 2; // Calcula a média do aluno atual
        printf("\n");
    }

    // 2. Saída de dados (Relatório Final)
    printf("---------- RELATORIO FINAL ----------\n");
    printf("ALUNO\t\tNOTA 1\tNOTA 2\tMEDIA\n");
    printf("-------------------------------------\n");

    for (i = 0; i < 3; i++) {
        // Exibe o nome, as notas da matriz e a média calculada
        printf("%s\t\t%.1f\t%.1f\t%.1f\n", nomes[i], notas[i][0], notas[i][1], medias[i]);
    }

    return 0;
}
