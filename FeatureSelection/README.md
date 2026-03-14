# Özellik Seçimi (Feature Selection)

Bu proje, bir veri setindeki mevcut olan çok sayıdaki özellik (sütun) arasından, tahmin veya sınıflandırma modelimiz için **en değerli ve anlamlı olanları seçme (Feature Selection)** sürecini uygulamalı olarak göstermektedir.

Sütun sayısının (boyutun) çok fazla olması modeli yavaşlatır, anlaşılabilirliğini azaltır ve en önemlisi gereksiz detayları ezberlemesine (Overfitting) yol açar.

Projede **`feature-engine`** ve **`scikit-learn`** kütüphaneleri kullanılmıştır.

## 🚀 Projenin Amacı ve Temel Yöntemler

Özellik seçimi temelde üç ana yaklaşım altında incelenmiştir:

- **1. Filter Methods (Filtreleme Yöntemleri):** İstatistiksel testlere ve verinin varyansına dayalı yöntemlerdir. Modeli işin içine katmaz, sadece veriye bakar.
  - **Constant Features (Sabit Özellikler):** Tüm satırlarda aynı değere sahip değişmeyen sütunların atılması.
  - **Quasi-constant Features:** Verinin %99'luk büyük bir kısmının aynı olduğu az değişkenli sütunların atılması.
  - **Korelasyon (Correlation):** Sütunların birbirleriyle olan benzerlik ilişkisi. Aynı şeyi anlatan iki farklı sütundan birinin çıkartılarak çoklu doğrusallık sorununun (Multicollinearity) çözülmesi.
- **2. Wrapper Methods (Sarmalayıcı Yöntemler):** Bir makine öğrenmesi algoritmasını kullanarak, özellikleri tek tek veya gruplar halinde ekleyip çıkararak en yüksek performansı veren sütun kombinasyonunu bulmaya dayalı yöntemler.
- **3. Embedded Methods (Gömülü Yöntemler):** Algoritmanın kendi doğası gereği (örn: Lasso L1 Regülarizasyonu veya Ağaç tabanlı modellerin Feature Importance özelliği) özelliklerin önemine kendi eğitim sürecinde karar verip gereksizleri budaması.

## 🛠 Kullanılan Teknolojiler

- **Python 3**
- **Pandas & NumPy**
- **Seaborn & Matplotlib:** Özellikler arası korelasyonları Heatmap (Isı Haritası) ile görselleştirme.
- **Feature-Engine & Scikit-Learn:** Korelasyon filtrelemesi, varyans testleri ve model oluşturma.

## 💡 Neden Özellik Seçimi Yapıyoruz?
Bir veri setine ne kadar çok veri eklerseniz o kadar iyi model çıkar mantığı her zaman doğru değildir (Curse of Dimensionality - Boyut Laneti). Daha az, ancak gerçekten hedefi açıklayan özellikler ile daha hızlı, şeffaf ve yüksek tahmin yeteneğine sahip genellenebilir (robust) modeller elde ederiz.
