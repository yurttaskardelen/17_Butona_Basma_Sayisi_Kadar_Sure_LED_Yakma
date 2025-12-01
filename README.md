# 17_Butona_Basma_Sayisi_Kadar_Sure_LED_Yakma (Count to Duration)

Bu proje, **STM32F407-Discovery** kartı üzerinde butona kaçıncı kez basıldığına bağlı olarak LED'in yanma süresini dinamik olarak değiştiren bir uygulamadır.

Bu depo, bir değişkenin hem **sayaç** (kaç kere basıldı?) hem de **zamanlayıcı çarpanı** (kaç saniye yanacak?) olarak nasıl verimli kullanılabileceğini gösterir.

---

### 🎯 Proje Senaryosu

Sistem "kademeli" bir yapıya sahiptir. Her basışta süre uzar ve belirli bir sınırdan sonra sıfırlanır.

1.  **1. Basış:**
    * Sayaç = 1.
    * LED **1 saniye** (`1 * 1000ms`) boyunca yanar ve söner.
2.  **2. Basış:**
    * Sayaç = 2.
    * LED **2 saniye** (`2 * 1000ms`) boyunca yanar ve söner.
3.  **3. Basış:**
    * Sayaç = 3.
    * LED **3 saniye** (`3 * 1000ms`) boyunca yanar ve söner.
    * **Sıfırlama:** Sayaç 0'a eşitlenir. Bir sonraki basışta döngü 1. saniyeden başlar.

---

### ⚙️ Pull-Up Konfigürasyonu

Projenin düzgün çalışması için `.ioc` dosyasında buton pininin (`PA0`) **Pull-Up** olarak ayarlanması gereklidir.

* **Pin:** `PA0` -> `GPIO_Input`
* **Resistor:** `Pull-up`

<img width="843" height="644" alt="image" src="https://github.com/user-attachments/assets/a5bccc60-b813-4f18-9e9a-a4f0fd3519bf" />
---

### 🛠️ Gerekli Donanım

* **1x** STM32F407-Discovery Geliştirme Kartı
* **1x** LED
* **1x** 220 Ohm Direnç
* **1x** Push-Button
* **Breadboard ve Jumper Kablolar**


---

### 🔌 Devre Şeması

Buton bağlantısı **Pull-Up** mantığına göre (GND'ye) yapılmalıdır.

| Bileşen | STM32 Pini | Bağlantı Detayı |
| :--- | :--- | :--- |
| **Buton** | `PA0` | Bir bacak **PA0**, diğer bacak **GND** |
| **LED** | `PA1` | Anot -> **PA1**, Katot -> Direnç -> **GND** |

<img width="346" height="480" alt="image" src="https://github.com/user-attachments/assets/5b2998e0-3e4e-4f1a-84cc-8264f9fee38a" />

---

### 💻 Kod Bloğu

<img width="1052" height="819" alt="image" src="https://github.com/user-attachments/assets/dde9f82b-6fa5-454d-9629-3609be2bf8a2" />

---
### 🚀 Nasıl Kullanılır?

1.  Bu depoyu klonlayın (`git clone ...`).
2.  STM32CubeIDE yazılımını açın.
3.  `File > Open Projects from File System...` seçeneği ile proje klasörünü seçin.
4.  Proje içindeki `.ioc` dosyasını açarak pin yapılandırmasını inceleyebilirsiniz.
5.  Derleyin (Build) ve ST-Link V2 üzerinden kartınıza yükleyin (Run).
