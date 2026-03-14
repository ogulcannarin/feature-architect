# Özellik Mühendisi Rehberi (Feature Architect)

**Feature Architect**, makine öğrenmesi modellerinizin kalitesini, doğruluğunu ve performansını en üst düzeye çıkarmak için uygulanan "Özellik Mühendisliği (Feature Engineering)" tekniklerini adım adım anlatan, uygulamalı bir rehber ve kod deposudur.

Ham veriyi doğrudan makine öğrenmesi modellerine vermek genellikle hüsranla sonuçlanır. Modellerin daha iyi kavrayabileceği, aykırı değerlerden arındırılmış, kayıp değerleri doldurulmuş ve matematiksel olarak anlamlı hale getirilmiş özellikler (sütunlar) inşa etmek işin temelidir. Bu repo, profesyonel bir veri bilimcinin kullandığı modern özellik mimarisi konseptlerini içerir.

## 📂 İçindekiler ve Klasör Yapısı

Repo, özellik mühendisliği kavramlarını belirli görevlere göre klasörlere ayırmıştır. Her klasör kendi içinde konuyu, kodları ve detaylı açıklama içeren bir `README.md` dosyasını barındırır.

1. **[Discretisation (Ayrıklaştırma) & Mean Encoding](./Discretisation/)**
   Sürekli sayısal değişkenleri belirli aralıklara (bin) bölüp kategorize etme ve kategorileri hedef değişkenin ortalamasıyla değiştirerek algoritmaya sunma teknikleri.

2. **[Encoding (Kategorik Kodlama)](./Encoding/)**
   Aralarında hiyerarşi olan veya olmayan metin bazlı kategorik değişkenlerin (One-Hot, Ordinal, Count/Frequency, Target, Rare Label) sayısal sistemlere en doğru biçimde dönüştürülmesi adımları.

3. **[Feature Selection (Özellik Seçimi)](./FeatureSelection/)**
   Elimizdeki verilerden modelin kafasını karıştırabilecek gereksiz sütunları filtreleyerek boyut indirgeme, korelasyon tespiti ve en saf, performanslı özellikleri seçme yöntemleri (Filter, Wrapper, Embedded).

4. **[Feature Scaling (Özellik Ölçeklendirme)](./Feature_Scaling/)**
   Sayısal değerlerin büyüklük birimlerinin (metrekare ile oda sayısı gibi) modellerde domine etme sorununu çözmek için veriyi belirli bir aralığa Standardizasyon ve Normalizasyon ile oturtma çalışmaları.

5. **[Missing Data Imputation (Eksik Veri Doldurma)](./Missing%20Data%20Imputation/)**
   Gerçek hayat senaryolarındaki boş ve hatalı verilerin, veri kaybı yaşanmadan sayısal (Mean/Median) veya kategorik ("Missing"/Frequent) tekniklerle onarılması işlemi.

6. **[Datetime Feature Extraction (Tarihsel Özellik Çıkarımı)](./datetime/)**
   Ham tarih/zaman bilgisinin model tarafından anlaşılamaması problemine karşılık; datetime verisinden yıl, ay, gün, saat gibi yeni özniteliklerin türetilmesi süreçleri.

7. **[Outlier Handling & Transformations (Aykırı Değer Yönetimi ve Dönüşümler)](./outlier_handling_and_transformation/)**
   Modellerin doğruluğunu ciddi şekilde bozan Aykırı Değerlerin (Outliers) tespit edilerek uç sınırlarının kırpılması ve çarpıklığı yüksek veri seti dağılımlarını normale yaklaştırmak için uygulanan Matematiksel (Log) Dönüşüm işlemleri.

## 🛠 Kullanılan Temel Teknolojiler

- Mimarinin tamamında **Python** dili hakimdir.
- İstatistik ve manipülasyon işlemleri için **Pandas** ve **NumPy**
- Algoritmik döngüler, ölçeklendirme aracı olarak **Scikit-Learn**
- Otomatik özellik mühendisliğini en güvenli şekilde yapmak ve Pipeline oluşturmak için muhteşem **Feature-Engine** kütüphanesi
- Görselleştirmeler için **Matplotlib**, **Seaborn** ve **Missingno**

## 🚀 Nasıl Kullanılır?

1. İlginizi çeken konunun klasörüne gidin.
2. O klasör içindeki **README.md** dosyasını okuyarak problemin ne olduğunu ve hangi mantıkta çözüldüğünü anlayın.
3. Jupyter Notebook (`.ipynb`) dosyalarını açarak kodları ve adımları inceleyin.

Makine Öğrenmesi dünyasında asıl farkı yaratan şey devasa algoritmalar değil, veriyi o algoritmalara nasıl hazırladığınızdır. Bu proje bu vizyonu inşa etmek için tasarlanmıştır.
