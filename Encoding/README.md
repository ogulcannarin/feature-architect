# Özellik Mühendisliği: Kategorik Değişken Kodlama (Categorical Encoding)

Bu proje, makine öğrenmesi modellerinin anlayabilmesi için **Kategorik Değişkenlerin Sayısal Formata Dönüştürülmesi (Encoding)** işlemlerinin nasıl yapıldığını adım adım göstermektedir. Bilgisayarlar metin tabanlı verileri doğrudan işleyemez; bu nedenle kategorik verilerin sahip olduğu özelliklere (sıralı, sırasız, çok sınıflı vb.) uygun kodlama yöntemlerinin seçilmesi model başarısı için çok önemlidir.

Projede güçlü ve açık kaynaklı **`feature-engine`** kütüphanesi kullanılmıştır.

## 🎯 Projenin Amacı ve Odak Noktaları

- **One-Hot Encoding:** Aralarında hiyerarşi olmayan kategorik verileri (örn. Şehir, Renk) 0 ve 1'lerden oluşan bağımsız sütunlara çevirmek.
- **Ordinal Encoding:** Aralarında bir sıralama/derece bulunan kategorik verileri (örn. Kötü, Orta, İyi, Mükemmel) mantıklı bir sayısal hiyerarşiye (0, 1, 2, 3) dönüştürmek.
- **Count / Frequency Encoding:** Kategorik değerleri, veri setinde geçme sayılarına veya yüzdelik oranlarına (frekanslarına) göre sayısallaştırmak.
- **Target (Mean) Encoding:** Kategorik değerleri, o kategorideki hedef değişkenin ortalamasıyla değiştirerek modelin doğrudan hedefle olan bağıntıyı kurmasını sağlamak.
- **Rare Label Encoding:** Veri setinde çok az (%5 gibi bir eşiğin altında) geçen nadir kategorileri tek bir çatı altında ("Rare" vb.) toplayarak aşırı öğrenmeyi (overfitting) ve gereksiz sütun kalabalığını önlemek.

## 🛠 Kullanılan Teknolojiler ve Kütüphaneler

- **Python 3**
- **Pandas:** Veri işleme, temizleme ve analizi.
- **Feature-Engine:** `RareLabelEncoder`, `OneHotEncoder`, `OrdinalEncoder`, `CountFrequencyEncoder`, `MeanEncoder` modülleri ile kolay ve hızlı özellik mühendisliği.

## 📝 Adım Adım Neler Yapıldı?

1. Veri setindeki çeşitli özellikler (Sokak, Mahalle, Ev Kalitesi vb.) analiz edilerek hangi veri türüne hangi kodlamanın uygun olduğu belirlendi.
2. Aşırı az tekrar eden veriler `RareLabelEncoder` ile toplandı.
3. Hiyerarşisi olmayan değişkenler için standart `OneHotEncoder` işlemi uygulandı.
4. "ExterQual" (Dış Cephe Kalitesi) gibi birbiriyle sıralama ilişkisi olan değişkenlere `OrdinalEncoder` uygulandı.
5. "Mahalle" gibi özellikler için o mahallenin veri setindeki geçme sayısını gösteren `CountFrequencyEncoder` ve hedefe göre ortalama fiyatını gösteren Target (`MeanEncoder`) uygulandı.

---

### 💡 Neden Bu Yöntemleri Kullanıyoruz?
Doğru bir kategorik kodlama yapılmazsa, model metin verilerini işlemekte hata alarak çökecek veya yanlış anlamlandırmalar yapacaktır (örneğin One-Hot Encoding yapılması gereken bir yere Ordinal Encoding yapmak renklerin birbiri ardına dizilmesine ve modelin mantıksız ilişkiler kurmasına neden olur). Gelişmiş kodlama yöntemleri model performansını inanılmaz ölçüde artırabilir.
