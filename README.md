# الباحث الذكي — تطبيق Android شخصي

تطبيق Android حقيقي (Capacitor): واجهة عربية RTL، اتصال مباشر بـ Anthropic API من الهاتف،
مفتاح API في Android Keystore، والمشاريع محفوظة على الهاتف وتعمل بدون إنترنت.
لا Netlify ولا خادم ولا تسجيل دخول. الإنترنت مطلوب فقط عند توليد الخطط.

## الطريقة أ: بناء APK بدون تثبيت أي برنامج (GitHub Actions)
1. أنشئ مستودعًا خاصًا (Private) في github.com.
2. ارفع محتويات هذا المجلد كاملةً مع بنيتها، ومنها المجلد المخفي `.github/workflows/android.yml`.
3. افتح تبويب **Actions** ← **Build APK** ← **Run workflow** وانتظر 5–10 دقائق حتى يظهر ✔.
4. افتح التشغيل الناجح ← قسم **Artifacts** ← حمّل `alba7ith-apk`، وفك الضغط لتحصل على `app-debug.apk`.

## الطريقة ب: البناء على الحاسوب (Android Studio)
1. ثبّت Node.js (LTS) و Android Studio.
2. في مجلد المشروع: `npm install` ثم `node scripts/prepare.js` ثم `npx cap add android` ثم `npx cap sync android`
3. `npx cap open android` ثم في Android Studio: **Build ← Build Bundle(s)/APK(s) ← Build APK(s)**.
4. الملف في: `android/app/build/outputs/apk/debug/app-debug.apk`
بعد أي تعديل في `www/index.html`: `npm run sync` ثم أعد البناء.

## التثبيت على الهاتف
انقل الملف إلى الهاتف، وافتحه، واسمح بـ «التثبيت من مصادر غير معروفة» عند الطلب، ثم ثبّت.
(هذا APK تجريبي موقّع بمفتاح debug، وهو مناسب للاستخدام الشخصي.)

## ربط مزوّدي الذكاء الاصطناعي
افتح التطبيق ← **الإعدادات** ← اختر المزوّد (Claude / OpenAI / Gemini / OpenRouter / DeepSeek / Groq / Mistral / xAI / مزوّد آخر متوافق مع OpenAI)
← الصق مفتاحه ← **حفظ المفتاح** ← **اختبار الاتصال**. لكل مزوّد مفتاحه المحفوظ منفصلًا (Android Keystore)، ويظهر مقنّعًا دائمًا.
غيّر المزوّد في أي وقت من القائمة نفسها. اسم النموذج قابل للتعديل لكل مزوّد.
OpenRouter يتيح الوصول إلى مئات النماذج بمفتاح واحد.
ملاحظة: الربط يتم عبر مفاتيح API (مدفوعة عند كل مزوّد)، ولا يمكن استعمال اشتراكات ChatGPT أو Gemini أو Claude في التطبيقات.

## ملاحظات
- «تصدير PDF» و«تصدير Word» و«مشاركة» تفتح قائمة المشاركة في أندرويد لحفظ الملف أو إرساله.
- الواجهة مبنية بالويب داخل غلاف Android أصلي (Capacitor)، وليست واجهة Kotlin/Flutter أصلية.
