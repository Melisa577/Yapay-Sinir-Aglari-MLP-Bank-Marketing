# Yapay Sinir Ağları — MLP ile Bank Marketing Sınıflandırması

Yüksek lisans ara sınav projesi. Öğrenci numarası son 5 hane: **12902**; temel seed: **14928**.

## Dataset
UCI Bank Marketing: yalnızca `bank-additional.csv` (4.119 kayıt). `duration` özelliklerden çıkarılır. Kaynak: https://archive.ics.uci.edu/dataset/222/bank+marketing (DOI: 10.24432/C5K306).

## Çalıştırma
Google Colab üzerinde `MLP_Midterm_14928_Colab.ipynb` dosyasını sırayla çalıştırın. Üç ayrı notebook (`01_eda.ipynb`, `02_nested_cv.ipynb`, `03_final_test.ipynb`) aynı açık runtime'da sırayla çalışacak şekilde hazırlanmış bölümlerdir; bağımsız çalıştırılabilir değillerdir.

**Bağımsız test etiketleriyle metrik hesaplamadan önce** etiketsiz `test_predictions_locked.csv`, nihai konfigürasyon ve kod ayrı bir GitHub commit'ine kaydedilmelidir. Geçmiş commit sırası ayrıca doğrulanmalıdır; sonraki yüklemeler geçmişteki kilitlemeyi kanıtlamaz.

## Yöntem
%80 development / %20 bağımsız test; 3 outer ve 3 inner stratified fold; 6 manuel + 6 rastgele aday; PyTorch MLP, BCEWithLogitsLoss, early stopping, ReduceLROnPlateau ve fold-local preprocessing. Ana değerlendirme metriği Average Precision (AP).

## Beklenen dosyalar
- `MLP_Midterm_14928_Colab.ipynb`: ana Colab notebook
- `01_eda.ipynb`, `02_nested_cv.ipynb`, `03_final_test.ipynb`: ardışık bölümler
- `configs/`: adaylar ve eğitim ayarları
- `results/`: split, arama sonuçları, eğitim günlükleri, tahminler ve test metrikleri
- `figures/`: EDA, CV, eğitim ve test görselleri
- `report.pdf`: **gözden geçirilmesi gereken Türkçe rapor taslağı**
- `requirements.txt`: paketler (gerçek sürümler `results/environment.json` içinde)

## Sınırlamalar
Veri kümesinde müşteri kimliği yoktur; rastgele bölme zaman/kişi bağımsız genellemeyi kanıtlamaz. Test skorlarına göre hiperparametre veya eşik değiştirilmez. Rapor teslimden önce tablo, şekil ve kaynaklarla karşılaştırılmalıdır.

## Kaynaklar
Moro, Rita ve Cortez (2014), Bank Marketing, UCI, DOI 10.24432/C5K306; https://scikit-learn.org/stable/ ; https://pytorch.org/docs/stable/ .
