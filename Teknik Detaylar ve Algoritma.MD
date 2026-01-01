# Teknik Detaylar ve Algoritma Dokümantasyonu

Bu belge, Yemeksepeti Tüketici ve Strateji Analizi projesinin teknik altyapısını, kullanılan algoritmaları ve veri şemalarını detaylandırmaktadır.


## 1. Yapay Zeka Analiz Motoru (`DEOK AI - analiz`)

Projenin çekirdeğini oluşturan analiz motoru, DEOK AI modeli üzerine kurgulanmıştır. Bu modül, ham metin verilerini yapılandırılmış JSON formatına dönüştürür.

### Prompt Mühendisliği (Prompt Engineering)
Modelin bir "Halkla İlişkiler Uzmanı" ve "Stratejik İş Analisti" personasına bürünmesi sağlanmıştır. Analiz şu parametrelere göre yapılandırılmıştır:

1.  **Sorun Kategorizasyonu:** Yorumlar, önceden tanımlanmış 15+ kategoriye (Örn: `Teslimat Operasyonu`, `Finans: İade Süreçleri`, `Market: Kalite Kontrolü`) göre sınıflandırılır.
2.  **Churn (Terk) Riski:** Model, kullanıcının markayı bırakma ihtimalini şu lojik ile hesaplar:
    *   *Yüksek:* Rakip övgüsü + Birden fazla kritik sorun.
    *   *Orta:* Sadece rakip isminin geçmesi.
    *   *Düşük:* Tekil ve çözülebilir sorun.
3.  **Aksiyon Önceliği:** Finansal kayıp ve marka imajı üzerindeki potansiyel etkiye göre `Kritik`, `Yüksek`, `Orta`, `Düşük` olarak derecelendirilir.

### Veri İşleme Akışı
*   **Ön İşleme:** Metinlerdeki satır sonları ve bozucu karakterler temizlenir.
*   **Batch Processing:** API kotalarını verimli kullanmak için veriler 60'arlı gruplar (batch) halinde modele gönderilir.
*   **Hata Toleransı:** JSON decode hataları veya API kesintileri durumunda, ilgili batch için "Retry" mekanizması devreye girer.


## 2. Veri Sözlüğü (Data Dictionary)

Paylaşılan CSV dosyalarındaki kritik sütunların teknik tanımları aşağıdadır:

| Sütun Adı | Veri Tipi | Açıklama |
| :--- | :--- | :--- |
| `id` | Integer | Kaydın benzersiz tanımlayıcısı. |
| `author` | String | Yorum sahibinin kullanıcı adı (Anonimleştirilmiş). |
| `title` | String | Şikayet veya yorumun başlığı. |
| `content` | String | Yorumun tam metni. |
| `ai_puan` | Integer (1-10) | AI tarafından atanan genel memnuniyet skoru (1: En kötü, 10: En iyi). |
| `churn_risk_seviyesi` | Categorical | Müşteri kaybı riski (`Yüksek`, `Orta`, `Düşük`, `Yok`). |
| `hizmet_tipi` | Categorical | Hizmetin türü (`Yemek`, `Market`, `Genel`). |
| `kategori` | Categorical | Tespit edilen ana sorun kategorisi. |
| `rakip` | String | Yorumda bahsedilen rakip firma adı (yoksa 'Yok'). |
| `oncelik_skoru` | Categorical | Aksiyon alma aciliyeti (`Kritik` -> `Düşük`). |
