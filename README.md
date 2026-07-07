# 🏪 Do'kon Tizimi - Qarz boshqaruvi bilan

Firebase Real-time Database ga ulangan to'liq funksional do'kon boshqaruv tizimi va qarz tizimi.

## 📋 Xususiyatlar

### Market.html - Asosiy Do'kon Tizimi
- ✅ **Admin Panel**: Tovarlar, savdo, kirim/chiqim boshqaruvi
- ✅ **Sotuvchi Panel**: Mahsulot sotish, shaxsiy savdolar tarixi
- ✅ **Tovar boshqaruvi**: CRUD operatsiyalari, zaxira nazorati
- ✅ **Savdo tizimi**: Naqd va qarzga sotish
- ✅ **Kirim/Chiqim**: Tovar harakati tarixi
- ✅ **Dashboard**: Statistika va hisobotlar

### 🔍 Maxsus Skaner Xususiyatlari (YANGI!)
- ✅ **Har tovar uchun alohida kodlar**: Shtrix-kod va QR kod
- ✅ **Donalarni ro'yxatga olish**: Qabul qilingan tovarlarni individual skanerlash
- ✅ **Maxsus QR skaner**: Qora idishlardagi oq QR kodlar uchun
- ✅ **Lazer chizilgan kodlar**: Energetiklar va metall idishlar uchun
- ✅ **Avtomatik rejim**: Tezkor ketma-ket skanerlash
- ✅ **Image processing**: Yorug'lik, kontrast, gamma sozlamalari
- ✅ **Multi-strategy scanning**: Bir nechta algoritm bilan aniqlash

### 💳 Qarz Tizimi
- ✅ **Qarzga sotish**: Tashkilot yoki shaxsga qarzga tovar berish
- ✅ **Login/Parol yaratish**: Birinchi qarzga sotishda avtomatik
- ✅ **Qarzdorlar boshqaruvi**: Tashkilotlar va shaxslar alohida
- ✅ **Qarz to'lash**: Qisman yoki to'liq to'lov qabul qilish
- ✅ **Avvalgi qarzdorlar**: Takroriy xaridlarda tanlash imkoni

### report.html - Hisobotlar Tizimi
- 📊 **Savdo hisobotlari**: Tovarlar bo'yicha tahlil
- 📦 **Zaxira hisobotlari**: Real-time ombor holati
- 💳 **Qarzlar hisoboti**: Qarzdorlar statistikasi va tahlili
- ⬇️ **CSV Export**: Barcha hisobotlarni yuklab olish
- 🔍 **Filtrlash va qidirish**: Kuchli qidiruv tizimi

### debt.html - Qarzdorlar Shaxsiy Kabineti
- 🔐 **Login/Parol bilan kirish**: Xavfsiz autentifikatsiya
- 📊 **Qarz statistikasi**: Jami, to'langan, qolgan summa
- 📜 **Xaridlar tarixi**: Batafsil qarzlar ro'yxati
- 📈 **Progress bar**: Vizual to'lov holati
- 🔄 **Real-time**: Avtomatik yangilanish

## 🚀 Ishga tushirish

### 1. Firebase sozlash

1. [Firebase Console](https://console.firebase.google.com/) da yangi loyiha yarating
2. Realtime Database'ni yoqing (Test mode)
3. Firebase konfiguratsiyasini oling

### 2. Konfiguratsiya

Market.html faylida Firebase konfiguratsiyasini o'zgartiring:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  databaseURL: "YOUR_DATABASE_URL",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_BUCKET",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

**Muhim**: Agar konfiguratsiya to'ldirilmasa, tizim demo rejimda ishlaydi (ma'lumotlar saqlanmaydi).

### 3. Fayllarni ochish

- `Market.html` - Asosiy tizim (admin va sotuvchi uchun)
- `sw.js` - Service Worker (offline support)
- `report.html` - Hisobotlar (agar mavjud bo'lsa)
- `debt.html` - Qarzdorlar kabineti (agar mavjud bo'lsa)

## 🔐 Kirish ma'lumotlari

### Market.html (Default)
- **Admin**: PIN `1234`
- **Sotuvchi**: PIN `5678`

*Sozlamalar bo'limida PIN kodlarni o'zgartirish mumkin.*

## 🔍 Skaner Funksiyalari

### 1. Oddiy QR/Barcode Skaner
- Standart QR kodlar va barkodlar uchun
- Avtomatik rejim mavjud
- Real-time aniqlash

### 2. Maxsus QR Skaner (Oq kodlar uchun)
- Qora plastik/metall idishlardagi oq QR kodlar
- Lazer bilan chizilgan kodlar uchun optimizatsiya
- Yorug'lik, kontrast, gamma sozlamalari
- Auto-optimization rejimi

### 3. Donalarni ro'yxatga olish
- Omborga qabul qilingan lekin skanerlanmagan tovarlar uchun
- Har bir dona uchun alohida QR kod
- Progress tracking va eksport funksiyasi
- Batch processing qo'llab-quvvatlaydi

## 💡 Skaner maslahatlar

### Umumiy
- Kamerani tozalang va barqaror ushlab turing
- Yaxshi yorug'lik ta'minlang
- 10-20 sm masofada skaner qiling
- Kodni tekis va to'g'ri yo'nalishda ushlab turing

### Maxsus skaner uchun
- "Lazer" presetini tanlang
- Idishni biroz burib ko'ring
- Kontrast va yorug'likni sozlang
- Agar ishlamasa, oddiy skanerga o'ting

## 🔧 Texnik xususiyatlar

### Texnologiyalar
- **Frontend**: Vanilla JavaScript, HTML5, CSS3
- **Backend**: Firebase Realtime Database
- **Skaner**: jsQR (QR), Quagga.js (Barcode)
- **PWA**: Service Worker, offline support
- **Authentication**: PIN kod va login/parol tizimi

### Brauzer qo'llab-quvvatlash
- Chrome, Firefox, Safari, Edge (so'nggi versiyalar)
- Mobile browsers (iOS Safari, Chrome Mobile)
- Kamera API qo'llab-quvvatlash talab qilinadi

### Xavfsizlik
- Firebase Security Rules sozlang
- PIN kodlarni murakkablashtiring  
- HTTPS protokoli tavsiya etiladi
- Qarzdorlar login/parolini xavfsiz saqlang

## 📱 Mobil foydalanish

- Responsive design - barcha qurilmalarda ishlaydi
- Touch-friendly interfeys
- Optimizatsiya qilingan kamera ishlash
- Offline qo'llab-quvvatlash

## ⌨️ Klaviatura yorliqlari

- **ESC** - Barcha oynalarni yopish
- **F1** - Yordam
- **F5** - Sahifani yangilash

## 🐛 Muammolar va yechimlar

### Kamera ishlamayotganda
1. Brauzer sozlamalarida kamera ruxsatini tekshiring
2. Boshqa dasturlar kamerani ishlatmayotganini tasdiqlang
3. HTTPS protokoli ishlatilganini tekshiring
4. Sahifani yangilang (F5)

### Firebase ulanish muammolari
1. Konfiguratsiya to'g'riligini tekshiring
2. Internet aloqasini tekshiring
3. Firebase loyiha sozlamalarini ko'rib chiqing
4. Demo rejimda sinab ko'ring

### Skaner aniqlamayotganda
1. Kamerani tozalang
2. Yorug'likni yaxshilang
3. Maxsus skanerga o'ting
4. Kod sifatini tekshiring

## 📝 Litsenziya

MIT License - O'z loyihalaringizda erkin foydalaning!

---

**Yaratildi:** 2026-yil, Iyul  
**Versiya:** 2.0.0 (Enhanced Scanner Edition)  
**Til:** O'zbek tili
