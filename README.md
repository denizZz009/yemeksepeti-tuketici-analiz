# Yemeksepeti Tuketici ve Strateji Analizi Projesi
<img width="1399" height="904" alt="Screenshot_1" src="https://github.com/user-attachments/assets/d3ddb2c3-8d44-47ea-9876-394dab6b4fd1" />
## Proje Özeti
Bu proje, Türkiye'nin önde gelen çevrimiçi yemek ve market sipariş platformlarından biri olan Yemeksepeti'ne yönelik kullanıcı geri bildirimlerini analiz etmek amacıyla geliştirilmiş kapsamlı bir veri madenciliği ve yapay zeka çalışmasıdır. Proje kapsamında, Şikayetvar, Google Play Store, App Store ve Ekşi Sözlük gibi çeşitli platformlardan toplanan **29.000'den fazla kullanıcı yorumu** (Veri seti: `yemeksepeti_cleaned_data.csv`), Doğal Dil İşleme (NLP) ve Büyük Dil Modelleri (LLM) kullanılarak incelenmiştir.

Çalışmanın temel amacı, ham kullanıcı verilerini stratejik iş zekasına dönüştürmektir. Geliştirilen analiz hattı (pipeline), her bir yorumu **Churn Riski (Müşteri Kaybı)**, **Duygu Durumu**, **Şikayet Kategorisi** ve **Rakip Analizi** gibi çok boyutlu metriklerle etiketleyerek, marka sağlığına dair derinlemesine içgörüler sunmaktadır.

## Metodoloji

### 1. Veri Toplama (Data Scraping)
Veriler, platformlara özgü geliştirilen Python tabanlı "scraper" algoritmaları ile toplanmıştır. Dinamik web sayfalarından veri çekme, anti-bot korumalarını (429 Rate Limiting) yönetme ve eksik veri tamamlama (Bypass teknikleri) konularında optimize edilmiştir.
- **Kaynaklar:** Şikayetvar, Google Play, App Store, Ekşi Sözlük.
- **Kapsam:** Yapılandırılmamış metin verileri (yorumlar), meta veriler (tarih, yazar, puan).

### 2. Yapay Zeka Tabanlı Analiz
Toplanan veriler,DEOK AI modeli ile entegre edilen `analiz` betiği aracılığıyla işlenmiştir. Her veri bloğu, stratejik bir "Business Analyst" perspektifiyle hazırlanmış özel "Prompt Mühendisliği" tekniklerine tabi tutulmuştur.
Analiz boyutları şunlardır:
- **Duygu Analizi (Sentiment Analysis):** Memnuniyet, Kızgınlık, Hayal Kırıklığı tespiti.
- **Churn Riski:** Müşterinin platformu terk etme olasılığının (Yüksek/Orta/Düşük) tahmini.
- **Rakip Analizi:** Rakip firmalarla (Getir, Trendyol Yemek vb.) yapılan kıyaslamaların tespiti.
- **Aksiyon Önceliği:** Sorunun işletme üzerindeki finansal ve itibar etkisine göre önceliklendirilmesi.



## Kullanım Alanları

Bu veri seti ve analiz araçları, aşağıdaki alanlarda akademik ve sektörel çalışmalar için kaynak teşkil edebilir:
- **Marka İtibar Yönetimi:** Şikayet trendlerinin zaman serisi analizi.
- **Rakip İstihbaratı:** Pazar payı geçişlerinin nedenlerinin irdelenmesi.
- **Müşteri Deneyimi (CX):** Operasyonel darboğazların (kurye, iade, sıcaklık vb.) tespiti.
- **NLP Çalışmaları:** Türkçe metinlerde duygu analizi ve sınıflandırma modellerinin eğitimi.

## Lisans ve Yasal Uyarı
Bu proje kapsamında paylaşılan veriler, kamuya açık kaynaklardan derlenmiştir. Veri setindeki kişisel tanımlayıcı bilgiler (kullanıcı adları), KVKK ve etik standartlar gereği **anonimleştirilmiştir** (`[Kullanıcı Adı Gizlendi]`). Veriler sadece eğitim ve araştırma amaçlı kullanılmalıdır.
