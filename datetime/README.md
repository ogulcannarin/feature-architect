# Datetime Özellik Çıkarımı (Datetime Feature Extraction)

Bu proje, makine öğrenmesi uygulamalarında zaman serisi veya tarih bazlı veri setleriyle çalışırken, **tarih ve saat (datetime)** verilerinden eğitim için ne kadar zengin öznitelikler çıkarılabileceğini anlatan uygulamalı bir rehberdir. Modeller genellikle standart bir datetime string formatını doğrudan işleyemez; bu nedenle tarih bilgisini yıl, ay, gün, saat gibi sayısal ve kategorik bileşenlerine ayırmak çok kritik bir özellik mühendisliği (feature engineering) adımıdır.

Bu projede güçlü ve açık kaynaklı **`feature-engine`** kütüphanesi kullanılmıştır.

## 🚀 Projenin Amacı ve Odak Noktaları

Bu örnek çalışma aşağıdaki konuları kapsamlı bir biçimde öğrenmenizi sağlar:

- **DatetimeFeatures Sınıfının Kullanımı:** `feature_engine.datetime` modülünü kullanarak bir `date_time` değişkeninden belirli veya tüm zaman varyasyonlarını otomatik olarak üretmek.
- **Esnek Özellik Çıkarımı:** Sadece modele katkı sağlayacağı düşünülen spesifik alanların ayıklanması (örneğin sadece `"day_of_month"` ve `"hour"` değerleri).
- **Orijinal Sütun Davranışını Yönetme:** Çıkarım sonrası orijinal tarih sütununu koruma (`drop_original=False`) veya silme seçimini yapmak.
- **Otomatik Özellik Çıkarımı:** Parametre vermeden (`features_to_extract=None` kullanılarak) tüm olası zaman bileşenlerini (yıl, ay, gün, saatin dakikası, saniyesi vb.) tek adımda türetmek.
- **Scikit-Learn Pipeline Entegrasyonu:** Gerçek dünya projelerinde, bu özelliğin ve `DropConstantFeatures` kuralının bir uçtan uca `sklearn.pipeline.Pipeline` içinde nasıl birleştirilip profesyonel standartlarda kullanılacağını tecrübe etmek.

## 📦 Kullanılan Veri Seti

Uygulamada **Metro Interstate Traffic Volume** DataFrame'i (`Metro_Interstate_Traffic_Volume.csv.gz`) kullanılmıştır. Veri setindeki bazı temel değişkenler:

- `holiday`: O günün resmi tatil olup olmadığı
- `temp`, `rain_1h`, `snow_1h`, `clouds_all`: Meteorolojik sayısal veriler
- `weather_main`, `weather_description`: Kategorik hava durumu bilgileri
- `date_time`: **Üzerinde özellik çıkarımı yapacağımız temel tarih/saat değişkeni**
- `traffic_volume`: Otoban trafik hacmi (Genelde tahmin edilmeye çalışılan hedef yapı)

## 🛠 Kullanılan Teknolojiler ve Kütüphaneler

Projeyi çalıştırmak için aşağıdaki bileşenlere ihtiyaç duyulmaktadır:

- `Python 3.x`
- `pandas` (Veri okuma, temizleme ve analizi)
- `numpy` (Matematiksel ve sayısal operasyonlar)
- `matplotlib` (Olası veri görselleştirme adımları)
- `scikit-learn` (Veri boru hatları / Pipeline mimarisi)
- `feature-engine` (Temel özellik çıkarıcılarımız: *DatetimeFeatures*, *DropConstantFeatures*)

## 💡 Proje Adımları

1. **Verinin Yüklenmesi:** Sıkıştırılmış `.csv.gz` üzerinden veri okunur, veri tipleri incelenir ve `NaN` (kayıp veri) incelemesi yapılır.
2. **Spesifik Özellik Çıkarımı:** `DatetimeFeatures` fonksiyonuna sadece `"day_of_month", "hour"` gibi belli parametreler geçilerek dar kapsamlı dönüşüm yapılır.
3. **Orijinal Sütunu Koruma:** `drop_original=False` argümanının eklenmesiyle ilk `date_time` formunun kaybolmaması sağlanır.
4. **Veri Temizliği (Hata Çözümü):** Pipeline'a girmeden önce `dropna()` gibi metotlarla kayıp değerlerin silinmesi/doldurulması tekniği ele alınır.
5. **Kurumsal Akış (Makine Öğrenmesi Pipeline Çalışması):**  Model eğitim kısmına verinin en temiz ve doğru şekilde akabilmesi için `Pipeline` objesi kurulur, özellikler çıkarılır ve sabit kalan, modele bilgi katmayan varyanssız (constant) sütunlar `DropConstantFeatures` yardımıyla elenir.

---
*Bu içerik, veriden maksimum kavrama gücü elde etmeyi amaçlayan Veri Bilimi ve Makine Öğrenmesi öğrencileri/geliştiricileri için yol gösterici bir doküman olma niteliğindedir.*
