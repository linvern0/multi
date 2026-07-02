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

### 💳 Qarz Tizimi (YANGI!)
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

Har 3 ta HTML faylda (`Market.html`, `report.html`, `debt.html`) Firebase konfiguratsiyasini o'zgartiring:

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

### 3. Fayllarni ochish

- `Market.html` - Asosiy tizim (admin va sotuvchi uchun)
- `report.html` - Hisobotlar (admin uchun)
- `debt.html` - Qarzdorlar uchun shaxsiy kabinet

## 🔐 Kirish ma'lumotlari

### Market.html (Default)
- **Admin**: PIN `1234`
- **Sotuvchi**: PIN `5678`

### report.html
- **Admin**: PIN `1234`

### debt.html
- **Qarzdorlar**: Admin tomonidan yaratilgan login/parol

## 💡 Qarz tizimi qanday ishlaydi?

### 1. Birinchi marta qarzga sotish
1. Admin yoki sotuvchi tovarlarni savatga qo'shadi
2. "Qarzga sotish" tugmasini bosadi
3. Tashkilot/Shaxs turini tanlaydi
4. Tashkilot nomi (agar kerak bo'lsa) va xaridor ismini kiritadi
5. **Tizim avtomatik login/parol yaratishni taklif qiladi**
6. Admin login/parol yaratadi va qarzdorga beradi
7. Savdo yakunlanadi, qarz yoziladi

### 2. Takroriy qarzga sotish
1. Admin tovarlarni savatga qo'shadi
2. "Qarzga sotish" tugmasini bosadi
3. **Avvalgi tashkilot/ism avtomatik taklif qilinadi**
4. Tanlaydi va davom etadi
5. Yangi qarz mavjud qarzdorga qo'shiladi

### 3. Qarz to'lash
1. Admin `Market.html` da "Qarzlar" bo'limiga kiradi
2. Qarzdorni topadi va "To'lash" tugmasini bosadi
3. Summasini kiritadi (to'liq yoki qisman)
4. To'lov avtomatik eng eski qarzlardan boshlab taqsimlanadi

### 4. Qarzdor o'z qarzini ko'radi
1. Qarzdor `debt.html` ga kiradi
2. Login/parol bilan tizimga kiradi
3. Barcha qarzlarini, xaridlar tarixini ko'radi
4. To'lov holati real-time yangilanadi

## 📊 Firebase Databaza Strukturasi

```
/
├── settings/
│   ├── adminPin: "1234"
│   ├── sellerPin: "5678"
│   └── returnPeriod: 30
├── products/
│   └── {productId}/
│       ├── name, price, stock, volume
│       ├── image, note, createdAt
│       └── createdBy
├── sales/
│   └── {saleId}/
│       ├── items[], total, timestamp
│       ├── paymentType: "cash" | "debt"
│       ├── debtorId (agar qarzga sotilgan bo'lsa)
│       └── seller
├── debts/
│   └── {debtId}/
│       ├── debtorId, saleId
│       ├── amount, paidAmount, remainingAmount
│       ├── items[], status, note
│       ├── createdAt, seller
│       └── lastPayment
├── debtors/
│   └── {debtorId}/
│       ├── type: "organization" | "individual"
│       ├── organizationName, personName
│       ├── login, password, phone
│       └── createdAt, createdBy
└── inventory/
    └── {inventoryId}/
        ├── productId, type, amount
        ├── reason, resultStock
        └── timestamp, user
```

## 🎯 Asosiy Mantiq

### Tashkilot vs Shaxs
- **Tashkilot**: Bir login/parol, ko'p xodim (masalan: ABS tashkiloti → Aziz, Rustam, Nodir)
- **Shaxs**: Bir kishi uchun alohida login/parol (masalan: Bek)

### Login/Parol
- Faqat **birinchi marta** qarzga sotishda yaratiladi
- Takroriy xaridlarda mavjud login ishlatiladi
- Qarzdor o'z login/paroli bilan `debt.html` ga kiradi

## 🛠 Texnologiyalar

- **Frontend**: Vanilla JavaScript, HTML5, CSS3
- **Backend**: Firebase Realtime Database
- **Authentication**: PIN kod (admin/sotuvchi), Login/Parol (qarzdorlar)
- **Real-time**: Firebase onValue listeners
- **Responsive**: Mobile-friendly design

## 📱 Browser Support

- Chrome, Firefox, Safari, Edge (so'nggi versiyalar)
- Mobile browsers (iOS Safari, Chrome Mobile)

## ⚠️ Muhim eslatmalar

1. **Firebase konfiguratsiyasini o'zgartirish SHART!**
2. PIN kodlarni o'zgartiring (Sozlamalar bo'limida)
3. Production'da Firebase Security Rules sozlang
4. Qarzdorlar login/parolini xavfsiz saqlang
5. Muntazam backup oling

## 🔒 Xavfsizlik

- Firebase Security Rules'ni sozlang
- PIN kodlarni murakkablashtiring
- HTTPS protokolidan foydalaning
- Login/parollarni shifrlashni o'ylang (production uchun)

## 📝 Litsenziya

MIT License - O'z loyihalaringizda erkin foydalaning!

## 🤝 Yordam

Savollar yoki muammolar bo'lsa, GitHub Issues'da xabar qoldiring.

---

**Yaratildi:** 2026-yil, Iyul
**Versiya:** 1.0.0
**Til:** O'zbek tili
