# ✅ tasks.md — Yâdigâr AI Geliştirme Görev Listesi

> Bu liste `prd.md` belgesine dayanılarak hazırlanmıştır.  
> Her görevi tamamladıkça `[ ]` kutusunu `[x]` olarak işaretle.

---

## 🏗️ AŞAMA 1 — Temel Yapı (HTML İskeleti)

- [ ] `features/index.html` dosyasını oluştur
- [ ] `<head>` içine Chart.js ve Font Awesome CDN linklerini ekle
- [ ] Genel CSS değişkenlerini tanımla (renk paleti, font boyutları, boşluklar)
- [ ] Mobil öncelikli (mobile-first) temel CSS yapısını kur
- [ ] Üç ekranı temsil eden div bloklarını oluştur: `#ekran-profil`, `#ekran-sohbet`, `#ekran-unutulanlar`
- [ ] Ekranlar arası geçişi yöneten `showScreen(id)` JavaScript fonksiyonunu yaz

---

## 👤 AŞAMA 2 — Hasta Profili Formu

- [ ] Profil formu HTML'ini oluştur:
  - [ ] Ad Soyad alanı
  - [ ] Yaş alanı
  - [ ] Kan Grubu alanı (dropdown)
  - [ ] Mevcut hastalıklar textarea'sı
  - [ ] Kullandığı ilaçlar textarea'sı
  - [ ] Tetikleyici kelimeler alanı (virgülle ayrılmış)
  - [ ] Yakın ekleme bölümü: isim + telefon + "Ekle" butonu (dinamik liste)
  - [ ] Gemini API anahtarı alanı (type="password")
  - [ ] "Kaydet ve Başla" butonu
- [ ] `saveProfile()` fonksiyonunu yaz — tüm alanları `localStorage`'a kaydet
- [ ] `loadProfile()` fonksiyonunu yaz — sayfa açılışında localStorage'dan profili yükle
- [ ] Uygulama açılışında profil kontrolü yap: profil doluysa sohbet ekranına, boşsa form ekranına yönlendir
- [ ] Yakın ekleme / silme dinamik liste mantığını JavaScript ile yaz
- [ ] Form validasyonu ekle: zorunlu alanlar boş bırakılırsa uyar

---

## 💬 AŞAMA 3 — AI Sohbet Ekranı

- [ ] Sohbet ekranı HTML'ini oluştur:
  - [ ] Üst bar: hamburger menü ikonu (sol) + "Yâdigâr" logosu (orta)
  - [ ] Mesaj listesi alanı (`#mesajlar` div, scroll edilebilir)
  - [ ] Alt bar: metin giriş kutusu + Gönder butonu
- [ ] Mesaj baloncuğu CSS stillerini yaz (AI: sol + farklı renk, kullanıcı: sağ + farklı renk)
- [ ] `buildSystemPrompt()` fonksiyonunu yaz:
  - [ ] localStorage'dan profili oku
  - [ ] Hasta adı, yaşı, hastalıkları, ilaçlarını prompt'a ekle
  - [ ] Yasaklı kelimeleri "Bu kelimeleri ASLA kullanma:" listesi olarak ekle
  - [ ] Yakın isimlerini "Proaktif olarak şu kişileri sor:" olarak ekle
  - [ ] Ton kurallarını ekle: kısa cümle, sabırlı, sevgi dolu, 2-4 cümle maksimum
- [ ] `sendMessage()` fonksiyonunu yaz:
  - [ ] Kullanıcı mesajını ekrana yaz
  - [ ] Sohbet geçmişini dizide tut (role: user/assistant)
  - [ ] Gemini API'ye `fetch` ile POST isteği gönder (sistem promptu + geçmiş + yeni mesaj)
  - [ ] API yanıtını parse et ve ekrana yaz
- [ ] "Gönder" butonuna ve Enter tuşuna `sendMessage()` bağla
- [ ] API isteği sırasında "Yâdigâr yazıyor..." yükleniyor animasyonu göster
- [ ] API anahtarı eksikse kullanıcıyı Hesabım ekranına yönlendir ve uyar

---

## 🆘 AŞAMA 4 — Acil Bildirim Sistemi

- [ ] Tehlike anahtar kelime listesini tanımla: `["kayboldum", "yardım", "ağrı", "düştüm", "korktum", "neredeyim", "nefes alamıyorum"]`
- [ ] `checkDangerSignal(text)` fonksiyonunu yaz — gelen metinde anahtar kelime var mı kontrol et
- [ ] Her AI yanıtından sonra `checkDangerSignal()` çağır
- [ ] Acil uyarı modal HTML'ini oluştur:
  - [ ] Kırmızı arka planlı tam ekran kart
  - [ ] "⚠️ Acil Durum Tespit Edildi" başlığı
  - [ ] Her kayıtlı yakın için ayrı "WhatsApp'ta Mesaj Gönder" butonu
  - [ ] "Kapat / Durum İyi" butonu
- [ ] `showEmergencyAlert()` fonksiyonunu yaz:
  - [ ] localStorage'dan yakın listesini çek
  - [ ] Her yakın için `wa.me/90XXXXXXXXXX?text=...` linki oluştur
  - [ ] Mesaj içeriğini otomatik hazırla: "Sayın [İsim], [Hasta Adı] şu an yardıma ihtiyaç duyuyor olabilir. Lütfen arayın."
  - [ ] Modalı ekrana getir
- [ ] Modal kapatma butonunu işlevsel yap

---

## 📊 AŞAMA 5 — İlerleme Takibi (Unutulanlar Ekranı)

- [ ] Unutulanlar ekranı HTML'ini oluştur:
  - [ ] "Bilişsel İlerleme Takibi" başlığı
  - [ ] Chart.js için `<canvas id="riskGrafik">` alanı
  - [ ] Risk seviyesi rozeti alanı
  - [ ] Hafıza egzersiz önerileri listesi (statik, 3 madde)
- [ ] `calculateRiskScore(conversation)` fonksiyonunu yaz:
  - [ ] Konuşmada yakın ismi hatırlanmadıysa +puan
  - [ ] Tarih/gün sorusuna yanlış yanıt varsa +puan
  - [ ] Kısa ve tutarsız cümleler varsa +puan
  - [ ] 0–100 arası skor döndür
- [ ] Her sohbet oturumu sonunda risk skorunu hesapla ve `localStorage`'a tarihle birlikte kaydet
- [ ] `drawRiskChart()` fonksiyonunu yaz:
  - [ ] Son 7 günün skorlarını localStorage'dan oku
  - [ ] Chart.js çizgi grafiği olarak çiz (x: tarih, y: risk skoru 0-100)
  - [ ] Renk kodlaması: 0-33 yeşil, 34-66 sarı, 67-100 kırmızı
- [ ] Risk rozeti mantığını yaz: skorun ortalamasına göre "Düşük / Orta / Yüksek" göster
- [ ] Unutulanlar ekranı açıldığında `drawRiskChart()` otomatik çağır

---

## 🍔 AŞAMA 6 — Hamburger Menü Navigasyonu

- [ ] Hamburger menü HTML'ini oluştur (üstte sabit konum)
- [ ] Menü açma/kapama animasyonunu CSS ile yaz (slide-in)
- [ ] Menü öğelerine tıklanınca ilgili ekrana geç:
  - [ ] 💬 Ana Menü → sohbet ekranı
  - [ ] 👤 Hesabım → profil formu (mevcut verilerle dolu gelsin)
  - [ ] 📊 Unutulanlar → ilerleme takibi ekranı
- [ ] Menü dışına tıklanınca menüyü kapat

---

## 🧪 AŞAMA 7 — Test ve Düzeltme

- [ ] **Profil testi:** Formu doldur, sayfayı kapat, yeniden aç — veriler geldi mi?
- [ ] **Yasaklı kelime testi:** 10 farklı sohbet senaryosunda AI yasaklı kelime kullandı mı kontrol et
- [ ] **Tehlike sinyali testi:** "Düştüm" yaz — modal 1 saniye içinde açıldı mı?
- [ ] **WhatsApp linki testi:** Oluşturulan wa.me linkini telefonda aç — numara ve mesaj doğru mu?
- [ ] **Grafik testi:** Risk skoru localStorage'a kaydedildi mi? Grafik doğru çiziliyor mu?
- [ ] **Mobil test:** Chrome DevTools'da 375px genişliğinde tüm ekranlar düzgün görünüyor mu?
- [ ] **API hata testi:** Yanlış API anahtarıyla dene — hata mesajı görünüyor mu?
- [ ] **"Emin misiniz?" testi:** Profil sıfırlama butonuna bas — onay dialogu çıkıyor mu?

---

## 🚀 AŞAMA 8 — Yayına Alma

- [ ] Tüm testler geçildikten sonra `features/index.html` dosyasını son kez kontrol et
- [ ] [Netlify Drop](https://app.netlify.com/drop) veya [Vercel](https://vercel.com) ile yayına al
- [ ] Yayın linkini `README.md` içindeki "Yayın Linki" bölümüne ekle
- [ ] Projeyi GitHub reposuna push et

---

> 💡 **İpucu:** Görevleri sırayla yap — bir aşama bitmeden diğerine geçme. Her aşama sonunda tarayıcıda test et.
