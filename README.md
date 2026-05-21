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
