<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>تطبيق همم - النسخة المطورة</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700&display=swap');
        body { font-family: 'Tajawal', sans-serif; background-color: #f1f5f9; color: #1e293b; padding-bottom: 100px; -webkit-tap-highlight-color: transparent; }
        .card { background: white; border-radius: 20px; padding: 20px; box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05); margin-bottom: 16px; }
        
        /* تصميم أزرار التبديل (Switches) */
        .toggle-switch { position: relative; width: 50px; height: 26px; border-radius: 20px; background-color: #e2e8f0; transition: 0.3s; cursor: pointer; }
        .toggle-switch::after { content: ''; position: absolute; top: 3px; right: 3px; width: 20px; height: 20px; border-radius: 50%; background: white; transition: 0.3s; box-shadow: 0 2px 4px rgba(0,0,0,0.2); }
        .toggle-switch.active { background-color: #10b981; }
        .toggle-switch.active::after { transform: translateX(-24px); }

        /* تصميم العدادات */
        .counter-btn { width: 36px; height: 36px; border-radius: 10px; display: flex; align-items: center; justify-content: center; font-weight: bold; transition: 0.1s; }
        .counter-btn:active { transform: scale(0.9); }
        .counter-val { font-size: 1.2rem; font-weight: bold; width: 50px; text-align: center; }

        /* شريط التقدم الدائري العلوي */
        .progress-ring { width: 100%; height: 6px; background: #e2e8f0; border-radius: 4px; overflow: hidden; margin-top: 10px; }
        .progress-fill { height: 100%; background: #10b981; width: 0%; transition: width 0.5s ease; }
    </style>
</head>
<body class="bg-slate-100">

    <header class="bg-white p-5 pb-6 shadow-sm sticky top-0 z-50 rounded-b-3xl">
        <div class="flex justify-between items-end mb-2">
            <div>
                <h1 class="text-2xl font-bold text-emerald-700">تطبيق هِمم</h1>
                <p class="text-xs text-gray-500" id="currentDate">--</p>
            </div>
            <div class="text-center">
                <span id="scoreText" class="text-2xl font-bold text-emerald-600">0%</span>
                <p class="text-[10px] text-gray-400">إنجاز اليوم</p>
            </div>
        </div>
        <div class="progress-ring"><div id="progressBar" class="progress-fill"></div></div>
    </header>

    <main class="p-4 max-w-lg mx-auto">

        <section class="grid grid-cols-2 gap-3 mb-5">
            <a href="https://alazkar.today/" target="_blank" class="bg-amber-50 border border-amber-100 text-amber-800 p-4 rounded-2xl flex flex-col items-center justify-center gap-2 font-bold shadow-sm hover:bg-amber-100 transition">
                <i class="fa-solid fa-sun text-2xl text-amber-500"></i> <span class="text-sm">أذكار الصباح</span>
            </a>
            <a href="https://alazkar.today/" target="_blank" class="bg-indigo-50 border border-indigo-100 text-indigo-800 p-4 rounded-2xl flex flex-col items-center justify-center gap-2 font-bold shadow-sm hover:bg-indigo-100 transition">
                <i class="fa-solid fa-moon text-2xl text-indigo-500"></i> <span class="text-sm">أذكار المساء</span>
            </a>
        </section>

        <section class="card">
            <h2 class="font-bold text-lg mb-4 flex items-center gap-2 text-gray-700">
                <i class="fa-solid fa-mosque text-emerald-500"></i> الصلوات المفروضة
            </h2>
            <div class="space-y-4" id="prayersContainer">
                </div>
        </section>

        <section class="card">
            <div class="flex justify-between items-center mb-3">
                <h2 class="font-bold text-lg flex items-center gap-2 text-gray-700">
                    <i class="fa-solid fa-book-quran text-emerald-500"></i> القرآن الكريم
                </h2>
                <a href="https://quran.com/ar/1?startingVerse=2" target="_blank" class="text-xs bg-emerald-600 text-white px-3 py-1.5 rounded-full shadow hover:bg-emerald-700 transition flex items-center gap-1">
    <i class="fa-solid fa-book-open"></i> فتح المصحف
 </a>
            </div>
            
            <div class="bg-emerald-50 rounded-xl p-4 border border-emerald-100">
                <div class="flex justify-between items-center mb-2">
                    <span class="text-sm font-semibold text-emerald-800">عدد الصفحات</span>
                    <span class="text-xs text-emerald-600 bg-white px-2 py-1 rounded-full border border-emerald-200">الهدف: 5</span>
                </div>
                <div class="flex items-center justify-between">
                    <button onclick="updateCounter('quranPages', -1)" class="counter-btn bg-white text-emerald-600 shadow-sm border border-emerald-100"><i class="fa-solid fa-minus"></i></button>
                    <span id="val_quranPages" class="counter-val text-emerald-700">0</span>
                    <button onclick="updateCounter('quranPages', 1)" class="counter-btn bg-emerald-500 text-white shadow-emerald-200 shadow-lg"><i class="fa-solid fa-plus"></i></button>
                </div>
                <div class="w-full bg-emerald-200 h-1.5 rounded-full mt-3 overflow-hidden">
                    <div id="prog_quranPages" class="bg-emerald-500 h-full rounded-full" style="width: 0%"></div>
                </div>
            </div>
        </section>

        <section class="card">
            <h2 class="font-bold text-lg mb-4 flex items-center gap-2 text-gray-700">
                <i class="fa-solid fa-chart-simple text-blue-500"></i> بناء العادات
            </h2>
            <div class="space-y-3">
                
                <div class="bg-gray-50 p-3 rounded-xl border border-gray-100">
                    <div class="flex justify-between items-center mb-2">
                        <span class="text-sm font-bold text-gray-700"><i class="fa-solid fa-person-walking text-blue-400 ml-1"></i> المشي (دقائق)</span>
                        <span class="text-[10px] text-gray-400">الهدف: 20 د</span>
                    </div>
                    <div class="flex items-center justify-between gap-3">
                        <button onclick="updateCounter('walkMinutes', -5)" class="counter-btn bg-white border"><i class="fa-solid fa-minus"></i></button>
                        <span id="val_walkMinutes" class="font-bold text-xl w-12 text-center text-blue-600">0</span>
                        <button onclick="updateCounter('walkMinutes', 5)" class="counter-btn bg-blue-500 text-white"><i class="fa-solid fa-plus"></i></button>
                    </div>
                </div>

                <div class="bg-gray-50 p-3 rounded-xl border border-gray-100">
                    <div class="flex justify-between items-center mb-2">
                        <span class="text-sm font-bold text-gray-700"><i class="fa-solid fa-brain text-purple-400 ml-1"></i> حفظ آيات</span>
                        <span class="text-[10px] text-gray-400">الهدف: 1</span>
                    </div>
                    <div class="flex items-center justify-between gap-3">
                        <button onclick="updateCounter('ayahCount', -1)" class="counter-btn bg-white border"><i class="fa-solid fa-minus"></i></button>
                        <span id="val_ayahCount" class="font-bold text-xl w-12 text-center text-purple-600">0</span>
                        <button onclick="updateCounter('ayahCount', 1)" class="counter-btn bg-purple-500 text-white"><i class="fa-solid fa-plus"></i></button>
                    </div>
                </div>

                <div class="bg-gray-50 p-3 rounded-xl border border-gray-100">
                    <div class="flex justify-between items-center mb-2">
                        <span class="text-sm font-bold text-gray-700"><i class="fa-solid fa-language text-orange-400 ml-1"></i> جمل إنجليزية</span>
                        <span class="text-[10px] text-gray-400">الهدف: 1</span>
                    </div>
                    <div class="flex items-center justify-between gap-3">
                        <button onclick="updateCounter('englishSentences', -1)" class="counter-btn bg-white border"><i class="fa-solid fa-minus"></i></button>
                        <span id="val_englishSentences" class="font-bold text-xl w-12 text-center text-orange-600">0</span>
                        <button onclick="updateCounter('englishSentences', 1)" class="counter-btn bg-orange-500 text-white"><i class="fa-solid fa-plus"></i></button>
                    </div>
                </div>

                <div class="bg-gray-50 p-3 rounded-xl border border-gray-100">
                    <div class="flex justify-between items-center mb-2">
                        <span class="text-sm font-bold text-gray-700"><i class="fa-solid fa-book-open text-teal-400 ml-1"></i> صفحات كتاب</span>
                        <span class="text-[10px] text-gray-400">الهدف: 5</span>
                    </div>
                    <div class="flex items-center justify-between gap-3">
                        <button onclick="updateCounter('bookPages', -1)" class="counter-btn bg-white border"><i class="fa-solid fa-minus"></i></button>
                        <span id="val_bookPages" class="font-bold text-xl w-12 text-center text-teal-600">0</span>
                        <button onclick="updateCounter('bookPages', 1)" class="counter-btn bg-teal-500 text-white"><i class="fa-solid fa-plus"></i></button>
                    </div>
                </div>

                <div class="bg-blue-50 p-3 rounded-xl border border-blue-100">
                    <div class="flex justify-between items-center mb-2">
                        <span class="text-sm font-bold text-gray-700"><i class="fa-solid fa-glass-water text-blue-500 ml-1"></i> أكواب ماء</span>
                        <span class="text-[10px] text-blue-400">الهدف: 8</span>
                    </div>
                    <div class="flex items-center justify-between gap-3">
                        <button onclick="updateCounter('waterCups', -1)" class="counter-btn bg-white border border-blue-100 text-blue-500"><i class="fa-solid fa-minus"></i></button>
                        <span id="val_waterCups" class="font-bold text-xl w-12 text-center text-blue-600">0</span>
                        <button onclick="updateCounter('waterCups', 1)" class="counter-btn bg-blue-500 text-white"><i class="fa-solid fa-plus"></i></button>
                    </div>
                </div>

            </div>
        </section>

        <section class="card">
            <h2 class="font-bold text-lg mb-3 flex items-center gap-2 text-gray-700">
                <i class="fa-solid fa-users text-pink-500"></i> صلة الرحم
            </h2>
            <div class="flex flex-wrap gap-2" id="kinshipContainer"></div>
        </section>

        <section class="card">
            <h2 class="font-bold text-lg mb-2 text-gray-700"><i class="fa-solid fa-clock text-red-400"></i> التواصل الاجتماعي</h2>
            <div class="flex items-center gap-3 mb-4">
                 <button onclick="updateCounter('screenTime', -10)" class="counter-btn bg-gray-100"><i class="fa-solid fa-minus"></i></button>
                 <div class="flex-1 text-center bg-gray-50 p-2 rounded-lg border">
                     <span id="val_screenTime" class="font-bold text-xl text-gray-700">0</span> <span class="text-xs text-gray-500">دقيقة</span>
                 </div>
                 <button onclick="updateCounter('screenTime', 10)" class="counter-btn bg-gray-600 text-white"><i class="fa-solid fa-plus"></i></button>
            </div>

            <h2 class="font-bold text-lg mb-2 text-gray-700 border-t pt-4"><i class="fa-solid fa-pen-nib text-purple-400"></i> الامتنان</h2>
            <textarea id="gratitudeInput" onchange="saveGratitude()" rows="2" class="w-full p-3 rounded-xl border bg-purple-50 border-purple-100 focus:outline-none focus:border-purple-300 text-sm" placeholder="الحمدلله على..."></textarea>
        </section>

        <section class="card">
            <h2 class="font-bold text-sm text-gray-500 mb-4">أداؤك آخر 7 أيام</h2>
            <div class="h-40">
                <canvas id="performanceChart"></canvas>
            </div>
        </section>

        <div class="text-center mt-6">
            <button onclick="resetDay()" class="text-red-400 text-sm font-medium underline">تصفير بيانات اليوم</button>
        </div>

    </main>

    <script>
        // --- 1. إعداد البيانات ---
        const todayStr = new Date().toLocaleDateString('en-CA');
        let appData = JSON.parse(localStorage.getItem('hemaAppV3')) || {};

        // الأهداف الافتراضية
        const targets = {
            quranPages: 5,
            walkMinutes: 20,
            ayahCount: 1,
            englishSentences: 1,
            bookPages: 5,
            waterCups: 8
        };

        // هيكل بيانات اليوم الافتراضي
        if (!appData[todayStr]) {
            appData[todayStr] = {
                prayers: {
                    fajr: {done: false, jamaah: false, sunnah: false},
                    dhuhr: {done: false, jamaah: false, sunnah: false},
                    asr: {done: false, jamaah: false, sunnah: false},
                    maghrib: {done: false, jamaah: false, sunnah: false},
                    isha: {done: false, jamaah: false, sunnah: false}
                },
                counters: {
                    quranPages: 0,
                    walkMinutes: 0,
                    ayahCount: 0,
                    englishSentences: 0,
                    bookPages: 0,
                    waterCups: 0,
                    screenTime: 0
                },
                kinship: {},
                gratitude: '',
                score: 0
            };
        }

        let todayData = appData[todayStr];

        // --- 2. دوال العرض (Rendering) ---
        function init() {
            // التاريخ
            document.getElementById('currentDate').innerText = new Date().toLocaleDateString('ar-SA', {weekday:'long', day:'numeric', month:'long'});

            // الصلوات
            renderPrayers();

            // العدادات
            for (let key in todayData.counters) {
                renderCounterValue(key);
            }

            // صلة الرحم
            renderKinship();

            // الامتنان
            document.getElementById('gratitudeInput').value = todayData.gratitude || '';

            // النتائج والرسم
            calculateScore();
            renderChart();
        }

        // --- منطق الصلوات ---
        const prayerNames = { fajr: 'الفجر', dhuhr: 'الظهر', asr: 'العصر', maghrib: 'المغرب', isha: 'العشاء' };
        
        function renderPrayers() {
            const container = document.getElementById('prayersContainer');
            container.innerHTML = '';
            
            Object.keys(prayerNames).forEach(key => {
                const p = todayData.prayers[key];
                
                // HTML لكل صلاة
                const html = `
                <div class="bg-white border border-gray-100 rounded-xl p-3 shadow-sm">
                    <div class="flex justify-between items-center mb-3 pb-2 border-b border-gray-50">
                        <span class="font-bold text-gray-800">${prayerNames[key]}</span>
                        <div onclick="togglePrayer('${key}', 'done')" class="cursor-pointer px-3 py-1 rounded-lg text-sm transition ${p.done ? 'bg-emerald-100 text-emerald-700 font-bold' : 'bg-gray-100 text-gray-400'}">
                            ${p.done ? '<i class="fa-solid fa-check"></i> تمت' : 'لم تتم'}
                        </div>
                    </div>
                    
                    ${p.done ? `
                    <div class="flex justify-between px-2">
                        <div class="flex flex-col items-center gap-1">
                            <span class="text-[10px] text-gray-400 font-bold">جماعة؟</span>
                            <div onclick="togglePrayer('${key}', 'jamaah')" class="toggle-switch ${p.jamaah ? 'active' : ''}"></div>
                            <span class="text-[10px] ${p.jamaah ? 'text-emerald-600' : 'text-gray-400'}">${p.jamaah ? 'نعم' : 'لا'}</span>
                        </div>
                        <div class="w-px bg-gray-100 h-8"></div>
                        <div class="flex flex-col items-center gap-1">
                            <span class="text-[10px] text-gray-400 font-bold">السنن؟</span>
                            <div onclick="togglePrayer('${key}', 'sunnah')" class="toggle-switch ${p.sunnah ? 'active' : ''}"></div>
                            <span class="text-[10px] ${p.sunnah ? 'text-emerald-600' : 'text-gray-400'}">${p.sunnah ? 'نعم' : 'لا'}</span>
                        </div>
                    </div>
                    ` : '<p class="text-xs text-center text-gray-300 py-2">سجل الصلاة لتظهر الخيارات</p>'}
                </div>
                `;
                container.innerHTML += html;
            });
        }

        function togglePrayer(prayerKey, type) {
            todayData.prayers[prayerKey][type] = !todayData.prayers[prayerKey][type];
            // إذا ألغى الصلاة الرئيسية، نلغي الفرعيات منطقياً
            if(type === 'done' && !todayData.prayers[prayerKey].done) {
                todayData.prayers[prayerKey].jamaah = false;
                todayData.prayers[prayerKey].sunnah = false;
            }
            saveAndRefresh();
        }

        // --- منطق العدادات ---
        function updateCounter(key, delta) {
            let current = todayData.counters[key] || 0;
            let newVal = current + delta;
            if (newVal < 0) newVal = 0;
            
            todayData.counters[key] = newVal;
            
            // تحديث الرقم في الشاشة مباشرة (تحسين الأداء)
            renderCounterValue(key);
            calculateScore(); // تحديث النسبة
            saveToStorage();  // حفظ
        }

        function renderCounterValue(key) {
            const el = document.getElementById(`val_${key}`);
            if(el) el.innerText = todayData.counters[key];

            // تحديث شريط التقدم الصغير (للأشياء التي لها هدف)
            if (targets[key]) {
                const progEl = document.getElementById(`prog_${key}`);
                if (progEl) {
                    const pct = Math.min(100, (todayData.counters[key] / targets[key]) * 100);
                    progEl.style.width = `${pct}%`;
                    if(pct >= 100) progEl.classList.add('bg-emerald-600');
                }
            }
        }

        // --- منطق صلة الرحم ---
        const kinshipList = ['الأم', 'الأب', 'الأخت', 'بنت الأخت', 'قريب', 'قريبة'];
        function renderKinship() {
            const container = document.getElementById('kinshipContainer');
            container.innerHTML = '';
            kinshipList.forEach(k => {
                const isChecked = todayData.kinship[k];
                container.innerHTML += `
                    <button onclick="toggleKinship('${k}')" class="px-3 py-2 text-sm rounded-xl border transition flex-grow ${isChecked ? 'bg-pink-500 text-white border-pink-600 shadow-md' : 'bg-white text-gray-500 border-gray-200'}">
                        ${k}
                    </button>
                `;
            });
        }

        function toggleKinship(name) {
            todayData.kinship[name] = !todayData.kinship[name];
            saveAndRefresh();
        }

        function saveGratitude() {
            todayData.gratitude = document.getElementById('gratitudeInput').value;
            saveToStorage();
        }

        // --- الحساب والحفظ ---
        function calculateScore() {
            let points = 0;
            let totalPointsPossible = 0;

            // 1. حساب الصلوات (كل صلاة نقطتين، جماعة نقطة، سنة نقطة) = 4 * 5 = 20 نقطة
            Object.values(todayData.prayers).forEach(p => {
                totalPointsPossible += 4;
                if (p.done) points += 2;
                if (p.jamaah) points += 1;
                if (p.sunnah) points += 1;
            });

            // 2. العدادات (بناءً على تحقيق الهدف)
            const countKeys = ['quranPages', 'walkMinutes', 'ayahCount', 'englishSentences', 'bookPages', 'waterCups'];
            countKeys.forEach(k => {
                totalPointsPossible += 2; // نقطتين لكل عادة
                const val = todayData.counters[k];
                const target = targets[k];
                if (val >= target) points += 2;
                else if (val > 0) points += 1; // نصف الدرجة للمحاولة
            });

            // 3. صلة الرحم (نقطة واحدة لأي تواصل)
            totalPointsPossible += 2;
            const kinshipCount = Object.values(todayData.kinship).filter(v => v).length;
            if (kinshipCount > 0) points += 2;

            // النسبة المئوية
            const percentage = Math.round((points / totalPointsPossible) * 100);
            
            document.getElementById('scoreText').innerText = percentage + '%';
            document.getElementById('progressBar').style.width = percentage + '%';
            
            todayData.score = percentage;
        }

        function saveAndRefresh() {
            saveToStorage();
            init(); // إعادة رسم لتحديث الأزرار التي تعتمد على الحالة
        }

        function saveToStorage() {
            appData[todayStr] = todayData;
            localStorage.setItem('hemaAppV3', JSON.stringify(appData));
        }

        function resetDay() {
            if(confirm('هل أنت متأكد من تصفير العدادات لهذا اليوم؟')) {
                // إعادة تعيين كائن اليوم فقط
                appData[todayStr] = undefined; 
                location.reload();
            }
        }

        // --- الرسم البياني ---
        let myChart = null;
        function renderChart() {
            const ctx = document.getElementById('performanceChart').getContext('2d');
            const labels = [];
            const dataPoints = [];
            
            for (let i = 6; i >= 0; i--) {
                const d = new Date();
                d.setDate(d.getDate() - i);
                const k = d.toLocaleDateString('en-CA');
                const dName = d.toLocaleDateString('ar-SA', {weekday: 'short'});
                
                labels.push(dName);
                // استخدام البيانات المحفوظة أو 0
                dataPoints.push((appData[k] && appData[k].score) ? appData[k].score : 0);
            }

            if (myChart) myChart.destroy();
            myChart = new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: labels,
                    datasets: [{
                        label: 'الإنجاز %',
                        data: dataPoints,
                        backgroundColor: '#10b981',
                        borderRadius: 5
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: { beginAtZero: true, max: 100, display: false },
                        x: { grid: { display: false } }
                    },
                    plugins: { legend: { display: false } }
                }
            });
        }

        // تشغيل التطبيق
        init();

    </script>
</body>
</html>
