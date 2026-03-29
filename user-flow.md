# 🔄 user-flow.md — Kullanıcı Akışı (v2)

## Genel Akış

```
[Site Açılır]
      │
      ▼
İlk kez mi?
   /       \
 EVET      HAYIR
  │           │
  ▼           ▼
[1. HASTA    [3. ANA EKRAN]
 BİLGİLERİ   (Sohbet / AI)
 FORMU]
  │
  ▼
[2. YAKIN
 BİLGİLERİ]
  │
  ▼
[3. ANA EKRAN]
```

---

## Ekran 1 — Hasta Bilgileri Formu (İlk Giriş)

**Yâdigâr şunu söyler:** "Merhaba! Sizi daha iyi tanımak istiyorum."

**Form alanları:**
- Ad Soyad (zorunlu)
- Yaş
- Kan Grubu
- Tanı / Rahatsızlıklar (ör: Alzheimer Evre 1, Diyabet)
- Kullanılmaması gereken kelimeler (virgülle ayır — ör: ölüm, unutma, hastalık)
- Günlük hatırlatma ister misin? (Evet/Hayır)

**[İleri →] butonu**

---

## Ekran 2 — Yakın Bilgileri (İlk Giriş, 2. adım)

**Yâdigâr:** "Sevdiklerinizi de tanıyayım."

**Her yakın için:**
- İsim (ör: Büşra)
- Yakınlık (Kız, Oğul, Eş, vb.)
- Telefon numarası

**[+ Yakın Ekle] butonu** — birden fazla yakın eklenebilir
**[Başla →] butonu**

---

## Ekran 3 — Ana Ekran (Sohbet)

**Üst bar:**
- Sol: ☰ Hamburger menü
- Orta: "Yâdigâr" logosu
- Sağ: Kullanıcı adı

**Yâdigâr'ın ilk mesajı:**
> "Merhaba [Ad], bugün nasılsın? Biraz sohbet edelim mi?"

**Sohbet alanı:**
- Mesaj baloncukları (AI solda, kullanıcı sağda)
- Yazı kutusu
- 🎤 Mikrofon butonu (sesli konuşma)
- ➤ Gönder butonu

---

## Hamburger Menü (☰)

### 👤 Hesabım
**Alt bölüm 1 — Hasta Bilgileri:**
- Ad, yaş, kan grubu, rahatsızlıklar görüntüle/düzenle
- Yasak kelimeler listesi

**Alt bölüm 2 — Yakınımın Bilgileri:**
- Yakın listesi (isim, yakınlık, telefon)
- Yakın ekle / düzenle / sil

---

### 🧩 Unutulanlar (İlerleme Takibi)

**Üst kısım — Hastalık İlerleme Riski:**
- Görsel risk göstergesi (düşük / orta / yüksek)
- Haftalık sohbet skoru grafiği
- "Son 7 günde 4 sohbet yapıldı" gibi özet

**Alt kısım — Kaydedilen Unutmalar:**
- "Kızının adını sorunca hatırlamadı — 12 Mart"
- "Öğle yemeğini yiyip yemediğini hatırlamıyordu — 10 Mart"
- Yâdigâr bu notları sohbet sırasında otomatik kaydeder
- Elle not da eklenebilir

---

### 🏠 Ana Menü
Sohbet ekranına geri döner.

---

## Acil Mesaj Akışı

```
Sohbet sırasında → Yâdigâr "acil" kelimesi veya
                   kafa karışıklığı/panik tonu algılar
                        │
                        ▼
              "Biraz rahatsız mısınız?" diye sorar
                        │
               Kullanıcı "evet" / olumlu yanıt
                        │
                        ▼
           Kayıtlı yakınlara SMS/bildirim gönderilir:
           "[Ad Soyad] yardıma ihtiyaç duyabilir.
            Yâdigâr uygulaması otomatik bildirim."
```
