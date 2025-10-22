# 🔬 Deri Lezyonu Sınıflandırma Projesi: Dengesiz Veri Seti Optimizasyonu

## 1. Proje Özeti 

Bu proje, Kaggle'dan alınan Skin Cancer Detection with CNNs – HAM10000 Dataset'ni kullanarak yedi farklı deri lezyonu sınıfını (akiec, mel, nv, vb.) sınıflandırmayı amaçlamaktadır. Projenin ana zorluğu, **Nevus (nv)** sınıfının baskın olduğu ciddi sınıf dengesizliğiydi. Bu sorun, `Class Weighting` ve `Macro F1 Score` takibi ile çözülmüştür.

## 2. Geliştirme Süreci ve Optimizasyon

Modelin sadece baskın sınıfı tahmin etme önyargısını gidermek için kritik teknikler uygulanmıştır:

1.  **Veri Dengeleme:** `Class Weighting` veya `Oversampling` yöntemi uygulanmıştır.
2.  **Doğru Metrik Takibi:** Yanıltıcı `Accuracy` yerine, tüm sınıfların performansını yansıtan **`Macro F1 Score`** ana metrik olarak belirlenmiştir.
3.  **Öğrenme Hızı Optimizasyonu:** Modelin kararlı öğrenmesi için **Learning Rate $0.00001$** değerine düşürülmüştür.

## 3. Ana Çıktılar (Confusion Matrix ve Grafikler)

Aşağıdaki çıktılar, modelin dengeleme sonrası performansını göstermektedir:

### A. Nihai Confusion Matrix
<img width="801" height="673" alt="Ekran görüntüsü 2025-10-22 162913" src="https://github.com/user-attachments/assets/d4eec5a2-1541-4511-8e9a-c497b3525ed9" />
 

### B. Loss ve Accuracy Grafikleri
<img width="1241" height="453" alt="Ekran görüntüsü 2025-10-22 163104" src="https://github.com/user-attachments/assets/0beae635-97be-4d74-8eec-ed5c0871d39f" />


## 5. Geliştirme Önerileri

Bu model, azınlık sınıflarında yüksek F1 skoru elde etse de, gelecekteki geliştirmeler şunları içerebilir:

1.  **Transfer Öğrenme:** Daha büyük ve önceden eğitilmiş bir model (ResNet, VGG) kullanarak öznitelik çıkarma gücünü artırmak.
2.  **Daha Agresif Optimizasyon:** Keras Tuner gibi otomatik araçlarla **Batch Size** ve **Kernel Boyutları** üzerinde sistematik denemeler yapmak.
3.  **TTA (Test Time Augmentation):** Tahmin aşamasında da veri artırma uygulayarak tahmin kararlılığını artırmak.
