# 📋 prd.md — Yâdigâr AI Ürün Gereksinim Belgesi (PRD)

> **Versiyon:** 2.0  
> **Proje:** Yâdigâr AI — Dijital Refakatçi  
> **Hedef Platform:** Web (tek dosya HTML uygulaması)  
> **Teknoloji:** Vanilla JS + Gemini API (Google AI Studio)

---

## 1. Ürün Özeti

Yâdigâr AI, Alzheimer hastaları ve yalnız yaşayan yaşlı bireyler için tasarlanmış kişiselleştirilmiş bir yapay zekâ refakatçisidir. Uygulama; hasta profilini öğrenir, tetikleyici kelimelerden kaçınır, duygusal bağ kurar, acil durumlarda yakınlara otomatik bildirim gönderir ve hastalık ilerleme riskini takip eder. Tüm bu işlevler tek bir HTML dosyasında çalışır; kurulum gerektirmez.

---

## 2. Hedef Kullanıcılar

| Kullanıcı Tipi | Açıklama |
|---|---|
| Birincil | Erken–orta evre Alzheimer hastaları, yalnız yaşayan yaşlı bireyler |
| İkincil | Hasta yakınları, bakıcılar |
| Üçüncül | Sağlık profesyonelleri (ilerleme verisi için) |

---

## 3. Temel Özellikler (MVP Kapsamı)

### 3.1 Hasta Profili Kurulumu
- **Ne yapar:** Kullanıcı ilk açılışta hasta bilgilerini girer.
- **Alanlar:**
  - Ad Soyad, Yaş, Kan Grubu
  - Mevcut hastalıklar ve kullandığı ilaçlar
  - Tetikleyici / kullanılmaması gereken kelimeler (virgülle ayrılmış liste)
  - Aile bireyleri: isim + telefon numarası (birden fazla eklenebilir)
  - Gemini API anahtarı
- **Depolama:** `localStorage` (tarayıcıda yerel, sunucu gerekmez)
- **Kabul kriteri:** Form doldurulup kaydedilince sohbet ekranı açılır.

### 3.2 AI Sohbet Ekranı
- **Ne yapar:** Hasta ile Gemini API aracılığıyla kişiselleştirilmiş konuşma yürütür.
- **Sistem promptu şunları içerir:**
  - Hasta adı, yaşı ve profil bilgileri
  - Yasaklı kelime listesi (AI bu kelimeleri kesinlikle kullanmaz)
  - Aile bireylerinin adları (AI proaktif hatırlatma yapar)
  - Konuşma tonu kuralları: kısa cümleler, sabırlı dil, sevgi dolu üslup
- **Tehlike sinyali tespiti:** Yanıtta "kayboldum", "yardım", "ağrı", "düştüm", "korktum" gibi anahtar ifadeler algılanırsa acil bildirim tetiklenir.
- **Kabul kriteri:** AI yanıtları hiçbir koşulda yasaklı kelimeleri içermez; her yanıt 2–4 cümleyi geçmez.

### 3.3 Acil Bildirim Sistemi
- **Ne yapar:** Tehlike sinyali algılandığında kayıtlı yakın numaralarına hazır mesaj içeriği gösterir.
- **Akış:**
  1. Tehlike sinyali tespit edilir.
  2. Ekranda büyük kırmızı uyarı kartı açılır.
  3. Her yakın için "WhatsApp'ta Mesaj Gönder" düğmesi görüntülenir (wa.me linki).
  4. Kullanıcı veya yakın onaylayana kadar kart ekranda kalır.
- **Not:** SMS gönderimi tarayıcı kısıtlamaları nedeniyle WhatsApp Web yönlendirmesi olarak uygulanır. Gerçek SMS için ileride Twilio entegrasyonu planlanmaktadır.
- **Kabul kriteri:** Tehlike ifadesinden sonra 1 saniye içinde uyarı kartı görünür.

### 3.4 İlerleme Takibi (Unutulanlar)
- **Ne yapar:** Sohbetlerde tespit edilen bilişsel kayıpları kaydeder ve görselleştirir.
- **Kayıt mantığı:** AI yanıtı analiz edilir; hastanın yakınını hatırlayıp hatırlamadığı, tarih/gün bilgisini bilip bilmediği ve konuşma tutarlılığı değerlendirilir.
- **Risk skoru:** Her sohbet sonunda 0–100 arası risk skoru hesaplanır (düşük / orta / yüksek).
- **Grafik:** Chart.js ile son 7 günün risk skorları çizgi grafik olarak gösterilir.
- **Kabul kriteri:** Sohbet bittikten sonra risk skoru otomatik kaydedilir ve grafik güncellenir.

### 3.5 Hamburger Menü Navigasyonu
Uygulama üç ana bölümden oluşur:

| Menü Öğesi | İçerik |
|---|---|
| 💬 Ana Menü | AI sohbet ekranı (varsayılan açılış ekranı) |
| 👤 Hesabım | Hasta profili formu, yakın bilgileri, API anahtarı |
| 📊 Unutulanlar | İlerleme grafiği, günlük risk skorları, hafıza egzersiz önerileri |

---

## 4. Teknik Gereksinimler

| Gereksinim | Detay |
|---|---|
| Platform | Tek dosya HTML (features/index.html) |
| Harici bağımlılık | Gemini API (Google AI Studio) |
| Veri depolama | `localStorage` (sunucu yok, hesap yok) |
| Grafik kütüphanesi | Chart.js (CDN) |
| İkon kütüphanesi | Font Awesome veya Heroicons (CDN) |
| CSS framework | Vanilla CSS (mobil uyumlu, büyük yazı boyutu) |
| Tarayıcı desteği | Chrome 90+, Firefox 88+, Safari 14+ |
| Mobil uyumluluk | Zorunlu — kullanıcılar tablet/telefon kullanabilir |

---

## 5. Kullanıcı Akışı

```
Uygulama Açılır
      │
      ▼
[Profil dolu mu?] ──Hayır──▶ Hasta Profili Formu ──▶ Kaydet
      │ Evet
      ▼
Sohbet Ekranı (AI)
      │
      ├──▶ Kullanıcı mesaj yazar
      │         │
      │         ▼
      │    Gemini API'ye gönderilir (sistem promptu + profil + geçmiş)
      │         │
      │         ▼
      │    Yanıt analiz edilir
      │         │
      │    [Tehlike sinyali var mı?]
      │         ├── Evet ──▶ Acil Uyarı Kartı + WhatsApp Linki
      │         └── Hayır ──▶ Yanıt ekrana yazdırılır
      │                          │
      │                          ▼
      │                   Risk skoru hesaplanır → localStorage'a kaydedilir
      │
      ├──▶ Hamburger Menü → Hesabım (profil düzenleme)
      └──▶ Hamburger Menü → Unutulanlar (grafik + egzersizler)
```

---

## 6. Ekran Tasarımı (Wireframe Açıklamaları)

### Ekran 1: Hasta Profili Formu
- Üstte logo + "Yâdigâr AI" başlığı
- Bölüm 1: Temel Bilgiler (ad, yaş, kan grubu)
- Bölüm 2: Sağlık Bilgileri (hastalıklar, ilaçlar)
- Bölüm 3: Yasaklı Kelimeler (etiket giriş alanı)
- Bölüm 4: Yakınlar (dinamik liste: isim + telefon + ekle butonu)
- Bölüm 5: API Anahtarı (şifreli input)
- Alt: "Kaydet ve Başla" butonu

### Ekran 2: Sohbet Ekranı
- Üstte hamburger menü ikonu (sol) + "Yâdigâr" logo (orta)
- Mesaj baloncukları (AI solda, kullanıcı sağda)
- Alt: Metin giriş alanı + Gönder butonu + mikrofon ikonu
- Acil durum: Tam ekranı kaplayan kırmızı modal kart

### Ekran 3: Unutulanlar
- Başlık: "Bilişsel İlerleme Takibi"
- Chart.js çizgi grafiği (son 7 gün risk skoru)
- Risk seviyesi rozeti (Düşük / Orta / Yüksek)
- Hafıza egzersiz önerileri listesi (3 madde)

---

## 7. Kapsam Dışı (Bu Versiyonda Yok)

- Gerçek SMS gönderimi (Twilio)
- Çoklu dil desteği
- Bulut veri senkronizasyonu
- Ses ile giriş (Web Speech API — gelecek versiyon)
- Doktor paneli / klinik raporlama modülü
- Kullanıcı hesabı / oturum sistemi

---

## 8. Başarı Kriterleri

| Kriter | Ölçüm Yöntemi |
|---|---|
| AI hiçbir koşulda yasaklı kelime kullanmaz | Manuel test: 10 farklı senaryo |
| Tehlike sinyalinden sonra uyarı kartı 1 sn içinde açılır | Tarayıcı console timer |
| Profil verisi uygulama yeniden açıldığında kayıplı değil | localStorage.getItem kontrolü |
| Sohbet geçmişi oturum boyunca korunur | Sayfa yenileme testi |
| Mobil ekranda tüm alanlar erişilebilir | Chrome DevTools mobil simülasyon |

---

## 9. Riskler ve Azaltma Stratejileri

| Risk | Olasılık | Azaltma |
|---|---|---|
| Gemini API anahtarı geçersiz / kotası dolu | Orta | Kullanıcıya açık hata mesajı + API ayar ekranına yönlendirme |
| localStorage temizlenirse veri kaybolur | Düşük | Profil export/import özelliği (v2.1 planı) |
| Tetikleyici kelime listesi yetersiz | Orta | Kullanıcıya her zaman düzenlenebilir liste |
| Hasta yanlışlıkla formu sıfırlarsa | Düşük | "Emin misiniz?" onay dialogu |

---

> 📌 Bu PRD, Yâdigâr AI v2 geliştirme sürecinin referans belgesidir. Özellik öncelikleri ve kapsam değişiklikleri için bu belge güncellenir.
