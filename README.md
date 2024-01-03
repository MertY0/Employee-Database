#include <stdio.h>
#include<string.h>

int sira, sayac = 0;

struct VeriTabani {
    char Isim[50];
    int Yas;
    char Cinsiyet[10];
};

void Giris(struct VeriTabani* Calisanlar) {
    printf("\nEnter Name    : ");
    scanf("%s", Calisanlar->Isim);

    printf("Enter Age     : ");
    scanf("%d", &Calisanlar->Yas);

    printf("Enter Gender  : ");
    scanf("%s", Calisanlar->Cinsiyet);
}

void KisiBulma(struct VeriTabani* Calisanlar) {
    char ad[50];
    int eslesme = 0;

    do {
        printf("Enter Employee's Name: ");
        scanf("%s", ad);

        for (sira = 0; sira <= sayac; sira++) {
            if (strcmp(Calisanlar[sira].Isim, ad) == 0) {
                eslesme = 1;
                break;
            }
        }

        if (!eslesme) {
            printf("No matching employee found. Please enter a valid name.\n");
        }
    } while (!eslesme);
}

void Goruntuleme(struct VeriTabani* Calisanlar) {
    printf("\nName    : %s\n", Calisanlar[sira].Isim);
    printf("Age     : %d\n", Calisanlar[sira].Yas);
    printf("Gender  : %s\n", Calisanlar[sira].Cinsiyet);
}

int main() {
    int islem;
    struct VeriTabani Calisanlar[100];
    printf("Employee Database");
    do {
        printf("\n\nChoose the operation you want to perform");
        printf("\n1. Provide Employee Information\n");
        printf("2. View Employee Information\n");
        printf("0. Exit\n\n");
        scanf("%d", &islem);

        switch (islem) {
        case 1:
            Giris(&Calisanlar[sayac]);
            sayac++;
            break;
        case 2:
            KisiBulma(Calisanlar);
            Goruntuleme(Calisanlar);
            break;
        case 0:
            printf("Exiting...\n");
            break;
        default:
            printf("Invalid Entry\n");
            break;
        }

    } while (islem != 0);

    return 0;
}
