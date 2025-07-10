# makine-ariza-tahmini
# Makine Arıza Tahmini — Zaman Serisi ve ML Tabanlı Yaklaşım

Bu proje, endüstriyel makine verilerini kullanarak **makine arızası tahmini (Failure_Occurrence)** yapmayı hedefler. Zaman serisi analizleri ve makine öğrenmesi algoritmaları kullanılarak, arıza gerçekleşmeden önce uyarı sistemleri oluşturmak amaçlanmıştır.

## Proje Yapısı

makine-ariza-tahmini/
│
├── Train.ipynb          # Eğitim veri hazırlığı, SMOTE, model eğitimi
├── Test.ipynb           # Kaydedilen modellerle test verisi değerlendirme
├── models/
│   ├── rf_model.joblib
│   ├── xgb_model.joblib
│   ├── mlp_model.joblib
│   └── scaler.joblib
├── README.md            # Bu belge

# Kullanılan Veri Seti
Veri Seti: Siemens Industrial Machine Sensor Dataset
Kaynak: Kaggle Linki
Kapsam: ~1.5 milyon zaman serisi kaydı, 30+ sensör & operasyonel değişken
Hedef Değişken: Failure_Occurrence (0: Arıza yok, 1: Arıza var)
Zorluk: Dengesiz sınıf dağılımı (minority: arıza durumları)

# Uygulanan Yöntemler
Özellik Seçimi & Girdi Hazırlığı
Saatlik zaman serisi verisi
Sliding window tekniği (window size = 6)
Korelasyon temelli değişken seçimi
Dengeleme
SMOTE ile sınıf dengesizliğinin giderilmesi (sadece eğitim setinde)

# Modeller
+ Random Forest
+ XGBoost
+ MLP (Multilayer Perceptron)
+ Ensemble (RF + XGB + MLP)

# Performans Değerlendirme
F1-Score, Recall, Confusion Matrix
En iyi eşik değeri (threshold) her model için find_best_threshold() fonksiyonu ile belirlenmiştir.

 # Nasıl Kullanılır?
Train.ipynb dosyasını çalıştırarak veri hazırlığı, dengeleme ve model eğitimi yapılabilir.
Eğitim sonrası modeller joblib ile models/ klasörüne kaydedilir.
Test.ipynb dosyası ile test verisi üzerinden tüm modeller değerlendirilir.
En iyi eşik değeri otomatik belirlenerek sınıflandırma yapılır.

