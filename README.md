# marathon
import random

class KelimeTahminOyunu:
    def __init__(self, kelime_listesi):
        self.kelime_listesi = kelime_listesi
        self.secilen_kelime = random.choice(kelime_listesi).upper()
        self.tahmin_edilen_harfler = set()
        self.kalan_hak = 6

    def kelimeyi_goster(self):
        return ''.join([harf if harf in self.tahmin_edilen_harfler else '_' for harf in self.secilen_kelime])

    def tahmin_yap(self, tahmin):
        tahmin = tahmin.upper()

        if tahmin in self.tahmin_edilen_harfler:
            print("Bu harfi zaten tahmin ettiniz.")
            return

        if tahmin not in self.secilen_kelime:
            self.kalan_hak -= 1
            print(f"Yanlış tahmin! Kalan hak: {self.kalan_hak}")
        else:
            print("Doğru tahmin!")

        self.tahmin_edilen_harfler.add(tahmin)

    def oyunu_oyna(self):
        while '_' in self.kelimeyi_goster() and self.kalan_hak > 0:
            print(f"Kelime: {self.kelimeyi_goster()}")
            tahmin = input("Bir harf tahmin edin: ")

            if len(tahmin) != 1 or not tahmin.isalpha():
                print("Geçersiz giriş. Lütfen bir harf girin.")
                continue

            self.tahmin_yap(tahmin)

        if '_' not in self.kelimeyi_goster():
            print(f"Tebrikler! Kelimeyi doğru tahmin ettiniz. Kelime: {self.secilen_kelime}")
        else:
            print(f"Üzgünüm, kelimeyi tahmin edemediniz. Doğru kelime: {self.secilen_kelime}")

# Örnek kullanım:
kelime_listesi = ["yazılımtoplulugu", "esma", "ayse", "fatma"]
oyun = KelimeTahminOyunu(kelime_listesi)
oyun.oyunu_oyna()

#esmanur özdemir
