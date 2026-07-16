# 📱 İkinci El Telefon Pazar Analizi - Power BI Dashboard

## 📋 Proje Özeti
Bu proje, Microsoft Power BI ile oluşturulmuş kapsamlı bir Veri Analizi ve Görselleştirme panosudur (dashboard). Piyasa trendlerini, donanımın fiyatlandırma üzerindeki etkilerini ve zaman içindeki değer kaybı oranlarını ortaya çıkarmak için **1.000.000 ikinci el cep telefonundan** oluşan devasa bir veri setini analiz eder.

## 📂 Veri Seti
Veri seti, aşağıdakileri içeren 1 milyon satırlık ikinci el telefon listelemesinden oluşmaktadır:
- **Cihaz Bilgileri:** Marka, Model, Çıkış Yılı, İşletim Sistemi (OS) Türü, 5G desteği.
- **Donanım Özellikleri:** RAM (GB), Depolama (GB), Batarya Kapasitesi, Batarya Sağlığı.
- **Fiziksel Durum:** Ekran kırık, Kasa hasarı, Tamir geçmişi, Su hasarı.
- **Fiyatlandırma Detayları:** Orijinal Fiyat, İkinci El Satış Fiyatı.

## 📊 Temel Özellikler ve Görselleştirmeler

### 1. Pazar Genel Bakış (Sayfa 1)
- **Üst Düzey KPI'lar:** Toplam İlan Sayısı, Ortalama Orijinal Fiyat, Ortalama İkinci El Fiyatı.
- **Marka Dağılımı:** Farklı markaların (Apple, Samsung, Google vb.) pazar payını gösteren halka grafik (Donut chart).
- **Durum Etkisi:** Cihaz durumunun (Mükemmel, İyi, Kötü) ikinci el değerini nasıl etkilediğini detaylandıran sütun grafik.
- **Etkileşimli Filtreler:** İşletim Sistemi Türü (Android/iOS) ve 5G Desteği için modern dilimleyiciler (slicers).

### 📉 2. Değer Kaybı ve Fiyatlandırma Analizi (Sayfa 2)
- **Yaş ve Fiyat Trendi:** Cihaz yaşına (ay cinsinden) dayalı değer kaybı eğrisini gösteren dağılım grafiği (Scatter plot).
- **Tarihsel Değer Düşüşü:** Çıkış yılına göre ortalama yüzde fiyat düşüşünü gösteren çizgi grafik.
- **Pazar Demografisi:** Farklı Şehir Kademeleri ve Satıcı Türleri (Mağaza vs. Bireysel) arasındaki satış dağılımını görselleştiren ağaç haritası (Treemap).

### ⚙️ 3. Donanımın Fiyat Üzerindeki Etkisi (Sayfa 3)
- **Özellik Matrisi:** RAM ve Depolama yapılandırmalarının ortalama ikinci el fiyatına karşı çapraz tablosu.
- **Hasar Analizi:** Ekran kırıkları ve su hasarının fiyatlandırma üzerindeki doğrudan olumsuz etkisini vurgulayan çubuk grafikler.
- **Batarya Sağlığı:** İkinci el telefon pazarının genel ortalama batarya sağlığını gösteren gösterge (Gauge) grafiği.

## 🧮 Kullanılan DAX Ölçüleri (Measures)
Önemli metrikleri anında hesaplamak için bu panoda dinamik DAX ölçüleri oluşturulmuştur:

```dax
Avg Resale Price = AVERAGE('used_phone_price_prediction_1M'[resale_price])

Avg Original Price = AVERAGE('used_phone_price_prediction_1M'[original_price])

Price Drop % = DIVIDE([Avg Original Price] - [Avg Resale Price], [Avg Original Price], 0)

Total Phones = COUNTROWS('used_phone_price_prediction_1M')
