#include <stdio.h>

int main() {
    int n;

    printf("Entrer une valeur n : ");
    scanf("%d", &n);

    int tableau[n+1];

    // Initialisation : on suppose que tous les nombres sont premiers
    for (int i = 0; i <= n; i++) {
        tableau[i] = 1;
    }

    // 0 et 1 ne sont pas premiers
    tableau[0] = 0;
    tableau[1] = 0;

    printf("\n--- Début du crible ---\n");

    for (int i = 2; i * i <= n; i++) {
        if (tableau[i] == 1) {
            printf("\n=> %d est premier. On élimine ses multiples : ", i);

            for (int j = i * i; j <= n; j += i) {
                if (tableau[j] == 1) {
                    printf("%d ", j);
                }
                tableau[j] = 0;
            }
            printf("\n");
        }
    }

    // Affichage des nombres premiers finaux
    printf("\n--- Nombres premiers jusqu'à %d ---\n", n);
    for (int i = 2; i <= n; i++) {
        if (tableau[i] == 1) {
            printf("%d ", i);
        }
    }

    printf("\n");
    return 0;
}
