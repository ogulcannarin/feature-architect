# Feature Engineering: Discretisation & Mean Encoding (Titanic Dataset)

Bu proje, açık kaynaklı **Titanic** veri setini kullanarak **Sürekli Değişkenlerin Ayrıklaştırılması (Discretisation)** ve ardından **Ortalama Kodlama (Mean Encoding)** işlemlerinin nasıl yapıldığını adım adım göstermektedir. Projedeki temel amaç, sürekli sayısal değişkenleri (yaş, bilet fiyatı vb.) belirli aralıklara (bin) bölmek ve ardından bu kategorileri hedef değişkenin ortalamasıyla sayısal hale getirerek, makine öğrenmesi modelleri (özellikle doğrusal modeller) için daha uygun bir formata dönüştürmektir.

## 🎯 Projenin Amacı

- **Sürekli Değişkenleri Kategorik Hâle Getirme (Discretisation):** Modelin, karmaşık sürekli verileri daha kolay algılamasını sağlamak amacıyla verileri mantıksal aralıklara bölmektir.
- **Hedef Odaklı Kodlama (Mean Encoding):** Elde edilen bu yeni kategorik aralıkları, hedef değişken (`survived` yani hayatta kalma durumu) ile doğrudan orantılı hale getirerek (monotonik bir ilişki kurarak) model performansını desteklemektir.

## 🛠 Kullanılan Teknolojiler ve Kütüphaneler

- **Python 3**
- **Pandas & NumPy:** Veri işleme, temizleme ve analizi.
- **Scikit-Learn:** Veri setinin train/test olarak ayrılması ve `Pipeline` oluşturulması.
- **Feature-Engine:** `ArbitraryDiscretiser` ve `MeanEncoder` modülleri ile kolay ve hızlı özellik mühendisliği.
- **Matplotlib:** Dönüşüm sonrası oluşan monotonik ilişkiyi görselleştirme.

## 📝 Adım Adım Neler Yapıldı?

1. **Veri Yükleme ve Temizleme (`load_titanic`):**
   - OpenML üzerinden Titanic verisi çekildi.
   - Bilinmeyen değerleri temsil eden `'?'` karakterleri gerçek boş değer (`NaN`) ile değiştirildi.
   - `age` (yaş) ve `fare` (ücret) sütunları sayısal veri tipine zorlandı.
   - Oluşan eksik (boş) değerler **Medyan (Ortanca)** yöntemiyle dolduruldu.
   - Modele katkı sağlamayacak olan `boat`, `body`, `ticket` gibi gereksiz sütunlar veriden çıkarıldı.

2. **Veri Setinin Ayrılması:**
   - Veriler bağımlı değişken (hedef: `survived`) ve bağımsız değişkenler olarak ayrıldı.
   - Sonrasında modeli eğitmek ve test etmek için `%70 Train`, `%30 Test` oranında bölündü.

3. **Arbitrary Discretiser Uygulaması:**
   - Sürekli olan `age` ve `fare` sütunları manuel olarak belirlenmiş aralıklara bölündü.
     - *Age (Yaş) Aralığı:* [0-18, 18-30, 30-50, 50-100]
     - *Fare (Ücret) Aralığı:* [-1-20, 20-40, 40-60, 60-80, 80-600]
   - Bu dönüşümün sonucu, sayısal değil kategorik bir obje olarak ayarlandı (`return_object=True`).

4. **Mean Encoder Uygulaması:**
   - `ArbitraryDiscretiser` ile kategorik gruplara ayrılan `age` ve `fare` sütunlarındaki her bir grup, hedef değişkenin o gruptaki **ortalaması (mean)** ile değiştirildi.
   - *Örnek:* "18-30 yaş" kategorisindeki herkesin hayatta kalma oranının ortalaması alınarak, 18-30 yaş aralığı bu ortalama sayısal değerle ifade edildi.

5. **Pipeline Kurulumu ve Dönüşüm (Transformation):**
   - Ayrıklaştırma (Discretisation) ve Kodlama (Mean Encoding) adımları düzenli ve tekrar edilebilir olması adına bir **Scikit-Learn Pipeline** içerisine entegre edildi.
   - `fit` ve `transform` işlemleri eğitim (train) ve test verilerine sızma (data leakage) olmadan uygulandı.

6. **Görselleştirme:**
   - Son olarak `fare` değişkeni ile hedef değişken olan `survived` arasındaki ilişki incelendi ve bu yeni özelliklerin hedef ile olan doğrusal/monotonik bağıntısı bir çizgi grafiği ile gösterildi.

---

### 💡 Neden Bu Yöntemi Kullanıyoruz?
Doğrusal modeller (Linear Regression, Logistic Regression vb.) değişkenler ile hedef arasında düzenli ve doğrusal bir ilişki olduğunda çok daha iyi çalışır. Sürekli bir değişkeni direkt kullanmak yerine önce mantıklı aralıklara bölüp sonra ortalaması üzerinden sisteme sokmak, aşırı uç değerlerin (outliers) model üzerindeki olumsuz etkisini azaltır ve veride gizli olan "grupların taşıdığı anlamı" modele doğrudan sunar.
