# Yapay Sinir Ağları — MLP ile Bank Marketing Sınıflandırması

Bu proje, Yapay Sinir Ağları dersi kapsamında yüksek lisans ara sınav çalışması olarak hazırlanmıştır. Çalışmada, bankacılık pazarlama verileri kullanılarak müşterilerin vadeli mevduat aboneliği yapma olasılıkları Çok Katmanlı Algılayıcı (MLP) modeli ile tahmin edilmiştir.

**Öğrenci Numarasının Son 5 Hanesi:** 12902  
**Temel Rastgelelik Tohumu (Seed):** 14928

## 1. Veri Kümesi

Projede UCI Machine Learning Repository'de bulunan **Bank Marketing** veri kümesinin `bank-additional.csv` dosyası kullanılmıştır.

- **Gözlem sayısı:** 4.119
- **Hedef değişken:** Vadeli mevduat aboneliği
- **Çıkarılan değişken:** `duration`

`duration` değişkeni, tahmin yapılacağı anda bilinmeyeceği için veri sızıntısını önlemek amacıyla modelden çıkarılmıştır.

**Veri kaynağı:** https://archive.ics.uci.edu/dataset/222/bank+marketing  
**DOI:** 10.24432/C5K306

## 2. Projenin Çalıştırılması

Projenin Google Colab ortamında çalıştırılması önerilmektedir.

1. `MLP_Midterm_14928_Colab.ipynb` dosyasını Google Colab üzerinden açın.
2. Gerekli kütüphaneleri `requirements.txt` dosyasına göre yükleyin.
3. Notebook içerisindeki kod hücrelerini sırasıyla çalıştırın.
4. Oluşturulan sonuçları `results/`, grafikleri ise `figures/` klasöründen inceleyin.

Projede ayrıca üç ayrı notebook bulunmaktadır:

- `01_eda.ipynb` — Keşifsel veri analizi
- `02_nested_cv.ipynb` — İç içe çapraz doğrulama ve hiperparametre araması
- `03_final_test.ipynb` — Nihai model ve test değerlendirmesi

Bu üç notebook, ortak değişkenler kullandıkları için aynı aktif Colab oturumunda sırasıyla çalıştırılmalıdır. Bağımsız olarak yeniden başlatılıp çalıştırılmak üzere hazırlanmamıştır.

**Önemli:** Nihai test sonuçları hesaplanmadan önce, test etiketlerini içermeyen tahminlerin, son model yapılandırmasının ve kodun GitHub'a ayrı bir commit ile kaydedilmesi gerekir. Bu projedeki test sonuçları mevcut deney çalışmasından elde edilmiştir. Tahminlerin kilitlenme sırası GitHub commit geçmişinden kontrol edilmelidir.

## 3. Kullanılan Yöntemler

Çalışmada aşağıdaki yöntemler uygulanmıştır:

- Verilerin %80 geliştirme ve %20 bağımsız test kümesi olarak tabakalı biçimde ayrılması
- 3 dış kat ve 3 iç kat ile Nested Cross-Validation uygulanması
- Altı manuel ve altı rastgele hiperparametre adayının karşılaştırılması
- PyTorch kullanılarak MLP modelinin oluşturulması
- `BCEWithLogitsLoss` kayıp fonksiyonunun kullanılması
- Early Stopping ve isteğe bağlı `ReduceLROnPlateau` uygulanması
- Veri ön işleme adımlarının yalnızca ilgili eğitim katında öğrenilmesi
- Üç farklı sabit seed ile nihai model sonuçlarının incelenmesi

Bağımsız test kümesi, model seçiminde kullanılmamış ve kilitli tahminlerin kaydedilmesinden sonra değerlendirilmiştir.

## 4. Proje Dosya Yapısı

| Dosya / Klasör | Açıklama |
|---|---|
| `MLP_Midterm_14928_Colab.ipynb` | Projenin ana notebook dosyası |
| `01_eda.ipynb` | Keşifsel veri analizi |
| `02_nested_cv.ipynb` | Nested CV ve hiperparametre araması |
| `03_final_test.ipynb` | Nihai model ve test işlemleri |
| `configs/` | Hiperparametre yapılandırmaları |
| `results/` | Veri ayrımları, deney sonuçları, eğitim kayıtları ve tahmin dosyaları |
| `figures/` | Grafikler ve görselleştirmeler |
| `report.pdf` | Projenin Türkçe teknik raporu |
| `requirements.txt` | Kullanılan Python kütüphaneleri |

## 5. Tekrarlanabilirlik ve Sınırlılıklar

Deneylerin tekrarlanabilmesi için kullanılan kütüphane sürümleri `results/environment.json` dosyasından kontrol edilebilir. Farklı kütüphane sürümleri sonuçlarda küçük değişikliklere neden olabilir.

Çalışmanın bazı sınırlılıkları bulunmaktadır:

- Veri kümesinde müşteri kimliği bulunmadığından, rastgele veri ayrımı müşteri bazında bağımsızlığı veya zamansal genellemeyi garanti etmez.
- Veri kümesindeki sınıf dengesizliği, pozitif sınıfın tahmin edilmesini zorlaştırmaktadır.
- Bağımsız test sonuçlarına göre model veya hiperparametre seçimi yapılmamalıdır.
- Nested CV ve farklı seed sonuçları, model performansının daha kapsamlı değerlendirilmesi amacıyla kullanılmıştır.

## 6. Teknik Rapor

Çalışmanın veri analizi, model mimarisi, hiperparametre karşılaştırmaları, performans metrikleri, grafikler ve sonuç değerlendirmeleri `report.pdf` dosyasında sunulmuştur.

## 7. Kaynaklar

1. Moro, S., Rita, P. ve Cortez, P. (2014). *Bank Marketing*. UCI Machine Learning Repository. DOI: 10.24432/C5K306
2. scikit-learn Documentation: https://scikit-learn.org/stable/
3. PyTorch Documentation: https://pytorch.org/docs/stable/
