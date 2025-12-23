#include <stdio.h>
struct ogrenci {
    char ad;
    char soyad;
    float ort;
};
int main() {
    struct ogrenci sinif[10] ;
    struct ogrenci gecici;
    for (int i = 0; i < 10; i++) {
        printf("ad, soyad, ortalama girin");
        scanf("%s %s %f", &sinif[i].ad, &sinif[i].soyad, &sinif[i].ort);
    }
        // Hocam burda yapay zekadan yardım aldım
        for(int i = 0; i < 9; i++) {
            for(int j = 0; j < 9 - i; j++) {

                if(sinif[j].ort < sinif[j+1].ort) {
                    gecici = sinif[j];
                    sinif[j] = sinif[j+1];
                    sinif[j+1] = gecici;
                }
            }
        }

        printf("\n%-15s %-15s %-10s\n", "Ad", "Soyad", "Ort");
        printf("--------------------------------------------\n");
        for(int i = 0; i < 10; i++) {
            printf("%-15c %-15c %-10.2f\n",sinif[i].ad, sinif[i].soyad, sinif[i].ort);
        }

        return 0;
}
