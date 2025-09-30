# Paclitaxel Doz Hesaplayıcı

*Canlı Uygulama:*  
👉 [Paclitaxel Dose Calculator Web App](https://nisa439.github.io/ONKOLOJIDE-3T-TEKNOFEST/)  

Bu proje, *Paclitaxel ilacının farklı kanser hücre hatlarındaki optimal dozunu tahmin etmek* amacıyla geliştirilmiş bir yapay zekâ tabanlı araştırma prototipidir. Sistem, hücre bazında *IC50 hesaplama, **%50–%90 arası etkililik seviyeleri için doz önerileri* ve *doz–yanıt eğrilerinin görselleştirilmesi* işlevlerini sağlamaktadır.  
  

---

## 🎯 Amaç
- Paclitaxel’in farklı hücre hatlarındaki doz–yanıt etkisini modellemek  
- IC50 değerlerini hesaplayarak ilaç duyarlılığını belirlemek  
- Hedef etkililik (%50–%90) için önerilen dozları sunmak  
- Kullanıcı dostu web arayüzü ile bu sonuçları erişilebilir kılmak  

---

## 🔬 Metodoloji
1. *Veri Hazırlama:*  
   - 390 hücre hattına ait toplam *4.114 doz–yanıt ölçümü* toplandı.  
   - Eksik değerler temizlendi, log dönüşümleri ve normalizasyon uygulandı.  

2. *Özellik Mühendisliği:*  
   - 16 yeni özellik (ör. log_dose, dose_squared, cell_line_encoded, duyarlılık kategorileri, doz sıralamaları).  
   - Hücre bazlı istatistiksel öznitelikler eklendi.  

3. *Modelleme:*  
   - 6 algoritma denendi: Linear Regression, Random Forest, Gradient Boosting, XGBoost, Neural Network, Ensemble.  
   - Baseline R² ≈ 0.44 → Final Model (NN) R² ≈ 0.88.  
   - 80/20 eğitim–test bölmesi, 5-kat çapraz doğrulama ile güvence altına alındı.  

4. *Model İyileştirme:*  
   - Hiperparametre optimizasyonu (GridSearchCV, RandomizedSearchCV).  
   - Ensemble yöntemleri (Voting, Bagging) test edildi.  

5. *Web Entegrasyonu:*  
   - Final modelin çıktıları JSON formatına aktarıldı.  
   - Web arayüzünde hücre hattı seçimi → hedef etkililik seçimi → önerilen doz çıktısı sağlandı.  

---

## 📊 Model Performansı
- *Baseline Model R²:* 0.44  
- *Final Model (Neural Network) R²:* 0.88  
- *RMSE:* 0.105  
- *Çapraz Doğrulama (5-fold):* R² = 0.8850 ± 0.0068  
- *Veri Boyutu:* 4.114 ölçüm (3.291 eğitim, 823 test)  
- *İyileşme:* %100+  

---

## 🌐 Web Uygulaması
Arayüz özellikleri:  
- Hücre hattına göre IC50 hesaplama  
- %50–%90 etkililik seviyeleri için önerilen dozlar  
- Doz–yanıt eğrilerinin interaktif görselleştirilmesi  
- CSV formatında çıktı alma  

---

## 📂 Proje Yapısı
```text
paclitaxel-dose-calculator/
├── model-development/   # 5 aşamalı ML pipeline (notebooklar)
├── assets/             # CSS ve JSON verileri
├── index.html/              # Web arayüzü

```

---

## 📈 Grafikler
- Veri dağılımları (doz, canlılık)  
- Hücre bazlı doz–yanıt eğrileri  
- Model karşılaştırmaları (R², RMSE)  
- Tahmin–gerçek uyumu ve residual analizleri  
- IC50 dağılımları ve optimal doz hesaplamaları  

👉 Ayrıntılı görseller için:  
https://docs.google.com/document/d/13zcDo6B0BH_SOElQdU4RaMufdT6Y9r2N/edit?usp=drive_link&ouid=104856913755461109286&rtpof=true&sd=true 
