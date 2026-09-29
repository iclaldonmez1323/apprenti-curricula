# Modern Veri Analitiğinin Kalbi: Python'ın Gücü ve Pandas Ekosistemi

## 1. Neden Python? (SPSS ve Excel'in Ötesi)
Geleneksel araçlar (Excel, menü bazlı SPSS vb.) küçük ölçekli anketler ve hızlı tablolar için kullanışlı olsa da büyük veri çağında yetersiz kalmaktadır. 

Python'ı veri dünyasının lideri yapan temel avantajlar:
* **Ölçeklenebilirlik:** Excel'in 1 milyon satır sınırının veya SPSS'in bellek kısıtlamalarının aksine; yüz binlerce veya milyonlarca satırlık veriyi takılmadan işleyebilir.
* **Uçtan Uca Otomasyon:** Her ay tekrarlanan veri temizleme, analiz ve raporlama süreçlerini tek bir script ile saniyeler içinde otomatikleştirir.
* **Canlı Sistemlerle Entegrasyon:** Doğrudan SQL veritabanlarına, bulut depolama sistemlerine, API'lara ve canlı web akışlarına bağlanarak veriyi kaynağından çeker.
* **Yapay Zeka ve Makine Öğrenmesi Köprüsü:** Temizlediğiniz veriyi anında Scikit-Learn, XGBoost veya derin öğrenme kütüphanelerine aktararak tahmin modellerine dönüştürmenizi sağlar.

---

## 2. Python Veri Dünyasında Neler Yapabilir? (Kullanım Alanları)

1. **Büyük Veri Temizleme ve Ön İşleme (Pandas & NumPy):**
   * Kirli, formatı bozuk, eksik ve aykırı değerlerle dolu ham veriyi analize ve modellemeye hazır temiz veri setlerine dönüştürür.
2. **Gelişmiş Görselleştirme (Matplotlib & Seaborn):**
   * Standart sütun grafiklerinin ötesinde; ısı haritaları (Heatmap), dağılım matrisleri (Pairplot) ve çok boyutlu korelasyon grafikleri ile verideki örüntüleri görselleştirir.
3. **İleri İstatistik ve Olasılık Modellemesi (SciPy & Statsmodels):**
   * Hipotez testleri, varyans analizleri, dağılım uyum testleri ve çoklu doğrusal/lojistik regresyon modellerini matematiksel detaylarıyla çalıştırır.
4. **Tahmine Dayalı Modelleme (Makine Öğrenmesi):**
   * Müşteri kaybı (Churn) tahmini, sahtekarlık (Fraud) tespiti, ürün öneri sistemleri ve satış tahminleri gibi geleceğe dönük kararlar üretir.
5. **Veri Çekme (Web Scraping):**
   * İnternet sitelerindeki fiyatları, haberleri veya kullanıcı yorumlarını otomatik olarak toplayıp analitik veri setlerine dönüştürür.

---

## 3. Veri Ön İşlemenin Omurgası: Pandas Temelleri

Veri analizinde zamanın yaklaşık %70'i veriyi temizlemeye harcanır. Pandas bu süreci yöneten temel kütüphanedir:

### Temel Keşif Adımları
* `df.info()`: Bellek kullanımını, sütun tiplerini ve boş olmayan satır sayılarını gösterir.
* `df.describe()`: Sayısal değişkenlerin dağılım parametrelerini (ortalama, standart sapma, çeyrekler) listeler.
* `df.isnull().sum()`: Hangi sütunda kaç adet eksik veri olduğunu tespit eder.

### Veri Temizleme ve Karar Stratejileri
* **Eksik Veri (Missing Data):**
  * Veri simetrik dağılıyorsa eksikler ortalama (`mean`), aşırı uç değerler varsa medyan (`median`) ile doldurulur.
  * Örnek: `df['gelir'].fillna(df['gelir'].median(), inplace=True)`
* **Tip Dönüştürme:**
  * Metin (string) olarak kalmış sayısal sütunları matematiksel işleme açar:
  * Örnek: `df['fiyat'] = pd.to_numeric(df['fiyat'], errors='coerce')`
* **Segmentasyon ve Özetleme (Groupby):**
  * Müşteri segmentleri veya ürün kategorileri bazında hızlı metrikler üretir:
  * Örnek: `df.groupby('segment')['harcama'].agg(['mean', 'std', 'count'])`