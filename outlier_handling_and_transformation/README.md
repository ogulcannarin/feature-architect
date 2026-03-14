# Aykırı Değer Yönetimi ve Matematiksel Dönüşümler (Outlier Handling & Transformations)

Bu proje, makine öğrenmesi modellerinin doğruluğunu ciddi şekilde bozan **Aykırı Değerlerin (Outliers)** nasıl tespit edilip yönetilebileceğini ve özellikle sağa/sola çarpık (skewed) veri dağılımlarını normale yaklaştırmak için uygulanan **Matematiksel Dönüşüm (Logaritmik Dönüşüm)** işlemlerini uygulamalı olarak göstermektedir.

Aykırı değerler ve verideki yüksek çarpıklık (skewness), lineer modeller (örn. Doğrusal Regresyon, Lojistik Regresyon) ve algılayıcı (perceptron) tabanlı modellerin ağırlıklarını şaşırtarak tahmin gücünü düşürür.

Projede sıklıkla kullanılan **`feature-engine`**, **`numpy`** ve veri görselleştirme kütüphaneleri kullanılmıştır.

## 🎯 Projenin Amacı ve Odak Noktaları

- **Veri Dağılımını Anlama:** Bir özniteliğin (örneğin Konut Fiyatları - `SalePrice`) histogram ve Kutu Grafiği (Boxplot) ile nasıl bir dağılıma (çarpıklığa) sahip olduğunun tespit edilmesi.
- **IQR ile Aykırı Değer Tespiti:** Q1 (1. Çeyreklik) ve Q3 (3. Çeyreklik) değerleri hesaplanarak matematiksel alt ve üst sınırların bulunması.
- **Aykırı Değerleri Kırpma / Capping (Winsorizer):** Aşırı uçta kalan değerleri, veri kaybını önlemek adına silmek (Drop) yerine alt veya üst sınırlara sabitleme/kırpma tekniği (Winsorization) uygulamak.
- **Matematiksel Dönüşüm (Log Transformation):** Sağa doğru çok uzun bir kuyruğa sahip (High Positive Skewness) veri setlerinin, `np.log1p()` kullanılarak logaritmasının alınıp standart normal dağılıma (Çan Eğrisi) dönüştürülmesi.

## 🛠 Kullanılan Teknolojiler ve Kütüphaneler

- **Python 3**
- **Pandas & NumPy:** İstatistiksel hesaplamalar ve logaritma (`log1p`) fonksiyonu.
- **Matplotlib & Seaborn:** Histogramlar ve Boxplotlar ile aykırı değerlerin görsel izlenimi.
- **Feature-Engine:** `Winsorizer` modülü ile pratik outlier kırpma işlemi.

## 📝 Adım Adım Neler Yapıldı?

1. Konut fiyatları (`SalePrice`) incelendi, verinin sağa çarpık (skewed) olduğu gözlemlendi.
2. IQR formülü ile üst sınır ve alt sınır tespit edildi, bu sınırları aşan yüzlerce aykırı değer bulundu.
3. Modelin eğitilebilir bir şekilde kurgulanması için `feature-engine` içerisinden `Winsorizer` kullanıldı. Outlier'lar silinmek yerine sınır değerine sabitlendi (Capping).
4. `SalePrice` orijinal haliyle Lineer Regresyon gibi modeller için aşırı çarpık olduğundan `np.log1p()` dönüşümü uygulandı.
5. İşlem sonrasında Çarpıklık (Skewness) katsayısının 1.88'den 0.12'ye (mükemmele çok yakın) düştüğü görüldü ve dağılım grafiği tekrar çizildi.

---

### 💡 Neden Bu Yöntemleri Kullanıyoruz?
Eğer ev fiyatları genelde 100.000 TL ile 300.000 TL arasındayken veri setinin içinde 10.000.000 TL'lik bir yalı varsa, makine öğrenmesi algoritması o yalıyı anlamak için tüm ağırlıklarını kaydıracak ve ortalama evleri yanlış tahmin etmeye başlayacaktır. Aynı şekilde Algoritmalar, Normal (Çan Eğrisi) Dağılımına sahip verileri işlemekte çok daha yeteneklidir. Log dönüşümü, matematiksel bir ilüzyon ile verinin genetiğini değiştirmeden şeklini modellerin en çok sevdiği formata getirir.
