# SPSS'in Analitik Gücü: Anketin Ötesi ve Hipotez Testlerinin Sayısal Dünyası

## 1. SPSS Sadece Bir "Anket Aracı" mıdır?
SPSS çoğu zaman yalnızca anket sonuçlarını girmeye yarayan bir program gibi algılanır; oysa bu, aracın kapasitesinin çok küçük bir kısmıdır.

SPSS; sensör verileri, finansal işlemler, fabrika üretim ölçümleri, müşteri harcamaları veya hasta tahlil sonuçları gibi her türlü yapılandırılmış veriyi işleyen kapsamlı bir istatistik yazılımıdır. 
* Bize kazandırdığı asıl yetkinlik veri girmek değil; **büyük veri yığınları üzerinden bilimsel karar verme süreçlerini otomatikleştirmektir.**

---

## 2. Geçen Dönem Gördüğümüz Hipotez Testleriyle Bağlantısı Nedir?

Geçen dönem teorik derslerde öğrendiğimiz formülleri hatırlayalım:
* Formülle serbestlik derecesi hesaplamak,
* Kareler toplamı ve varyans formüllerini elle işletmek,
* İstatistik tablolarından kritik değer (t tablosu, z tablosu, F tablosu) aramak,
* "Hesaplanan değer tablo değerinden büyükse H0 reddedilir" kuralını işletmek.

**SPSS'in Yaptığı İş:**
Tüm bu teorik adımları arka planda mikro saniyeler içinde çalıştırır. Bizi binlerce satırlık veride elle işlem yapma yükünden kurtarır ve doğrudan **p-değerini (Sig.)** üretir. 

Bizim teorik olarak bildiğimiz karar kuralı SPSS ekranında şu tek satıra indirgenir:
* **p < 0.05:** Geçen dönemki mantıkla "Hesaplanan değer kritik bölgeye düştü, H0 reddedildi, fark anlamlı."
* **p >= 0.05:** "Hesaplanan değer kabul bölgesinde kaldı, H0 reddedilemez, anlamlı bir fark yok."

---

## 3. Hipotez Testi Mantığının SPSS'teki Karşılığı

| Teoride Öğrendiğimiz Test | SPSS'teki Yeri | Hangi Veri Tipinde Kullanılır? (Anket Dışı Örnekler) |
| :--- | :--- | :--- |
| **Bağımsız İki Örneklem t-Testi** | `Analyze -> Compare Means -> Independent-Samples T Test` | İki farklı makineden çıkan parçaların dayanıklılık ortalamaları farklı mı? |
| **Eşleştirilmiş (Paired) t-Testi** | `Analyze -> Compare Means -> Paired-Samples T Test` | Bir yazılım güncellemesinden önce ve sonra sunucu yanıt süreleri değişti mi? |
| **Tek Yönlü ANOVA** | `Analyze -> Compare Means -> One-Way ANOVA` | Üç farklı hammadde tedarikçisinden gelen ürünlerin kalite puanları eşit mi? |
| **Ki-Kare Testi** | `Analyze -> Descriptive Statistics -> Crosstabs` | Hatalı üretilen parçaların üretim vardiyalarıyla (sabah/akşam) bir bağımlılığı var mı? |
| **Regresyon Analizi** | `Analyze -> Regression -> Linear` | Reklam harcamaları ve fiyat indirimleri satış adedini ne kadar tahmin ediyor? |

---

## 4. SPSS Bize Ne Kazandırır? (İş Dünyasındaki Değeri)

1. **Ön Koşul / Varsayım Disiplini:** Veriye körü körüne test uygulamamayı öğretir. Normallik (Shapiro-Wilk, Kolmogorov-Smirnov) ve varyans homojenliği (Levene Testi) gibi istatistiksel şartları kontrol etme refleksi kazandırır.
2. **Objektif Karar Alma:** "Bence bu yöntem daha iyi" demek yerine, verinin arkasındaki istatistiksel anlamlılığı (p-değeri ve etki büyüklüğü) göstererek kanıta dayalı rapor hazırlama gücü verir.
3. **Akademik ve Sektörel Raporlama Standardı:** Çıktı tabloları (t-değeri, serbestlik derecesi df, p-değeri); Ar-Ge merkezlerinde, kalite kontrol departmanlarında ve pazar araştırmalarında evrensel kabul gören standart formatı sağlar.