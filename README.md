# 💰 Tycoon İmparatorluğu

Tarayıcıda oynanan, tek dosyalık bir tıklama (clicker) ve tycoon oyunu. Bir limonata standıyla başla, işletmeler satın al, yükseltmeler aç ve galaktik bir imparatorluk kur.

Kurulum gerektirmez, bağımlılık yoktur. Tek bir HTML dosyasıdır.

## Özellikler

- **Tıklayarak kazan:** Büyük altın jetona dokun, her tıkta para kazan. Klavyede Boşluk veya Enter ile de çalışır.
- **9 işletme:** Limonata Standı’ndan Zaman Makinesi’ne kadar, her biri otomatik gelir üretir.
- **Adet bonusları:** Bir işletmeden 10, 25, 50, 100, 150, 200, 300, 400, 500, 750 ve 1000 adede ulaşınca o işletmenin geliri ×2 olur.
- **Alım miktarı seçimi:** ×1, ×10, ×100 veya Maks.
- **Yükseltmeler:** 6 tık gücü yükseltmesi ve 6 şirket geneli gelir yükseltmesi.
- **Altın jeton etkinliği:** Ekranda rastgele beliren jetona tıklarsan ya bol miktarda para ya da 20 saniyelik ×7 “Çılgınlık” kazanırsın.
- **Yeniden doğuş (prestij):** Her şeyi sıfırla, hisse kazan. Her hisse tüm gelire kalıcı +%10 ekler.
- **19 başarım:** Her başarım tüm gelire +%1 ekler.
- **Rütbeler:** Çırak’tan Galaktik Tycoon’a kadar toplam kazancına göre yükselirsin.
- **Çevrimdışı kazanç:** Oyundan ayrıldığında gelirinin %50’sini (en fazla 8 saat) kazanmaya devam edersin.
- **Otomatik kayıt:** İlerleme her 5 saniyede tarayıcıya kaydedilir.
- **Açık ve koyu tema:** Sağ üstteki düğmeyle değiştirilir, sistem temasını da takip eder.
- **Mobil uyumlu:** Telefonda ve masaüstünde çalışır.

## Nasıl oynanır?

1. Jetona tıklayarak ilk paranı kazan.
2. Parayla ilk işletmeni (Limonata Standı) al, gelir otomatik akmaya başlasın.
3. Daha fazla işletme ve yükseltme satın alarak geliri büyüt.
4. Altın jeton belirince hızla tıkla.
5. Yeniden doğuş açıldığında hisse kazan ve çok daha hızlı yeniden başla.

## Yerelde çalıştırma

Dosyayı indir ve tarayıcıda aç. Başka bir şey gerekmez.

```bash
git clone https://github.com/KULLANICI_ADI/REPO_ADI.git
cd REPO_ADI
# index.html dosyasını tarayıcıda aç
```

## GitHub Pages ile yayınlama

1. Oyun dosyasının adını `index.html` yap ve repoya yükle.
2. Repoda **Settings → Pages** bölümüne git.
3. **Source** olarak **Deploy from a branch** seç, branch olarak `main` ve klasör olarak `/ (root)` seç, **Save**’e bas.
4. Birkaç dakika sonra oyun şu adreste yayında olur: `https://KULLANICI_ADI.github.io/REPO_ADI/`

## Özelleştirme

Oyunun tüm dengesi `index.html` içindeki script bölümünün başındaki dizilerde durur:

| Dizi | Ne işe yarar? | Satır biçimi |
| --- | --- | --- |
| `B` | İşletmeler | `[ad, emoji, başlangıç maliyeti, saniyelik gelir]` |
| `K` | Tık gücü yükseltmeleri | `[ad, emoji, maliyet, çarpan]` |
| `G` | Şirket geneli yükseltmeler | `[ad, emoji, maliyet, gelir bonusu]` |
| `MS` | Adet bonusu eşikleri | Sayı listesi |
| `RK` | Rütbeler | `[gereken toplam kazanç, ad]` |

Yeni bir işletme eklemek için `B` dizisine bir satır eklemen yeterli. Arayüz ve kayıt sistemi otomatik uyum sağlar.

## Oyun matematiği

- Bir işletmenin her yeni adedi bir öncekinden %15 daha pahalıdır (maliyet çarpanı 1,15).
- Toplam gelir çarpanı: `(1 + şirket geneli bonusları) × (1 + 0,10 × hisse) × (1 + 0,01 × başarım sayısı)`, çılgınlık sırasında ayrıca ×7.
- Tık değeri: `tık çarpanı × gelir çarpanı + saniyelik gelirin %1’i × alınan tık yükseltmesi sayısı`.
- Yeniden doğuşta kazanılan hisse: `floor(√(bu turdaki kazanç / 100 milyon))`.

## Teknik notlar

- Saf HTML, CSS ve JavaScript. Framework ve harici kütüphane yoktur.
- Kayıt `localStorage` içinde `tycoon_v1` anahtarıyla tutulur. Tarayıcı verisini temizlemek ilerlemeyi siler.
- Oyunu sıfırlamak için arayüzdeki **Sıfırla** düğmesini kullan.

## Yol haritası

- [ ] Dünya geneli skor tablosu (harici bir sunucu gerektirir, örneğin Firebase veya Supabase)
- [ ] Ses efektleri
- [ ] Yeni işletmeler ve yükseltmeler
- [ ] Ek temalar

## Lisans

Lisansı kendin seç ve repoya `LICENSE` dosyası olarak ekle. Emin değilsen MIT yaygın bir tercihtir.
