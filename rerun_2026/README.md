# Yeniden Çalıştırma Kaydı (19 Kasım 2026)

Bu klasör, Bank Marketing veri kümesi üzerinde gerçekleştirilen MLP deneyinin yeniden çalıştırılmasına ait kayıtları içerir. Önceki deneyin dosyaları ve GitHub geçmişi korunmuştur. Bu yeniden çalıştırma, önceki test sonuçlarının zaten görülmüş olduğu gerçeğini değiştirmez; bu nedenle tamamen kör bir ilk test değerlendirmesi olarak sunulmaz.

## GitHub commit sırası (UTC)

1. **6ad4290618d3** — 13:14:25: Test etiketlerini içermeyen tahminler ve nihai hiperparametreler kaydedildi.
2. **ce18e64b4f7e** — 13:16:56: Yeniden çalıştırmaya ait Notebook kaydedildi.
3. **a0e7b8827037** — 13:22:14: Bağımsız test değerlendirmesi çıktı dosyaları kaydedildi.

Bu sıra, yeniden çalıştırmaya ait tahminlerin, yapılandırmanın ve Notebook dosyasının test sonuçlarının GitHub'a yüklenmesinden önce commit edildiğini gösterir. Notebook dosyası önceki çalıştırmadan kaydedilmiş çıktı hücreleri de içerebilir; commit zamanları tek başına testin daha önce görülmediğini kanıtlamaz. Test sonuçlarına bakılarak yeni hiperparametre seçimi yapılmamıştır.

## Dosyalar

- `test_predictions_locked (4).csv`: Test etiketlerini içermeyen, üç seed için kilitli tahminler.
- `final_hyperparameters (1).json`: Nihai MLP yapılandırması (M5, AdamW, 64–32 gizli katmanlar, seed 14928).
- `MLP_Midterm_14928_Colab (2).ipynb`: Yeniden çalıştırma için kaydedilen Notebook.
- `test_metrics.csv`: Üç MLP seed ve karşılaştırma modellerinin test metrikleri.
- `bootstrap_ci.csv`: Ana modelin %95 bootstrap güven aralıkları.
- `seed_stability_results.csv`: Seed kararlılığı sonuçları.
- `error_analysis.csv`: Yanlış pozitif ve yanlış negatif sayıları.

## Test sonuçlarının özeti

Ana model (`MLP_seed_14928`): **AP = 0.446868**, **ROC-AUC = 0.800590**, **F1 = 0.346457**, **Sensitivity = 0.244444**.

Bootstrap %95 güven aralıkları: AP [0.351958, 0.559705], ROC-AUC [0.751199, 0.852050], F1 [0.234319, 0.446285].

Testte 15 yanlış pozitif ve 68 yanlış negatif kaydedilmiştir. Düşük duyarlılık, pozitif sınıfın önemli bir bölümünün tespit edilemediğini göstermektedir.

Ana proje raporu ve diğer deney dosyaları depo kök dizinindeki `report.pdf`, `results/` ve `figures/` klasörlerindedir.
