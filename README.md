index.html <!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>الموقع الإسلامي الرقمي</title>
    <link href="https://fonts.googleapis.com/css2?family=Amiri:wght@400;700&family=Tajawal:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-color: #0f0f10;
            --card-bg: #18181b;
            --text-color: #f4f4f5;
            --gold: #d4af37;
            --gold-light: #f3e5ab;
            --border-color: #27272a;
        }

        [data-theme="light"] {
            --bg-color: #f4f4f5;
            --card-bg: #ffffff;
            --text-color: #0f0f10;
            --gold: #b89728;
            --gold-light: #d4af37;
            --border-color: #e4e4e7;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Tajawal', sans-serif;
            transition: background 0.3s, color 0.3s;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            padding-bottom: 80px;
        }

        header {
            background-color: var(--card-bg);
            border-bottom: 1px solid var(--border-color);
            padding: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        h1, h2, h3 {
            font-family: 'Amiri', serif;
            color: var(--gold);
        }

        .theme-btn {
            background: none;
            border: 1px solid var(--gold);
            color: var(--gold);
            padding: 8px 15px;
            border-radius: 20px;
            cursor: pointer;
            font-weight: 500;
        }

        .container {
            max-width: 800px;
            margin: 20px auto;
            padding: 0 15px;
        }

        .card {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        .ayah-box {
            text-align: center;
            font-size: 1.4rem;
            line-height: 2;
            font-family: 'Amiri', serif;
            color: var(--gold-light);
        }

        .prayer-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(130px, 1fr));
            gap: 10px;
            margin-top: 15px;
        }

        .prayer-card {
            background: var(--bg-color);
            border: 1px solid var(--border-color);
            padding: 12px;
            border-radius: 10px;
            text-align: center;
        }

        .prayer-card span {
            display: block;
            font-size: 0.85rem;
            color: var(--gold);
            margin-top: 5px;
        }

        .counter-box {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 15px;
            padding-top: 15px;
            border-top: 1px solid var(--border-color);
        }

        .count-btn {
            background-color: var(--gold);
            color: #000;
            border: none;
            padding: 10px 20px;
            border-radius: 10px;
            font-weight: bold;
            cursor: pointer;
        }

        .download-btn {
            display: block;
            width: 100%;
            text-align: center;
            background: linear-gradient(135deg, var(--gold), #aa820a);
            color: #000;
            padding: 14px;
            border-radius: 12px;
            text-decoration: none;
            font-weight: bold;
            font-size: 1.1rem;
            margin-top: 10px;
        }

        /* شريط التنقل السفلي للجوال */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            background-color: var(--card-bg);
            border-top: 1px solid var(--border-color);
            display: flex;
            justify-content: space-around;
            padding: 12px 0;
            z-index: 1000;
        }

        .nav-item {
            color: var(--text-color);
            text-decoration: none;
            font-size: 0.9rem;
            text-align: center;
        }

        .nav-item.active {
            color: var(--gold);
            font-weight: bold;
        }
    </style>
</head>
<body data-theme="dark">

    <header>
        <h1>نور الإسلام</h1>
        <button class="theme-btn" onclick="toggleTheme()">الوضع المضيء/المظلم</button>
    </header>

    <div class="container">
        <!-- آية اليوم -->
        <div class="card">
            <h3>آية اليوم</h3>
            <p class="ayah-box" id="daily-ayah">"أَلَا بِذِكْرِ اللَّهِ تَطْمَئِنُّ الْقُلُوبُ"</p>
        </div>

        <!-- أوقات الصلاة -->
        <div class="card">
            <h3>أوقات الصلاة والإقامة</h3>
            <p id="location-status" style="font-size:0.9rem; color:gray; margin-bottom:10px;">جاري تحديد موقعك لتحديد الأوقات بدقة...</p>
            <div class="prayer-grid" id="prayer-times-container">
                <div class="prayer-card">الفجر <br><b>04:15 ص</b><span>الإقامة: 04:28 ص</span></div>
                <div class="prayer-card">الشروق <br><b>05:45 ص</b><span>-</span></div>
                <div class="prayer-card">الظهر <br><b>12:15 م</b><span>الإقامة: 12:28 م</span></div>
                <div class="prayer-card">العصر <br><b>03:40 م</b><span>الإقامة: 03:53 م</span></div>
                <div class="prayer-card">المغرب <br><b>06:30 م</b><span>الإقامة: 06:38 م</span></div>
                <div class="prayer-card">العشاء <br><b>08:00 م</b><span>الإقامة: 08:13 م</span></div>
            </div>
        </div>

        <!-- الأذكار -->
        <div class="card">
            <h3>أذكار الصباح والمساء</h3>
            <p style="margin-top: 10px; font-size: 1.1rem;">سُبْحَانَ اللَّهِ وَبِحَمْدِهِ</p>
            <div class="counter-box">
                <span id="counter-value">العدد: 0</span>
                <button class="count-btn" onclick="incrementCounter()">تسبيح (+1)</button>
            </div>
        </div>

        <!-- معلومات يوم الجمعة -->
        <div class="card">
            <h3>فضائل يوم الجمعة</h3>
            <p style="line-height: 1.8; margin-top: 10px;">
                - الإكثار من الصلاة على النبي ﷺ.<br>
                - قراءة سورة الكهف.<br>
                - ساعة الاستجابة آخر ساعة بعد العصر.
            </p>
        </div>

        <!-- تحميل المصحف -->
        <div class="card" style="text-align: center;">
            <h3>المصحف الشريف</h3>
            <p style="margin: 10px 0; color: gray;">احصل على نسخة رقمية كاملة من المصحف الشريف بصيغة PDF.</p>
            <a href="#" class="download-btn" onclick="alert('سيتم بدء تحميل المصحف الشريف فوراً'); return false;">تحميل المصحف الشريف (PDF)</a>
        </div>
    </div>

    <!-- شريط التنقل السفلي -->
    <div class="bottom-nav">
        <a href="#" class="nav-item active">الرئيسية</a>
        <a href="#" class="nav-item">الأذكار</a>
        <a href="#" class="nav-item">المصحف</a>
        <a href="#" class="nav-item">الجمعة</a>
    </div>

    <script>
        // تبديل الوضع الليلي والنهاري
        function toggleTheme() {
            const body = document.body;
            if (body.getAttribute('data-theme') === 'dark') {
                body.setAttribute('data-theme', 'light');
            } else {
                body.setAttribute('data-theme', 'dark');
            }
        }

        // عداد الأذكار البسيط
        let count = 0;
        function incrementCounter() {
            count++;
            document.getElementById('counter-value').innerText = "العدد: " + count;
        }

        // محاكاة جلب الموقع الجغرافي
        if (navigator.geolocation) {
            navigator.geolocation.getCurrentPosition(function(position) {
                document.getElementById('location-status').innerText = "تم تحديد موقعك بدقة (حسب إحداثيات المتصفح).";
            }, function(error) {
                document.getElementById('location-status').innerText = "تعذر تحديد الموقع تلقائياً، يتم عرض الأوقات الافتراضية.";
            });
        }
    </script>
</body>
</html>
