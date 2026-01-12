<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مُتابِع الروتين اليومي</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #f3f4f6; }
        .checkbox-wrapper { display: flex; align-items: center; gap: 10px; margin-bottom: 5px; }
        input[type="checkbox"] { width: 20px; height: 20px; accent-color: #10b981; }
        .card { background: white; padding: 20px; border-radius: 12px; box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1); margin-bottom: 20px; }
        h2 { color: #1f2937; font-weight: bold; margin-bottom: 15px; border-bottom: 2px solid #e5e7eb; padding-bottom: 5px; }
    </style>
</head>
<body class="p-4 max-w-2xl mx-auto">

    <header class="text-center mb-6">
        <h1 class="text-3xl font-bold text-emerald-600">همم تعانق القمم 🚀</h1>
        <p class="text-gray-600 mt-2">نموذج متابعة الروتين اليومي</p>
        <p id="dateDisplay" class="text-sm text-gray-500 mt-1"></p>
    </header>

    <section class="card">
        <h2>🕌 1. الصلوات المفروضة</h2>
        <div class="overflow-x-auto">
            <table class="w-full text-center text-sm">
                <thead>
                    <tr class="bg-gray-100">
                        <th class="p-2">الصلاة</th>
                        <th class="p-2">أديتها؟</th>
                        <th class="p-2">جماعة؟</th>
                        <th class="p-2">السنن؟</th>
                    </tr>
                </thead>
                <tbody id="prayersTable">
                    </tbody>
            </table>
        </div>
    </section>

    <section class="card">
        <h2>📖 2. القرآن الكريم</h2>
        <label class="checkbox-wrapper p-2 bg-emerald-50 rounded cursor-pointer">
            <input type="checkbox" id="quranCheck">
            <span class="font-medium">قراءة 5 صفحات من المصحف</span>
        </label>
    </section>

    <section class="card">
        <h2>📿 3. الأذكار</h2>
        <div class="grid grid-cols-1 gap-2">
            <label class="checkbox-wrapper"><input type="checkbox" id="adhkarMorning"> أذكار الصباح</label>
            <label class="checkbox-wrapper"><input type="checkbox" id="adhkarEvening"> أذكار المساء</label>
            <label class="checkbox-wrapper"><input type="checkbox" id="adhkarPostPrayer"> أذكار بعد الصلوات</label>
        </div>
    </section>

    <section class="card">
        <h2>🌱 4. بناء العادات</h2>
        <div class="grid grid-cols-1 gap-2">
            <label class="checkbox-wrapper"><input type="checkbox" id="habitWalk"> 🚶 مشي لمدة 20 دقيقة</label>
            <label class="checkbox-wrapper"><input type="checkbox" id="habitAyah"> 🧠 حفظ آية من القرآن</label>
            <label class="checkbox-wrapper"><input type="checkbox" id="habitEnglish"> 🗣️ إتقان جملة إنجليزية</label>
            <label class="checkbox-wrapper"><input type="checkbox" id="habitBook"> 📚 قراءة في كتاب</label>
            <label class="checkbox-wrapper"><input type="checkbox" id="habitLecture"> 🎧 سماع محاضرة</label>
        </div>
    </section>

    <section class="card">
        <h2>📞 5. صلة الرحم (بمن اتصلت اليوم؟)</h2>
        <div class="grid grid-cols-2 gap-2" id="kinshipContainer">
            </div>
    </section>

    <section class="card">
        <h2>📱 6. وقت الترفيه</h2>
        <div class="flex flex-col gap-2">
            <label class="text-sm text-gray-700">الوقت المقضي على وسائل التواصل (بالدقائق):</label>
            <input type="number" id="screenTime" class="border p-2 rounded w-full" placeholder="مثلاً: 60">
        </div>
    </section>

    <div class="flex gap-4 mb-10">
        <button onclick="saveData()" class="flex-1 bg-emerald-600 text-white py-3 rounded-lg font-bold shadow hover:bg-emerald-700 transition">حفظ التقدم ✅</button>
        <button onclick="resetData()" class="flex-1 bg-red-500 text-white py-3 rounded-lg font-bold shadow hover:bg-red-600 transition">بدء يوم جديد 🔄</button>
    </div>

    <script>
        // إعداد التاريخ
        const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
        document.getElementById('dateDisplay').innerText = new Date().toLocaleDateString('ar-SA', options);

        // البيانات
        const prayers = ['الفجر', 'الظهر', 'العصر', 'المغرب', 'العشاء'];
        const relatives = ['الأم', 'الأب', 'الأخت', 'بنت الأخت', 'قريب', 'قريبة'];

        // توليد جدول الصلوات
        const prayersTable = document.getElementById('prayersTable');
        prayers.forEach((prayer, index) => {
            const row = `
                <tr class="border-b">
                    <td class="font-bold p-2">${prayer}</td>
                    <td><input type="checkbox" id="p_${index}_done"></td>
                    <td><input type="checkbox" id="p_${index}_jamaah"></td>
                    <td><input type="checkbox" id="p_${index}_sunnah"></td>
                </tr>
            `;
            prayersTable.innerHTML += row;
        });

        // توليد قائمة صلة الرحم
        const kinshipContainer = document.getElementById('kinshipContainer');
        relatives.forEach((relative, index) => {
            const item = `
                <label class="checkbox-wrapper bg-gray-50 p-2 rounded">
                    <input type="checkbox" id="k_${index}"> ${relative}
                </label>
            `;
            kinshipContainer.innerHTML += item;
        });

        // دالة الحفظ
        function saveData() {
            const data = {};
            
            // حفظ الصلوات
            for(let i=0; i<5; i++) {
                data[`p_${i}_done`] = document.getElementById(`p_${i}_done`).checked;
                data[`p_${i}_jamaah`] = document.getElementById(`p_${i}_jamaah`).checked;
                data[`p_${i}_sunnah`] = document.getElementById(`p_${i}_sunnah`).checked;
            }

            // حفظ القرآن والأذكار والعادات
            const ids = ['quranCheck', 'adhkarMorning', 'adhkarEvening', 'adhkarPostPrayer', 
                         'habitWalk', 'habitAyah', 'habitEnglish', 'habitBook', 'habitLecture'];
            ids.forEach(id => data[id] = document.getElementById(id).checked);

            // حفظ صلة الرحم
            for(let i=0; i<relatives.length; i++) {
                data[`k_${i}`] = document.getElementById(`k_${i}`).checked;
            }

            // حفظ وقت الشاشة
            data['screenTime'] = document.getElementById('screenTime').value;

            localStorage.setItem('dailyRoutineData', JSON.stringify(data));
            alert('تم حفظ تقدمك لليوم! بارك الله في وقتك.');
        }

        // دالة استرجاع البيانات
        function loadData() {
            const saved = localStorage.getItem('dailyRoutineData');
            if (saved) {
                const data = JSON.parse(saved);
                
                // استرجاع الصلوات
                for(let i=0; i<5; i++) {
                    if(data[`p_${i}_done`]) document.getElementById(`p_${i}_done`).checked = true;
                    if(data[`p_${i}_jamaah`]) document.getElementById(`p_${i}_jamaah`).checked = true;
                    if(data[`p_${i}_sunnah`]) document.getElementById(`p_${i}_sunnah`).checked = true;
                }

                // استرجاع الباقي
                const ids = ['quranCheck', 'adhkarMorning', 'adhkarEvening', 'adhkarPostPrayer', 
                             'habitWalk', 'habitAyah', 'habitEnglish', 'habitBook', 'habitLecture'];
                ids.forEach(id => {
                    if(data[id]) document.getElementById(id).checked = true;
                });

                // استرجاع صلة الرحم
                for(let i=0; i<relatives.length; i++) {
                    if(data[`k_${i}`]) document.getElementById(`k_${i}`).checked = true;
                }

                // استرجاع وقت الشاشة
                if(data['screenTime']) document.getElementById('screenTime').value = data['screenTime'];
            }
        }

        // دالة تصفير البيانات
        function resetData() {
            if(confirm('هل أنت متأكد من بدء يوم جديد وتصفير العدادات؟')) {
                localStorage.removeItem('dailyRoutineData');
                location.reload();
            }
        }

        // تشغيل الاسترجاع عند التحميل
        loadData();

    </script>
</body>
</html>
