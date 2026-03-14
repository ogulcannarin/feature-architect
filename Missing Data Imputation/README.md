# Eksik Veri Doldurma (Missing Data Imputation)

Bu proje, gerçek dünya veri setlerinin en büyük problemlerinden biri olan **Eksik veya Boş Özelliklerin (NaN / Null) Doldurulması** süreçlerini, hem sayısal hem de kategorik verilere özel teknikler uygulayarak göstermektedir. 

Modeller genellikle boş verilerle (NaN) karşılaştığında doğrudan hata verirler. Veriyi doğrudan silmek (Drop) kolay olsa da çok kıymetli veri kayıplarına yol açar. Bu nedenle verinin dağılımını bozmadan boşlukları doldurmak ana hedefimizdir.

Projede **`feature-engine`** ve **`missingno`** kütüphaneleri kullanılmıştır.

## 🚀 Proje Adımları ve Çözüm Yöntemleri

- **1. Durum Tespiti:** Veri setinin eksik veri oranı tespit edilmiş ve eksik veri dağılım örüntüsünü görselleştirmek için `missingno` kütüphanesinin matris çizim yetenekleri kullanılmıştır.
- **2. Sayısal Verileri Doldurma:** 
  - Sayısal değişkenler (örn. Cephe uzunluğu) incelenmiş ve boş değerlerin o sütunun **Medyan (Ortanca)** veya **Ortalama (Mean)** değeri ile doldurulması süreci işlenmiştir. Güvenli yaklaşım olan median kullanımı uygulanmıştır.
- **3. Kategorik Verileri Doldurma:**
  - Kategorik değişkenlerde oraya matematiksel bir ortalama koymak mümkün olmadığı için, boşlukların o sütunda en çok tekrar eden (Frequent/Mode) değerle doldurulması veya doğrudan boş olduğu anlaşılsın diye **"Missing" / "Kayıt Yok"** tarzında yepyeni bir grup etiketi atama yöntemleri kullanılmıştır.
- **4. Otomatizasyon:** Bu işlemler `feature-engine` modüllerinden `MeanMedianImputer` ve `CategoricalImputer` yardımıyla gerçekleştirilmiştir.

## 🛠 Kullanılan Teknolojiler

- **Python 3**
- **Pandas:** Satır bazlı eksik veri analizi (`isnull().sum()`, `isnull().mean()`) işlemleri.
- **Missingno & Matplotlib:** Eksik verilerin matris tabanlı görsel dağılımı.
- **Feature-Engine:** Hızlı, etkili ve pipeline uyumlu boş veri onarımı.

## 💡 Neden Verileri Doldurmalıyız?
Modellerin çalışması için verinin tam (complete matrix) olması gerekir. %80'i boş olan veriyi komple sütun olarak söküp atmak mantıklı bir stratejiyken; %5'i boş olan çok önemli bir özniteliğe sahip satırları sırf bir kutusu boş diye atmak elimizdeki potansiyeli çöpe atmaktır. Akıllı Doldurma (Imputation), modellerin güvenilirliğini artırır.
