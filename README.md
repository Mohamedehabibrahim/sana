# MAISON Theme — دليل الاستخدام على سلة

## هيكل الملفات

```
maison-theme/
├── index.html              ← الصفحة الرئيسية (preview)
├── assets/
│   ├── css/
│   │   └── theme.css       ← كل الستايلات
│   └── js/
│       └── theme.js        ← التفاعلات والـ animations
└── README.md
```

---

## طريقة الرفع على سلة

### الطريقة 1 — Theme Builder المدمج

1. افتح لوحة تحكم سلة
2. روح على **المظهر ← محرر الثيم**
3. ارفع `theme.css` في قسم الـ CSS
4. ارفع `theme.js` في قسم الـ JavaScript
5. انسخ محتوى الـ HTML في قسم الصفحة الرئيسية

### الطريقة 2 — Custom Theme Package

1. ضغّط المجلد كـ `.zip`
2. افتح **المظهر ← رفع ثيم مخصص**
3. ارفع ملف الـ ZIP

---

## تخصيص الصور

في كل صورة، ابحث عن التعليق:
```html
<!-- في سلة: {{ section.settings.hero_image | img_url: 'master' }} -->
```
واستبدل الـ `src` بمتغير سلة المناسب.

### متغيرات سلة الشائعة:
| المكان          | المتغير                                           |
|----------------|--------------------------------------------------|
| Hero           | `{{ section.settings.hero_image }}`              |
| صور الأقسام    | `{{ collection.image \| img_url: '600x600' }}`   |
| صور المنتجات   | `{{ product.featured_image \| img_url: '500x500' }}` |
| شعار المتجر    | `{{ shop.logo }}`                                |
| اسم المتجر     | `{{ shop.name }}`                                |

---

## الألوان الرئيسية (CSS Variables)

```css
--gold:       #b8966e   /* الذهبي الرئيسي */
--dark:       #1a1a1a   /* الأسود الفاخر */
--cream:      #faf9f7   /* خلفية الصفحة */
--cream-3:    #e8dcc8   /* الكريمي الدافئ */
```

لتغيير أي لون، عدّله مرة واحدة في `:root` وبيتطبق على كل الموقع.

---

## الأقسام الموجودة

| القسم            | الوصف                              |
|------------------|------------------------------------|
| Announcement Bar | شريط الإعلانات العلوي              |
| Header / Navbar  | الهيدر الثابت مع sticky scroll     |
| Hero Section     | الصورة الرئيسية مع overlay ونص    |
| Categories Grid  | 4 أقسام بصور كاملة + hover effect |
| Products Grid    | 4 بطاقات منتجات مع quick add       |
| Promo Banner     | بانر العروض                        |
| Trust Bar        | شريط الثقة (شحن، إرجاع، أمان)      |
| Footer           | الفوتر مع روابط وسوشيال           |

---

## ملاحظات الأداء (سرعة التحميل)

- كل الصور فيها `loading="lazy"` ما عدا الـ Hero
- استخدمنا `object-fit: cover` بدل resize يدوي
- الـ CSS variables بيقلل التكرار ويخلي الملف أصغر
- الـ animations بـ CSS فقط بدون libraries ثقيلة
- الـ Google Fonts محملة بـ `preconnect` لأسرع تحميل
