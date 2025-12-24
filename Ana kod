// Recep, Koçak, Memnuş, Ödev

#include <stdio.h>
#include <string.h> //strcmp ve strcpy fonks. için kullanılıyor

//struct yapısı
struct oyuncular {
    char ad[30];
    char soyad[30];
    int oynanan_mac_sayisi;
    int hatali_pas;
    int isabetli_pas;
};

void ekle(struct oyuncular takim[], int *mevcut_sayi, char ad[], char soyad[], int h_pas, int i_pas) {
    int bulundu = 0; // daha önce bu oyuncu bulundu mu bulunmadı mı (0 bulunamadı, 1 bulundu)


    for (int i = 0; i < *mevcut_sayi; i++) //kişi sayısı kadar tekrar ettirir

        {


        if (strcmp(takim[i].ad, ad) == 0 && strcmp(takim[i].soyad, soyad) == 0) //isim karşılaştırma

        {
            takim[i].oynanan_mac_sayisi++;
            takim[i].hatali_pas += h_pas;
            takim[i].isabetli_pas += i_pas;
            bulundu = 1; //buldum
            break;
        }
    }


    if (bulundu == 0 && *mevcut_sayi < 22) //listede bulundı mu ve kadro yani 22 kişi doldu mu iksiide hayır ise gir

        {
        strcpy(takim[*mevcut_sayi].ad, ad);
        strcpy(takim[*mevcut_sayi].soyad, soyad);
        takim[*mevcut_sayi].oynanan_mac_sayisi = 1;
        takim[*mevcut_sayi].hatali_pas = h_pas;
        takim[*mevcut_sayi].isabetli_pas = i_pas;
        (*mevcut_sayi)++;
    }
}

// b) Yazdir fonksiyonu: toplam.txt oluşturur
void yazdir (struct oyuncular takim[], int mevcut_sayi) {
    FILE *dosya = fopen("toplam.txt", "w");
    if (dosya == NULL) return;
    for (int i = 0; i < mevcut_sayi; i++) {
        fprintf(dosya, "%s %s %d %d %d\n",
                takim[i].ad, takim[i].soyad,
                takim[i].oynanan_mac_sayisi,
                takim[i].hatali_pas,
                takim[i].isabetli_pas);
    }
    fclose(dosya);
}

int main() {
    struct oyuncular takim[22];
    int mevcut_oyuncu_sayisi = 0;
    char ad[30], soyad[30];
    int h_pas, i_pas;

    FILE *fp = fopen("../paslar.txt", "r"); // CLion için yolu bu şekilde dene
    if (fp == NULL) fp = fopen("paslar.txt", "r"); // Alternatif yol


    while (fscanf(fp, "%s %s %d %d", ad, soyad, &h_pas, &i_pas) != EOF) {
        ekle(takim, &mevcut_oyuncu_sayisi, ad, soyad, h_pas, i_pas);
    }
    fclose(fp);

    yazdir(takim, mevcut_oyuncu_sayisi);
    return 0;
}
