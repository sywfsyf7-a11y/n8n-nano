# دليل تشغيل مشروع "الشركة الذكية" (Mini AI Company) على n8n Cloud

كل ملفات المشروع جاهزة داخل هذا المجلد لتشغيلها خلال **15 دقيقة** فقط قبل الفعالية الجامعية:

- `n8n-workflow.json` — ملف الـ Workflow الكامل (Chat Trigger + AI Agent + Gemini + Memory + Google Sheets + Gmail).
- `Orders.csv` و `IT_Tickets.csv` — قوالب جاهزة لجداول Google Sheets.
- `index.html` — واجهة الموقع التفاعلية بالعربية (فيها وضع Demo جاهز فوراً + زر ربط مباشر مع n8n Cloud).

---

## الخطوة 1: تجهيز جدول Google Sheets (دقيقتين)
1. افتح [Google Sheets](https://sheets.new) لإنشاء ملف جديد وسمّه مثلاً: `Mini AI Company`.
2. أنشئ ورقتين (Tabs) في الأسفل بالأسماء التالية بالضبط:
   - الورقة الأولى: **`Orders`** ← اعمل Import لملف `Orders.csv` (الأعمدة: `Date, Customer_Name, Service, Amount_JOD, Status, Notes`).
   - الورقة الثانية: **`IT_Tickets`** ← اعمل Import لملف `IT_Tickets.csv` (الأعمدة: `Date, Customer_Name, Issue_Summary, Priority, Status`).
3. انسخ **معرّف الملف (Sheet ID)** من رابط المتصفح (الجزء الطويل بين `/d/` و `/edit`).

---

## الخطوة 2: استيراد الـ Workflow في n8n Cloud (5 دقائق)
1. افتح حسابك في [n8n.io](https://n8n.io) (التجربة المجانية 14 يوم).
2. اضغط **Create Workflow** ← ثم من القائمة العلوية (`...`) اختر **Import from File** ← واختر ملف `n8n-workflow.json`.
3. اربط 3 حسابات فقط (كل واحد بضغطة زر):
   - **Google Gemini Chat Model:** احصل على API Key مجاني من [Google AI Studio](https://aistudio.google.com/apikey) والصقه في Credentials.
   - **Log_Order_Accounting** و **Create_IT_Ticket:** سجّل دخول Google (Sign in with Google) وضع الـ **Sheet ID** اللي نسخته في الخطوة 1.
   - **Request_Human_Approval (Gmail):** سجّل دخول Gmail وضع إيميلك مكان `PUT_MANAGER_EMAIL_HERE@gmail.com`.
4. اضغط **Save** ثم فعّل زر **Active** في الأعلى (يتحول للأخضر).

---

## الخطوة 3: تشغيل الواجهة التفاعلية والـ QR Code للجمهور (3 دقائق)
عندك خياران للعرض على المسرح:

### الخيار أ (الأسرع — رابط n8n المباشر):
- افتح Node الـ **When chat message received** وانسخ الـ **Chat URL**، وحوّله لـ **QR Code** ليفتحه الجمهور من تليفوناتهم مباشرة.

### الخيار ب (الأجمل والأفخم — صفحة `index.html` اللي جهزناها):
1. افتح `index.html` بالمتصفح لتجربته فوراً (بيشتغل بوضع **Demo Mode** حتى بدون إنترنت — ممتاز كخطة احتياطية لو فصل واي فاي الجامعة!).
2. لربطه مباشرة بـ n8n Cloud: اضغط زر **⚙️ ربط n8n Cloud** بالأعلى والصق الـ **Chat URL** من n8n.
3. لنشر الصفحة أونلاين مجاناً خلال 30 ثانية عشان تطلع منها QR Code للجمهور:
   - افتح [app.netlify.com/drop](https://app.netlify.com/drop) واسحب مجلد `mini-ai-company` داخل الصفحة، رح يعطيك رابط HTTPS فوري!
4. لتغيير الشعار لصورة شعاركم: عدّل السطر `🤖` داخل `<div class="logo-box">` في ملف `index.html` وحط `<img src="logo.png">` جنب الملف.

---

## نصيحة سريعة لسيناريو العرض (3 دقائق على المسرح):
1. **الدقيقة 1:** اعرض صفحة `index.html` بوضع الشاشة المقسومة (الشات يمين + لوحة المدير يسار)، واطلب خدمة عادية ← شوف المحاسب بيسجلها لحاله.
2. **الدقيقة 2:** اكتب مشكلة تقنية ← شوف تذكرة الـ IT بتفتح لحالها بأولوية High.
3. **الدقيقة 3 (لقطة الختام — رسالة الفيديو):** اطلب خصم 30% للطلاب ← النظام **يوقف** ويبعث طلب موافقة للمدير البشري ← تكبس **موافقة** قدام الجمهور ← وتختم بجملتك: *"الذكاء الاصطناعي شال 80% من الشغل الروتيني، بس القرار دايماً بيد الإنسان!"*
