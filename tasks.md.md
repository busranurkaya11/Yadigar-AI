# 🧭 CURSOR REHBERİ — Yazılım Bilmeden Yâdigâr AI'ı Geliştirme

## Bu Rehber Kimin İçin?
Kod yazmayı bilmiyorsunuz ama projeyi geliştirmek istiyorsunuz. Cursor bunu mümkün kılar.
Cursor'a Türkçe yazarak ne istediğinizi söylersiniz, o kodu yazar.

---

## ADIM 1 — Cursor'u İndirin ve Kurun

1. Tarayıcınızda **cursor.com** adresini açın
2. **"Download"** butonuna tıklayın
3. İndirilen dosyayı çalıştırın, kurulumu tamamlayın
4. Cursor'u açın

---

## ADIM 2 — Projeyi Cursor'a Açın

1. Cursor açıkken sol üstten **"File"** → **"Open Folder"**
2. `yadiga-v2` klasörünü seçin
3. Sol tarafta dosyalar listelenecek: `features/index.html`, `README.md` vb.

---

## ADIM 3 — Gemini API Anahtarı Alın (Ücretsiz, 5 Dakika)

1. Tarayıcıda **aistudio.google.com** adresini açın
2. Google hesabınızla giriş yapın
3. Sol menüden **"Get API Key"** seçin
4. **"Create API Key"** butonuna tıklayın
5. Çıkan anahtarı (AIzaSy... ile başlar) kopyalayın
6. Uygulamayı açtığınızda **"API Anahtarı"** menüsüne yapıştırın

---

## ADIM 4 — Cursor Chat ile Değişiklik Yapın (Ana Bölüm)

### Cursor Chat Nasıl Açılır?
Klavyede **Ctrl + L** (Mac'te **Cmd + L**) tuşlarına basın.
Sağ tarafta bir sohbet kutusu açılır. Buraya Türkçe yazabilirsiniz.

---

## 💬 CURSOR'A YAZACAĞINIZ KOMUTLAR

Aşağıdaki komutları Cursor Chat'e kopyalayıp yapıştırabilirsiniz. Cursor her birini uygular.

---

### 🎨 Tasarım Değişiklikleri

**Renk temasını değiştirmek için:**
```
features/index.html dosyasında renk temasını değiştir. 
Şu an bej/krem ton var. Bunu daha modern, 
açık mavi ve beyaz tonlarına çevir.
```

**Logo ve başlık değiştirmek için:**
```
features/index.html dosyasında uygulamanın adını 
"Yâdigâr" yerine "Yâdigâr AI" olarak güncelle.
Ana rengi bej yerine koyu lacivert yap.
```

---

### 🩺 Forma Yeni Alan Eklemek

**İlaç alanı eklemek için:**
```
features/index.html dosyasında hasta bilgileri formuna 
(ob1 bölümü) yeni bir alan ekle: "Kullandığı İlaçlar".
Diğer alanlarla aynı stilde, opsiyonel olsun.
Bu bilgi profile.medications olarak kaydedilsin.
```

**Doktor adı eklemek için:**
```
features/index.html dosyasında hasta bilgileri formuna 
"Takip Eden Doktor" ve "Doktor Telefonu" alanları ekle.
Hasta bilgileri görüntüleme ekranında da göster.
```

---

### 💬 AI'ın Konuşma Stilini Değiştirmek

```
features/index.html dosyasında buildSystemTurn() 
fonksiyonunu bul. System prompt'a şu kuralları ekle:
- Kullanıcı üzgün görünürse "Sizi anlıyorum, bu zor olabilir" 
  gibi empati cümleleri kur
- Her 5 mesajda bir hafıza egzersizi sor: 
  "Bana çocukluk anınızdan birini anlatır mısınız?"
- Kullanıcı "yardım" derse yakın listesinden ilkini belirterek 
  "Sizi arayayım mı?" de
```

---

### 📊 İlerleme Takibini Geliştirmek

```
features/index.html dosyasında progress sub-screen'e yeni bir bölüm ekle:
"Haftalık Özet" başlığı altında:
- Bu hafta kaç sohbet yapıldı (sayı)
- En çok konuşulan konu (manuel not olarak girilebilsin)
- Genel ruh hali (İyi / Orta / Kötü radio butonu)
Bu bilgiler localStorage'a kaydedilsin.
```

---

### 🆘 Acil Bildirim Özelliğini Geliştirmek

```
features/index.html dosyasında sohbet sırasında kullanıcı 
"yardım", "acil" veya "çok kötüyüm" yazarsa şunu yap:
1. Sarı arka planlı bir uyarı mesajı göster: 
   "Sizi duyuyorum. Bir yakınınızı haber vereyim mi?"
2. Evet butonuna basarsa kayıtlı ilk yakının adını ve telefonunu 
   büyük yazıyla ekranda göster.
3. "Hemen Ara" butonu çıksın.
```

---

### 🎤 Sesli Yanıt Eklemek (AI konuşsun)

```
features/index.html dosyasında addAiBubble() fonksiyonuna 
Web Speech Synthesis ekle. AI mesaj yazdıktan sonra aynı mesajı 
Türkçe sesle okusun. Sesi kapatmak için bir ses ikonu (🔊/🔇) 
ekle topbar'a.
```

---

### 📱 Mobil Görünümü İyileştirmek

```
features/index.html dosyasında mobil görünümü iyileştir:
- Alt kısımda sabit bir navigasyon çubuğu ekle 
  (💬 Sohbet, 👤 Profil, 📊 İlerleme ikonları)
- Font boyutlarını mobilde biraz büyüt (en az 18px)
- Butonları daha büyük yap (min 52px yükseklik)
```

---

## ADIM 5 — Değişiklikleri Kaydetmek

Cursor değişikliği yapınca otomatik kaydeder. Ama **Ctrl+S** ile de kaydedebilirsiniz.

Sonra tarayıcıda `features/index.html` dosyasını açık tutun ve **F5** ile yenileyin.

---

## ADIM 6 — Siteyi Yayına Almak (Ücretsiz)

### Netlify ile (En Kolay Yol):
1. **netlify.com** adresine gidin, ücretsiz hesap açın
2. **"Add new site"** → **"Deploy manually"**
3. `yadiga-v2` klasörünü sürükle-bırak edin
4. 30 saniyede canlı link alırsınız

### GitHub + Vercel:
1. **github.com** → "New repository" → `yadiga-ai`
2. `yadiga-v2` klasörünü yükleyin
3. **vercel.com** → "New Project" → GitHub repo'yu seçin
4. Deploy edin

---

## n8n ile SMS Otomasyonu (İleri Seviye)

n8n kodlamasız otomasyon aracıdır.

### Kurulum:
1. **n8n.io** → "Get started for free" (bulut versiyonu)
2. Yeni bir "Workflow" oluşturun
3. Şu düğümleri ekleyin:
   - **Webhook** (Yâdigâr'dan tetikleme alır)
   - **IF** (acil mesaj mı kontrol et)
   - **Twilio** (SMS gönder) veya **WhatsApp Business**

### Cursor'a Yazın:
```
features/index.html dosyasında acil durum tespit edildiğinde 
https://SENIN_N8N_ADRESIN/webhook/yadiga-emergency adresine 
POST isteği gönder. Body olarak şunu gönder:
{
  "patientName": profile.name,
  "relativePhone": relatives[0].phone,
  "message": "Acil durum algılandı"
}
```
(n8n webhook adresinizi oluşturduktan sonra buraya yapıştırın)

---

## ❓ Sık Karşılaşılan Sorunlar

| Sorun | Çözüm |
|-------|-------|
| AI yanıt vermiyor | API anahtarını kontrol et (Ayarlar menüsü) |
| Ses çalışmıyor | Chrome veya Edge kullan, mikrofon iznini ver |
| Değişiklikler görünmüyor | Tarayıcıda F5'e bas veya Ctrl+Shift+R |
| Cursor kodu anlamıyor | Daha açık yaz: "index.html dosyasında..." diye başla |

---

## 💡 Cursor'a Yazarken İpuçları

- ✅ **Dosya adını belirt:** "features/index.html dosyasında..."
- ✅ **Fonksiyon adını belirt:** "sendMsg() fonksiyonunu bul ve..."
- ✅ **Örnek ver:** "Şu an '...' yazıyor, bunu '...' ile değiştir"
- ✅ **Adım adım sor:** Tek seferde çok şey isteme
- ✅ **Türkçe yaz:** Cursor Türkçe komutları mükemmel anlar
