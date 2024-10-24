# ANN-CLASSIFICATION-
🐟 Yapay Sinir Ağı (ANN) ile Balık Sınıflandırma
Bu repo, yapay sinir ağı (ANN) modeli kullanarak balık türlerini sınıflandıran bir projeyi içermektedir. Veri seti, farklı balık türlerinin görüntülerini içerir ve derin öğrenme teknikleri kullanarak, verilen bir balık görüntüsünün türünü doğru bir şekilde tahmin eden bir model eğitilmiştir.

📊 Genel Bakış
Yapay Sinir Ağları (ANN), insan beyninin çalışma prensiplerini taklit eden güçlü makine öğrenimi algoritmalarıdır. Bu ağlar, veriyi işleyen ve öğrenen birbirine bağlı katmanlardan oluşur. Bu projede, ANN'yi görüntü sınıflandırma görevleri için kullandık; özellikle, görüntülerdeki balık türlerini doğru bir şekilde sınıflandırmayı amaçladık.

Model, geniş bir balık veri seti üzerinde eğitildi ve doğrulandı, daha yüksek doğruluk ve genelleme kabiliyeti elde etmek için çeşitli iyileştirmeler yapıldı.

🚀 Proje Özellikleri
Veri Artırımı (Data Augmentation): Eğitim veri setinin boyutunu yapay olarak artırmak için kullanıldı. Bu sayede modelin yeni, daha önce görülmemiş görüntülere karşı genelleme yeteneği geliştirildi.
Dropout Katmanları: Aşırı öğrenmeyi (overfitting) önlemek amacıyla bazı nöronların rastgele kapatıldığı dropout katmanları eklendi. Bu sayede model, belirli özelliklere aşırı bağımlı hale gelmedi.
Erken Durdurma (Early Stopping): Doğrulama kaybı iyileşmeyi bıraktığında eğitimi durdurarak modelin aşırı öğrenmesini engelledik.
Öğrenme Hızı Zamanlayıcısı (Learning Rate Scheduler): Öğrenme hızını eğitim sırasında dinamik olarak ayarlayarak, modelin performansının durağanlaştığı anlarda daha ince ayarlarla öğrenme yapmasını sağladık.
🛠️ Gereksinimler
Bu proje, aşağıdaki Python kütüphanelerini kullanmaktadır:

tensorflow: Sinir ağını oluşturmak ve eğitmek için
pandas: Veri manipülasyonu ve ön işleme için
numpy: Sayısal hesaplamalar için
sklearn: Veri bölme ve değerlendirme metrikleri için
matplotlib & seaborn: Veri görselleştirme ve sonuç grafikleme için
Gereksinimleri yüklemek için:

bash
Kodu kopyala
pip install -r requirements.txt

📁 Veri Seti
Bu projede kullanılan veri seti, çeşitli balık türlerinin görüntülerini içerir. Bu görüntüler, dosya yolları ve her bir görüntünün etiketi ile pandas DataFrame yapısında organize edilmiştir.

Eğitim-Test Bölmesi
Veri seti, %80 eğitim ve %20 test seti olarak bölünmüştür. Ayrıca, eğitim verilerinin %20’si doğrulama verisi olarak kullanılmıştır.

🧠 Model Mimarisi
ANN modelimiz, ReLU aktivasyon fonksiyonlarına sahip birkaç yoğun katmandan, batch normalization katmanlarından ve regularizasyon amacıyla dropout katmanlarından oluşmaktadır. Son katman ise sınıf olasılıklarını hesaplayan softmax fonksiyonu ile çıkış verir.

python
Kodu kopyala
model = tf.keras.Sequential([
    tf.keras.layers.Flatten(input_shape=(224, 224, 3)),
    tf.keras.layers.Dense(516, activation='relu'),
    tf.keras.layers.BatchNormalization(),
    tf.keras.layers.Dropout(0.5),
    tf.keras.layers.Dense(224, activation='relu'),
    tf.keras.layers.BatchNormalization(),
    tf.keras.layers.Dropout(0.5),
    tf.keras.layers.Dense(128, activation='relu'),
    tf.keras.layers.Dense(9, activation='softmax')  # 9 sınıf için çıkış
])

🎯 Değerlendirme
Model, doğruluk (accuracy), kayıp (loss) ve karışıklık matrisi (confusion matrix) gibi metriklerle değerlendirildi. Test verileri üzerinde aşağıdaki sonuçlar elde edilmiştir:

Test Doğruluğu: Model, test verileri üzerinde yüksek doğruluk oranına ulaşmıştır.
Karışıklık Matrisi: Yanlış sınıflandırmaları görselleştirerek, hangi balık türlerinin ayırt edilmesinin zor olduğunu gözlemledik.
📈 Görselleştirmeler
Aşağıdaki detaylı grafikleri sunduk:

Eğitim ve doğrulama kayıplarının epoch’lar boyunca değişimi
Eğitim ve doğrulama doğruluğunun epoch’lar boyunca değişimi
Karışıklık matrisi
Bu görselleştirmeler, modelin performansını anlamaya ve iyileştirme alanlarını tespit etmeye yardımcı olmaktadır.

📦 Kullanım
Repoyu klonlayın:
bash
Kodu kopyala
git clone https://github.com/kullanici-adi/Fish-Classification-ANN.git
Gerekli kütüphaneleri yükleyin:
bash
Kodu kopyala
pip install -r requirements.txt
Veri setini indirip, kodda açıklandığı gibi organize edin.

Jupyter Notebook’u veya Python dosyalarını çalıştırarak modeli eğitip değerlendirin.

📝 Lisans
Bu proje MIT Lisansı altında lisanslanmıştır - detaylar için LICENSE dosyasına bakabilirsiniz.

🤝 Katkıda Bulunma
Projeye katkıda bulunmak için repoyu fork edebilir, pull request gönderebilir veya sorun bildirebilirsiniz.

