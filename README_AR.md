# إمبراطورية المال — Money Empire

**الإصدار 1.1.0 — نسخة الويب الجاهزة للنشر على GitHub وNetlify**

## محتويات النسخة
- لعبة عربية باتجاه RTL وتصميم أسود/ذهبي/أخضر وشاشة بداية.
- شركات قابلة للشراء والتطوير ودخل تلقائي وترقيات.
- مدينة تتطور بصريًا حسب الثروة، واستثمارات افتراضية.
- مهام وإنجازات ومكافأة يومية وصندوق وملف شخصي وإعدادات.
- حفظ محلي وتصدير/استيراد نسخة احتياطية.
- صفحة حساب: إنشاء حساب وتسجيل دخول بالبريد وكلمة المرور، تسجيل Google، وإعادة تعيين كلمة المرور.
- مزامنة حفظ المستخدم مع Firebase Realtime Database.
- PWA وملفات Capacitor تمهيدًا لتجهيز تطبيق Android.

## النشر على GitHub وNetlify
1. فك ضغط المشروع وارفع محتويات مجلد `money_empire` إلى مستودع GitHub.
2. من Netlify اختر **Add new site → Import an existing project** ثم اربط مستودع GitHub.
3. إعدادات البناء موجودة في `netlify.toml` تلقائيًا: الأمر `npm run build` ومجلد النشر `dist`.
4. بعد النشر افتح رابط الموقع واختبر اللعبة وتسجيل الدخول.

## إعداد Firebase قبل تجربة الحسابات
1. افتح Firebase Console للمشروع `sycc-e2608`.
2. من **Authentication → Sign-in method** فعّل **Email/Password** و**Google**.
3. من **Authentication → Settings → Authorized domains** أضف نطاق Netlify الخاص بالموقع، وأي نطاق مخصص تستخدمه.
4. راجع `database.rules.json` وانشر قواعد قاعدة البيانات من Firebase Console. لا تترك قواعد قاعدة البيانات مفتوحة للعامة.
5. جرّب إنشاء حساب وتسجيل الخروج والدخول مرة أخرى للتأكد من المزامنة.

## التشغيل محليًا
يتطلب Node.js حديثًا:
```bash
npm install
npm run dev
```

## تجهيز Android
يتطلب Node.js وAndroid Studio وAndroid SDK وJDK مناسبًا لـ Android Studio:
```bash
npm install
npm run build
npx cap add android
npx cap sync android
npx cap open android
```
بعدها من Android Studio اختر **Build → Build APK(s)**. إذا كان مجلد `android` موجودًا مسبقًا، لا تكرر `npx cap add android`؛ استخدم `npm run android:sync`.

## تنبيهات مهمة
- هذه النسخة تستخدم Firebase Auth لتسجيل الدخول، لكن لا تعتبر أرقام الثروة المرسلة من جهاز اللاعب موثوقة. لا تستخدم الحفظ الحالي لتحديد فائزين أو ترتيب عالمي ذي قيمة؛ يمكن التلاعب بالقيم من جهة العميل.
- `database.rules.json` نموذج بداية يحتاج مراجعته ونشره في Firebase Console. قواعد الأمان لا تُطبّق بمجرد وجود الملف في GitHub.
- مفتاح إعداد Firebase للويب موجود في كود العميل بطبيعته؛ الأمان يعتمد على قواعد Firebase، وتقييد المفاتيح عند الحاجة، وإعدادات المصادقة الصحيحة.
- لا ترفع ملفات سرية أو مفاتيح خدمة إدارية إلى GitHub.
