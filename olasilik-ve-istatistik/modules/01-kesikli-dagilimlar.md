# Kesikli Olasılık Dağılımları ve Veri Analitiğindeki Rolü

## 1. Veri Analitiğinde Kesikli Dağılımlar Neden Önemlidir?
Veri analitiğinde her veri sürekli (boy, kilo, gelir gibi) değildir. Bir e-ticaret sitesinde sepetini onaylayan/onaylamayan kullanıcılar, bir çağrı merkezine düşen şikayet sayıları veya üretim bandından çıkan kusurlu ürün adetleri **kesikli rassal değişkenlerdir**. 

Bu dağılımları bilmek, iş kararlarında şu soruları yanıtlamamızı sağlar:
* Bir A/B testinde yeni tasarımın dönüşüm artışı şans eseri mi yoksa istatistiksel olarak anlamlı mı?
* Kalite kontrol sürecinde kaç parça incelersek hatalı ürün riskini minimize ederiz?
* Müşteri hizmetlerine saatte kaç çağrı geleceğini tahmin edip kaç personel çalıştırmalıyız?

---

## 2. Temel Kesikli Dağılımlar ve Formülleri

### A. Bernoulli Dağılımı(Temel İkili Karar)
* **Kavram:** Bir deneyde yalnızca iki sonuç (Başarı:p, Başarısızlık:q = 1-p) varsa bu bir Bernoulli denemesidir.
* **Fonksiyon:** f(x) = P(X = x) = p^x (1-p)^{1-x}, x değişkeni sadece 0 veya 1 değerini alabilir
* **Beklenen Değer & Varyans:** 
  E(X) = p
  Var(X) = p(1-p)
* **Veri Analitiği Karşılığı:** Lojistik regresyon modellerinin çıktısı (tıklama/tıklamama, kayıp müşteri / churn analizi).

### B. Binom Dağılımı (Bağımsız Tekrarlar)
* **Kavram:** Başarı olasılığı p olan bağımsız n Bernoulli denemesinde elde edilen başarı sayısıdır X rastgele değişkeni, n ve p parametrelerine sahip bir Binom dağılımı gösterir" 
* **Koşulları:** Deneme sayısı (n) sabit olmalı, denemeler bağımsız olmalı, p olasılığı değişmemelidir.
* **Fonksiyon:** 
  f(x) = P(X = x) = \binom{n}{x} p^x q^{n-x}, x = 0, 1, 
* **Beklenen Değer & Varyans:** 
  E(X) = np
  Var(X) = npq

### C. Çok Terimli (Multinom) Dağılım
* **Kavram:** Sonucun 2'den fazla kategoriye ayrılabildiği durumlar (k kategori). Binom dağılımının genelleştirilmiş halidir.
* **Veri Analitiği Karşılığı (Çok Sınıflı Sınıflandırma):**
  Hedef değişkenin yalnızca iki değil, üç veya daha fazla kategoriden oluştuğu senaryolarda kullanılır.
  * **Örnek 1 (Müşteri Destek / NLP):** Bir e-ticaret sitesine gelen destek mesajlarının makine öğrenmesi modeli tarafından otomatik olarak *"Kargo Problemi"*, *"İade Talebi"*, *"Ürün Hasarı"* veya *"Fatura Sorunu"* şeklinde 4 farklı sınıfa ayrılması.
  * **Örnek 2 (Görüntü İşleme):** Otonom araç kamerasının gördüğü bir nesneyi *"Yaya"*, *"Bisiklet"*, *"Araba"* veya *"Trafik İşareti"* olarak etiketlemesi.
  * Tıpkı araç muayenesindeki 4 farklı sonuç gibi (kusursuz, hafif, ağır, emniyetsiz), model her bir sınıf için ayrı bir olasılık (p1,p2,pk) hesaplar ve toplam olasılık daima 1'e eşittir (p_i = 1).

### D. Geometrik ve Negatif Binom Dağılımı
* **Geometrik Dağılım: İlk başarıyı elde edinceye kadar yapılan deneme sayısı.
  f(x) = p.q^{x-1}
  E(X) =1/p
  Var(X) =q/{p^2}
* **Negatif Binom Dağılımı:** k. başarıyı elde edinceye kadar gereken toplam deneme sayısı.
  f(x) = {x-1}{k-1} p^k (1-p)^{x-k}, 
  E(X) =k/p 
  Var(X) = kq/p^2
* **Veri Analitiği Karşılığı:** Müşterinin ilk alışverişini yapana kadar ziyaret ettiği sayfa sayısı veya bir makinenin arızalanana kadar çalışma döngüsü (Survival / Reliability Analysis).

### E. Hipergeometrik Dağılım (Yerine Koymasız Seçim)
* **Kavram:** Sonlu N büyüklüğündeki kitleden yerine koymaksızın çekilen n birimlik örneklemde istenen a tipindeki nesnelerin sayısı.
### F. Poisson Dağılımı
* **Kavram:** Belirli bir zaman aralığında nadir gerçekleşen olayların sayısı (λ\lambda).
  f(x) = {e^{-\lambda}.lambda^x}/x! 
  E(X) = λ
  Var(X) = λ

###veri Biliminde Nerede Karşımıza Çıkar?
Sunucu / Altyapı Yönetimi: Bulut sunucusuna saniyede gelen mikroservis istekleri veya düşen hata logları.

Dolandırıcılık (Fraud) Tespiti: Kredi kartı işlemlerinde sahte işlem oranı çok düşüktür ($p$ küçüktür, işlem sayısı $n$ ise milyonlardır); bu yüzden sahte işlemler Poisson süreciyle modellenir.
---

## Uygulama Görevi (Case Study)
Bir çağrı merkezinde müşteri temsilcisine gelen çağrılar Poisson dağılımı göstermektedir (λ\lambda = 6.9λ).
1. Temsilcinin bir saatte tam 5 çağrı alma olasılığını hesaplayınız.
2. Aynı süreci Python `scipy.stats` kütüphanesi kullanarak doğrulayınız.