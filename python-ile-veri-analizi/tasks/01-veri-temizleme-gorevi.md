# Uygulama Görevi: E-Ticaret Müşteri Verisi Uçtan Uca Analiz ve Temizlik

## 1. Senaryo
Bir e-ticaret platformunda son 1 yılda alışveriş yapan müşterilere ait 10.000 satırlık ham işlem verisi (`musteri_islemleri.csv`) elinize ulaştı. 

Veri tabanından çekilen bu ham veride bazı teknik problemler ve analize engel olan tutarsızlıklar bulunuyor:
* `harcama_tutari` sütunu para birimi simgesi ve virgül içerdiği için metin (string) olarak kaydedilmiş.
* `yas` sütununda sisteme giriş yapmamış kullanıcılardan ötürü %8 oranında eksik değer (NaN) var.
* `siparis_adedi` sütununda negatif veya aşırı uç (outlier) hatalı kayıtlar mevcut.
* Yönetim, müşterilerin `uyelik_tipi`ne (Standart, Premium, VIP) göre harcama alışkanlıklarını raporlamanızı istiyor.

---

## 2. Beklenen Analiz ve Kodlama Adımları

### Adım 1: Veri Tipi Dönüşümü ve Temizleme
`harcama_tutari` sütunundaki metinsel ifadeleri temizleyip (örn: "₺", boşluk ve virgül formatını düzelterek) sütunu sayısal (`float`) tipe çeviren Python kodunu yazınız.

### Adım 2: Eksik Veri Yönetimi ve İstatistiksel Karar
`yas` sütunundaki eksik değerleri inceleyiniz:
* Verinin çarpıklığını (skewness) veya medyan/ortalama farkını kontrol ederek eksik değerleri hangi merkezi eğilim ölçüsüyle doldurmanız gerektiğini gerekçesiyle açıklayınız.
* Seçtiğiniz yöntemi Pandas ile uygulayınız.

### Adım 3: Aykırı Değer (Outlier) Filtreleme
`siparis_adedi` değişkeninde 0'dan küçük değerleri ve IQR (Çeyrekler Açıklığı) yöntemine göre belirlenen üst sınırın üzerindeki bariz sistemsel hataları filtreleyen sorguyu oluşturunuz.

### Adım 4: İş Kararı ve Segmentasyon (Groupby)
Temizlenmiş veri üzerinde müşterileri `uyelik_tipi`ne göre gruplayınız:
* Her grubun müşteri sayısını (`count`), ortalama harcama tutarını (`mean`) ve toplam ciroya katkısını (`sum`) tek bir `groupby` tablosunda özetleyiniz.
* Bu segmentasyon sonucuna göre şirket yönetimine 1-2 cümlelik pazarlama tavsiyesi yazınız.

---

## AI Mentorship & Skills
> **AI Skill Rolü: `data-analyst-mentor`**  
> Bu analizi yaparken takıldığınız yerlerde AI Mentörünüze danışabilirsiniz:
> * Veri temizleme fonksiyonlarında (`replace`, `to_numeric`, `fillna`) syntax hatası alırsanız hatayı danışabilirsiniz.
> * IQR formülü veya eksik veri stratejisinde kararsız kalırsanız mentörünüz size doğrudan kodu vermek yerine istatistiksel sezgiyi hatırlatacak sorular soracaktır.