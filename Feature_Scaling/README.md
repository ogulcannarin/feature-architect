# Özellik Ölçeklendirme (Feature Scaling)

Bu proje, makine öğrenmesi algoritmalarının veri setindeki farklı büyüklük ve ölçü birimlerine sahip değişkenleri adil bir biçimde değerlendirebilmesi için yapılan **Özellik Ölçeklendirme (Feature Scaling)** işlemlerini ele almaktadır.

Makine öğrenmesi modelleri değişkenlerin "Birim" taşıdığını (Metrekare, KG, TL vb.) bilmez, onlara yalnızca mutlak sayılar gözüyle bakar. Bu yüzden biri 1-5 arasında (Örn: Oda sayısı), diğeri 10.000-500.000 arasında (Örn: Fiyat) değişiyorsa model algısında büyük olan değer çok daha baskınmış hatasına düşer.

## 🎯 Projenin Odak Noktaları

Projelerimizde karşılaştığımız iki temel ölçeklendirme yaklaşımı incelenmiştir:

- **Standardization (Standardizasyon / StandardScaler):** Verinin ortalamasını (mean) 0'a, standart sapmasını ise 1'e çekecek şekilde veriyi dağıtır. Aykırı değerlerin (outliers) varlığında daha güvenilir ve stabil sonuçlar verir. Genellikle değerler -3 ile +3 aralığına oturur.
- **Normalization (Normalizasyon / MinMaxScaler):** Veriyi belirlediğimiz minimum ve maksimum değerler arasına (genellikle 0 ile 1 aralığı) sıkıştırır. Verinin sınırları biliniyorsa veya Derin Öğrenme (Deep Learning) modellerinde olduğu gibi sabit aralıklı veriler isteniyorsa tercih edilir.

## 🛠 Kullanılan Teknolojiler

- **Python 3**
- **Pandas:** Veri çerçevelerinin (DataFrame) yönetimi ve işlenmesi.
- **Scikit-Learn:** `StandardScaler` ve `MinMaxScaler` ile veri dönüştürme işlemleri.

## 💡 Neden Ölçeklendirme (Scaling) Şarttır?
Özellikle uzaklık/mesafe ölçümüne dayanan algoritmalar (Örn: K-Nearest Neighbors - KNN, K-Means) ve ağırlık/gradyan optimizasyonuna dayalı algoritmalar (Örn: Lineer Regresyon, Yapay Sinir Ağları) ölçeklendirilmemiş veride ya hiç öğrenemeyecek ya da tamamen yanlış faktörlere odaklanacaktır. Ağaç tabanlı modeller (Random Forest, XGBoost) ölçeklendirmeye ihtiyaç duymasa da, genel bir Veri Bilimi alışkanlığı olarak uygulanması projeyi standartlara ulaştırır.
