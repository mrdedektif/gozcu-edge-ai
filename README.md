# Gömülü Sistem Tabanlı Yapay Zekâ Destekli Akıllı Gözetim Sistemi
Bu proje; **Raspberry Pi** platformu üzerinde çalışan, çoklu sensör füzyonu ve ardışık tetikleme mekanizmalarıyla donatılmış, yüksek enerji verimliliğine sahip bir **Uç Uç Yapay Zekâ (Edge-AI)** akıllı gözetim mimarisidir. 

Geleneksel CCTV sistemlerinin sürekli kayıt, yüksek depolama/bant genişliği maliyeti ve insan gözetimine bağımlılık gibi kısıtlamalarını; **Hareket**, **Mesafe** ve **Kamera (Görsel Doğrulama)** verilerini ağırlıklı bir güven skoru algoritmasıyla birleştirerek ortadan kaldırır.

---

## 🔬 Literatürden Farkı ve İnovasyon Değeri

Literatürdeki çalışmalar (örneğin *Noutele, 2024*) çoğunlukla tekil sensör tetiklemesine veya doğrudan kameraya dayalı sürekli nesne tanımaya (YOLOv5 vb.) odaklanmaktadır. Bu projenin özgün değerleri şunlardır:
1. **Ardışık Katmanlı Tetikleme:** Kamera modülü sürekli açık kalmaz. PIR hareket algılar -> Ultrasonik sensör mesafe doğrulaması yapar -> Kamera uyanır. Bu sayede maksimum enerji verimliliği sağlanır.
2. **Güven Skoru (Confidence Score) Algoritması:** Her bir sensör katmanına ve yapay zekâ modeline belirli bir ağırlık katsayısı atanır. Toplam güven skoru belirlenen eşik değeri ($W_{threshold}$) aşarsa nihai karar mekanizması (bildirim ve bulut kaydı) tetiklenir. Bu yöntem, yanlış alarm oranını (False Positive) minimize eder.

---

## 🚀 Sistem Mimarisi ve Karar Akışı

Sistemin çalışma mantığı aşağıdaki ardışık akış şemasına dayanmaktadır:

Çok Yakında....

---

## 🛠️ Donanım ve Entegrasyon Katmanı

| Bileşen | Seçilen Donanım | Sistemdeki Görevi / Fonksiyonu |
| :--- | :--- | :--- |
| **Ana İşlem Birimi** | Raspberry Pi | Lokal çıkarım (Inference), sensör okuma ve karar motoru. |
| **Hareket Algılama** | PIR Sensörü  | Geniş açılı ilk hareket tetiklemesi (Sistemi uyandırma). |
| **Mesafe Doğrulama** | Mesafe Sensörü | Algılanan hareketin fiziksel mesafesini doğrulayarak çevresel parazitleri engelleme. |
| **Görsel Doğrulama** | RPi Kamera Modülü (CSI) | İnsan, eylem ve anomali tespiti için yüksek hızlı görüntü yakalama. |
| **Fiziksel Stabilizasyon** | Vibration Damper | Toplu taşıma ve dinamik ortamlarda sarsıntı kaynaklı görüntü bozulmalarını önleme. |

---
## 🧠 4. Görüntü İşleme ve Nesne Tanıma Stratejisi

Kamera modülünden elde edilen veriler, donanım kaynaklarını optimize etmek amacıyla hafif derin öğrenme modelleri kullanılarak sınır bilişim (Edge-AI) yaklaşımıyla işlenir:

* **Model Alternatifleri:** TensorFlow Lite, YOLOv5-Nano,MobileNet veya alternatif mimariler.
* **Algılama Aşamaları:** Görüntü üzerinde öncelikle **insan tespiti** yapılır. İnsan doğrulandığı anda paralel olarak **eylem ve anomali tespiti** modülleri tetiklenir.
* **Tehdit Tanımı:** Toplum güvenliği, ev/ofis ihlalleri, tehlikeli malzeme tespiti (ateşli silahlar, bıçak, bomba...) ve şüpheli paket anomalileri bu kapsamda analiz edilir.

---

## 📚 7. Kaynakça
* Margapuri, V. (2020). Smart motion detection system using Raspberry Pi. arXiv preprint arXiv:2006.06442.
* Raavi, P., & Panchangam, H. (2020). Camera Surveillance Using Raspberry Pi. International Research Journal of Engineering and Technology (IRJET), 7(05).
* Namdeo, R., Sharma, S., Anand, V., & Lohi, C. (2020). Smart Automated Surveillance System using Raspberry Pi. International Journal of Recent Technology and Engineering (IJRTE), 9(2), 308-311.
* Mhaiskar, P., Lanjewar, V., Shambharkar, S., Bhude, S., Sharma, S., & Kalbande, M. (2022, May). Automated Surveillance System using Raspberry pi. In 2022 International Conference on Applied Artificial Intelligence and Computing (ICAAIC) (pp. 1473-1476). IEEE.
* NOUTELE, G. (2024). Using IoT and YOLOv5 for real-time security monitoring of homes.
* Rathour, N., Gehlot, Y., Gurung, A., Kundu, S. S., Kumar, V., & Pandey, P. S. (2024, December). Advanced Security with YOLO Object Detection Using Raspberry Pi. In 2024 International Conference on Emerging Technologies and Innovation for Sustainability (EmergIN) (pp. 214-218). IEEE.
