# ⚙️ tech-stack.md — Teknoloji Yığını (v2)

## Ana Teknolojiler

| Teknoloji | Kullanım | Seçim Gerekçesi |
|-----------|---------|-----------------|
| **HTML5 / CSS3 / Vanilla JS** | Arayüz | Kurulum gerektirmez, her tarayıcıda çalışır |
| **Google Gemini API** | AI sohbet motoru | Ücretsiz kota, Türkçe desteği mükemmel, Google AI Studio'dan kolayca alınır |
| **Web Speech API** | Sesli giriş (mikrofon) | Tarayıcıya gömülü, ek kurulum yok |
| **SpeechSynthesis API** | Sesli çıkış (AI seslendirme) | Tarayıcıya gömülü |
| **localStorage** | Profil ve sohbet geçmişi | Sunucu gerektirmez, veriler cihazda kalır |

---

## Gemini API — Google AI Studio

### Neden Gemini?
- **Ücretsiz başlangıç kotası** var (Claude veya GPT-4'e göre daha erişilebilir)
- Google AI Studio arayüzü çok sade — API anahtarı almak 2 dakika sürer
- Türkçe dil desteği çok güçlü
- `gemini-1.5-flash` modeli hızlı ve hafif

### API Anahtarı Alma (Adım Adım)
1. [aistudio.google.com](https://aistudio.google.com) → Google hesabıyla giriş
2. Sol menü → "API Keys" → "Create API Key"
3. Kopyala → Uygulamada Ayarlar → API Anahtarı alanına yapıştır
4. Bitti! Sunucu, kart, kayıt gerekmez.

---

## n8n — Opsiyonel Otomasyon (SMS Bildirimi İçin)

### n8n Nedir?
n8n, "kod yazmadan otomasyon" aracıdır. İki şey arasında köprü kurar:
> "Yâdigâr'dan bir sinyal geldiğinde → Yakına WhatsApp/SMS gönder"

### Neden n8n?
- Görsel sürükle-bırak arayüzü (kod yazmak gerekmez)
- Twilio (SMS), WhatsApp Business, Gmail ile kolayca entegre
- Ücretsiz self-hosted versiyonu var

### n8n Akışı (Konsept)
```
[Yâdigâr'dan Webhook tetiklenir]
        ↓
[n8n: "Acil bildirim" mı?]
        ↓
[Twilio / WhatsApp ile SMS gönder]
        ↓
[Yakının telefonuna mesaj ulaşır]
```

> **Not:** İlk versiyon için n8n olmadan da çalışır. SMS yerine tarayıcı bildirimi kullanılabilir.

---

## Mimari Karar: Neden Tek Dosya?

Hedef kullanıcı (hasta yakını, öğrenci, yarışma jürisi) teknik değil.
- Tek `index.html` → tarayıcıda aç, çalışır
- Sunucu, Node.js, Python ortamı gerektirmez
- Veriler cihazda kalır → gizlilik

---

## Gelecek Sürüm Teknolojileri

| Teknoloji | Amaç |
|-----------|------|
| **Supabase** | Bulut veritabanı (çoklu cihaz desteği) |
| **Twilio / MessageBird** | Gerçek SMS gönderimi |
| **ElevenLabs** | Daha doğal Türkçe ses |
| **PWA** | Telefon ana ekranına yükleme |
| **n8n** | SMS otomasyon akışları |
