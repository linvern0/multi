# 💳 QARZ TIZIMI - To'liq Ko'rsatma

## 🎯 Maqsad

Bu tizim do'konlar uchun qarzga mahsulot sotish va qarzlarni boshqarishni osonlashtiradi.

## 📋 Asosiy Imkoniyatlar

### ✅ Tashkilot va Shaxslarni ajratish
- **Tashkilot**: Bir kompaniya, ko'p xodim, bitta login/parol
- **Shaxs**: Bir kishi, alohida login/parol

### ✅ Avvalgi qarzdorlarni eslash
- Tashkilot/ism yozganda, avvalgilar ro'yxati ko'rsatiladi
- Tez tanlash va davom etish

### ✅ Avtomatik login/parol yaratish
- Birinchi marta qarzga sotishda
- Tasodifiy parol generator
- Admin qarzdorga beradi

### ✅ Qarz to'lash
- To'liq yoki qisman
- Avtomatik eng eski qarzlardan boshlab taqsimlash
- To'lov tarixi

### ✅ Qarzdorlar uchun shaxsiy sahifa
- Login/parol bilan kirish
- O'z qarzlarini ko'rish
- Xaridlar tarixi
- To'lov holati (progress bar)

## 🔄 Qanday ishlaydi? (Qadamma-qadam)

### STSENARIY 1: ABS tashkiloti (Aziz, Rustam ishlaydi)

#### 1-qadama: Birinchi marta Aziz qarzga oladi
```
1. Admin: Tovarlarni savatga qo'shadi
2. Admin: "Qarzga sotish" tugmasini bosadi
3. Admin: Turi = "Tashkilot"
4. Admin: Tashkilot nomi = "ABS"
5. Admin: Xaridor ismi = "Aziz"
6. Tizim: "Login/parol yaratish" modali ochiladi
7. Admin: Login yaratadi: "abs_company"
8. Admin: Parol yaratadi: "abc12345" (yoki tasodifiy)
9. Tizim: Qarzni saqlaydi
10. Admin: Login/parolni ABS tashkilotiga beradi
```

#### 2-qadama: Rustam ham qarzga oladi (bir necha kundan keyin)
```
1. Admin: Tovarlarni savatga qo'shadi
2. Admin: "Qarzga sotish" tugmasini bosadi
3. Admin: Turi = "Tashkilot"
4. Admin: Tashkilot nomi = "ABS" ← AVVALGI RO'YXATDAN TANLAYDI!
5. Admin: Xaridor ismi = "Rustam"
6. Tizim: "ABS" tashkiloti mavjud, yangi login/parol kerak emas
7. Tizim: Qarzni saqlaydi, ABS tashkilotiga qo'shadi
```

#### 3-qadama: ABS o'z qarzlarini ko'radi
```
1. Qarzdor (ABS): debt.html sahifasini ochadi
2. Qarzdor: Login = "abs_company"
3. Qarzdor: Parol = "abc12345"
4. Qarzdor: Kiradi va BARCHA qarzlarni ko'radi:
   - Aziz olgan tovarlar
   - Rustam olgan tovarlar
   - Jami qarz: 500,000 so'm
```

#### 4-qadama: ABS qarzni to'laydi
```
1. Admin: Market.html → "Qarzlar" bo'limiga kiradi
2. Admin: "ABS tashkiloti" ni topadi
3. Admin: "To'lash" tugmasini bosadi
4. Admin: Summa = 200,000 so'm kiritadi
5. Tizim: Eng eski qarzdan boshlab taqsimlaydi
6. Qarzdor (ABS): debt.html da to'lov avtomatik ko'rinadi!
```

---

### STSENARIY 2: Bek (alohida shaxs)

#### 1-qadama: Birinchi marta qarzga oladi
```
1. Admin: Tovarlarni savatga qo'shadi
2. Admin: "Qarzga sotish" tugmasini bosadi
3. Admin: Turi = "Shaxs"
4. Admin: Tashkilot nomi = (bo'sh qoldiriladi)
5. Admin: Xaridor ismi = "Bek"
6. Tizim: "Login/parol yaratish" modali ochiladi
7. Admin: Login = "bek_user"
8. Admin: Parol = "bek789"
9. Tizim: Qarzni saqlaydi
10. Admin: Login/parolni Bekga beradi
```

#### 2-qadama: Bek o'z qarzini ko'radi
```
1. Bek: debt.html sahifasini ochadi
2. Bek: Login = "bek_user"
3. Bek: Parol = "bek789"
4. Bek: Kiradi va faqat O'Z qarzlarini ko'radi
```

---

## 🎨 Interfeys elementlari

### Market.html da qarz bo'limi
```
1. Savat modali → "Qarzga sotish" tugmasi (ko'k rang)
2. Qarz modali:
   - Turi: [Tashkilot / Shaxs]
   - Tashkilot nomi: [Input + avvalgilar ro'yxati]
   - Xaridor ismi: [Input + avvalgi ismlar]
   - Telefon: [Ixtiyoriy]
   - Izoh: [Ixtiyoriy]
   - Qarz summasi: [Avtomatik hisoblanadi]
3. Login/parol modali (faqat yangi qarzdor uchun):
   - Login: [Input + taklif]
   - Parol: [Input + tasodifiy generator]
```

### report.html da qarzlar hisoboti
```
1. "Qarzlar" tab
2. Statistika:
   - Qarzdorlar soni
   - Ochiq qarzlar summasi
   - To'langan qarzlar
   - Qarzga sotilgan savdolar
3. Filtrlash:
   - Hammasi / Tashkilotlar / Shaxslar
   - Ochiq / To'langan / Barchasi
   - Qidirish (ism, tashkilot)
4. Har qarzdor uchun:
   - Nomi, login, telefon
   - Jami qarz
   - To'langan summa
   - Qarzlar ro'yxati (jadval)
```

### debt.html - Qarzdorlar sahifasi
```
1. Login sahifasi:
   - Login input
   - Parol input
   - "Kirish" tugmasi
2. Dashboard:
   - Jami qarz (qizil)
   - To'langan (yashil)
   - Qarz qoldi (ko'k)
   - Xaridlar soni
3. Xaridlar ro'yxati:
   - Sana, tovarlar, summa
   - To'lov holati (progress bar)
   - Har bir qarz alohida kartochka
```

## 🔧 Firebase Sozlash

### 1. Firebase Console'da
```
1. firebase.google.com ga kiring
2. "Add project" bosing
3. Realtime Database yarating
4. Rules'ni Test mode'ga qo'ying (development uchun):

{
  "rules": {
    ".read": true,
    ".write": true
  }
}

⚠️ Production'da xavfsizlik qoidalarini to'g'ri sozlang!
```

### 2. HTML fayllarida
Har 3 ta faylda (`Market.html`, `report.html`, `debt.html`) quyidagi qatorni toping:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",           // ← O'zgartiring
  authDomain: "YOUR_PROJECT...",     // ← O'zgartiring
  databaseURL: "YOUR_DATABASE_URL",  // ← O'zgartiring
  projectId: "YOUR_PROJECT_ID",      // ← O'zgartiring
  storageBucket: "YOUR_BUCKET",      // ← O'zgartiring
  messagingSenderId: "YOUR_ID",      // ← O'zgartiring
  appId: "YOUR_APP_ID"               // ← O'zgartiring
};
```

Firebase Console'dan oling va joylashtiring.

## 📊 Ma'lumotlar bazasi ko'rinishi

### Qarzdorlar (debtors)
```json
{
  "debtors": {
    "xyz123": {
      "type": "organization",
      "organizationName": "ABS",
      "personName": "Aziz",
      "login": "abs_company",
      "password": "abc12345",
      "phone": "+998901234567",
      "createdAt": 1719907200000,
      "createdBy": "Admin"
    },
    "abc456": {
      "type": "individual",
      "organizationName": "",
      "personName": "Bek",
      "login": "bek_user",
      "password": "bek789",
      "phone": "",
      "createdAt": 1719907200000,
      "createdBy": "Admin"
    }
  }
}
```

### Qarzlar (debts)
```json
{
  "debts": {
    "debt001": {
      "debtorId": "xyz123",
      "saleId": "sale001",
      "amount": 150000,
      "paidAmount": 50000,
      "remainingAmount": 100000,
      "status": "active",
      "items": [
        {
          "productId": "prod1",
          "name": "Coca-Cola",
          "volume": "1.5",
          "price": 10000,
          "quantity": 15
        }
      ],
      "note": "Tez to'lash kerak",
      "seller": "Admin",
      "createdAt": 1719907200000,
      "lastPayment": {
        "amount": 50000,
        "date": 1719993600000,
        "note": "Qisman to'lov",
        "receivedBy": "Admin"
      }
    }
  }
}
```

## ✅ Test qilish bosqichlari

### 1. Firebase sozlash
- [ ] Firebase loyihasi yaratildi
- [ ] Realtime Database yoqildi
- [ ] Konfiguratsiya 3 ta faylga qo'shildi

### 2. Asosiy funksiyalar
- [ ] Market.html ga kirildi (Admin PIN: 1234)
- [ ] Tovar qo'shildi
- [ ] Tovarni savatga qo'shildi
- [ ] Naqd sotish ishlaydi

### 3. Qarz tizimi
- [ ] Qarzga sotish modali ochiladi
- [ ] Tashkilot uchun qarz yaratildi
- [ ] Login/parol yaratildi
- [ ] Qarz Firebase'ga saqlandi
- [ ] Takroriy qarz (avvalgi qarzdorga) ishlaydi
- [ ] Shaxs uchun qarz yaratildi

### 4. Qarzdorlar sahifasi
- [ ] debt.html ochiladi
- [ ] Login/parol bilan kirish ishlaydi
- [ ] Qarzlar ko'rsatiladi
- [ ] Statistika to'g'ri

### 5. Qarz to'lash
- [ ] Market.html → Qarzlar bo'limi
- [ ] To'lash modali ochiladi
- [ ] Qisman to'lov ishlaydi
- [ ] To'liq to'lov ishlaydi
- [ ] debt.html da avtomatik yangilanadi

### 6. Hisobotlar
- [ ] report.html ochiladi
- [ ] Qarzlar hisoboti ko'rsatiladi
- [ ] Filtrlash ishlaydi
- [ ] CSV export ishlaydi

## 🐛 Tez-tez uchraydigan muammolar

### ❌ "Firebase bilan ulanmoqda..." to'xtamaydi
**Sabab**: Firebase konfiguratsiyasi noto'g'ri
**Yechim**: 
1. Console'da xato bormi tekshiring (F12)
2. Firebase konfiguratsiyasini qayta tekshiring
3. Database URL to'g'rimi?

### ❌ "Login yoki parol noto'g'ri"
**Sabab**: Qarzdor yaratilmagan yoki xato
**Yechim**:
1. Firebase Console → Realtime Database → debtors
2. Login va parol mavjudmi tekshiring
3. Katta-kichik harflar farqi bor!

### ❌ Qarzlar ko'rinmaydi
**Sabab**: Firebase listeners ishlamayapti
**Yechim**:
1. Internet ulangan bo'lsin
2. Firebase Rules "read: true" ga sozlangan bo'lsin
3. Console'da xato bormi tekshiring

## 💡 Maslahatlar

1. **PIN kodlarni o'zgartiring**: Market.html → Sozlamalar
2. **Backup oling**: Firebase Console → Export JSON
3. **Test rejimda sinab ko'ring**: Haqiqiy ma'lumotlar kiritishdan oldin
4. **Qarzdorlarga login/parolni yozing**: Unutmaslik uchun
5. **Qarzlarni muntazam tekshiring**: Har hafta yoki har oy

## 📞 Yordam kerakmi?

Savollaringiz bo'lsa yoki yordam kerak bo'lsa:
- GitHub Issues'da savol bering
- README.md ni o'qing
- Firebase dokumentatsiyasiga qarang

---

**Omad tilaymiz! 🚀**
