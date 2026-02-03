<!DOCTYPE html>  
<html lang="zh-TW">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">  
    <title>**東京**JP**助手** V2.0</title>  
    <script src="https://cdn.tailwindcss.com"></script>  
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">  
    <style>  
        body { background-color: #f4f9ff; font-family: -apple-system, sans-serif; }  
        .fuji-blue { background: linear-gradient(135deg, #1e3a8a 0%, #3b82f6 100%); }  
        .hide-scroll::-webkit-scrollbar { display: none; }  
        .tab-btn.active { background: white; color: #1e3a8a; font-weight: bold; }  
        .checked-item { text-decoration: line-through; opacity: 0.5; }  
    </style>  
</head>  
<body class="pb-24">  
  
    <div class="bg-blue-900 text-white text-**[**10px**]** py-1 px-4 flex justify-between items-center">  
        <span><i class="fa-solid fa-plane-up mr-1"></i> **東京之旅**</span>  
        <span id="countdownDisplay" class="font-bold"></span>  
    </div>  
  
    <header class="fuji-blue text-white p-5 rounded-b-**[**35px**]** shadow-xl">  
        <div class="flex justify-between items-center mb-4">  
            <h1 class="text-xl font-black italic">**東京**JP**自由行**</h1>  
            <p class="text-**[**10px**]** bg-white/20 px-2 py-1 rounded-full uppercase tracking-tighter">LAI JIUN YAU</p>  
        </div>  
  
        <div class="bg-blue-800/50 p-1 rounded-xl flex mb-4 text-xs">  
            <button onclick="toggleFlight('go')" id="goBtn" class="tab-btn active flex-1 py-2 rounded-lg transition-all">TPE ✈ NRT (4/8)</button>  
            <button onclick="toggleFlight('back')" id="backBtn" class="tab-btn flex-1 py-2 rounded-lg transition-all">NRT ✈ TPE (4/13)</button>  
        </div>  
  
        <div id="flightContent" class="bg-white rounded-3xl p-5 text-gray-800 shadow-lg transition-all duration-300">  
            </div>  
    </header>  
  
    <main class="p-4 space-y-6">  
          
        <section>  
            <div class="flex justify-between items-end mb-3 px-1">  
                <h2 class="text-gray-700 font-bold flex items-center"><i class="fa-solid fa-cloud-sun mr-2 text-blue-500"></i> **東京**/**富士天氣**</h2>  
                <span class="text-**[**10px**]** text-gray-400">**左右滑動查看** <i class="fa-solid fa-arrow-right"></i></span>  
            </div>  
            <div class="flex space-x-3 overflow-x-auto pb-2 hide-scroll">  
                <script>  
                    const weatherData = **[**  
                        { date: '4/8', icon: 'fa-sun', temp: '18°C', vis: '**高**(20km)' },  
                        { date: '4/9', icon: 'fa-cloud', temp: '15°C', vis: '**中**(12km)' },  
                        { date: '4/10', icon: 'fa-cloud-showers-heavy', temp: '12°C', vis: '**低**(5km)' },  
                        { date: '4/11', icon: 'fa-sun', temp: '17°C', vis: '**極高**(30km)' },  
                        { date: '4/12', icon: 'fa-sun-plant-wilt', temp: '19°C', vis: '**高**(22km)' },  
                        { date: '4/13', icon: 'fa-cloud-sun', temp: '16°C', vis: '**中**(15km)' }  
                    **]**;  
                    weatherData.forEach(w => {  
                        document.write(`  
                            <div class="bg-white p-3 rounded-2xl shadow-sm min-w-**[**90px**]** text-center border border-blue-50">  
                                <p class="text-**[**10px**]** text-gray-400 font-bold">${w.date}</p>  
                                <i class="fa-solid ${w.icon} text-blue-400 text-xl my-2"></i>  
                                <p class="text-xs font-bold text-gray-700">${w.temp}</p>  
                                <p class="text-**[**9px**]** mt-1 text-blue-600 bg-blue-50 rounded-full py-0.5">**能見度**: ${w.vis}</p>  
                            </div>  
                        `);  
                    });  
                </script>  
            </div>  
        </section>  
  
        <section class="bg-white p-5 rounded-3xl shadow-sm border border-gray-100">  
            <h2 class="text-gray-700 font-bold mb-3 flex items-center"><i class="fa-solid fa-clipboard-list mr-2 text-blue-500"></i> **行前準備**</h2>  
            <div class="flex gap-2 mb-4">  
                <input type="text" id="todoInput" placeholder="**新增清單項目**..." class="flex-1 bg-gray-50 p-2 rounded-xl text-xs border-none outline-none ring-1 ring-gray-100">  
                <button onclick="addTodo()" class="bg-blue-600 text-white px-3 py-2 rounded-xl text-xs font-bold">**新增**</button>  
            </div>  
            <ul id="todoList" class="space-y-2 text-xs">  
                <li class="flex items-center justify-between p-2 bg-gray-50 rounded-lg">  
                    <div onclick="this.parentElement.classList.toggle('checked-item')" class="flex items-center cursor-pointer">  
                        <i class="fa-regular fa-circle-check mr-2 text-blue-400"></i> **護照** & **簽證**  
                    </div>  
                    <button onclick="this.parentElement.remove()" class="text-gray-300"><i class="fa-solid fa-xmark"></i></button>  
                </li>  
                <li class="flex items-center justify-between p-2 bg-gray-50 rounded-lg">  
                    <div onclick="this.parentElement.classList.toggle('checked-item')" class="flex items-center cursor-pointer">  
                        <i class="fa-regular fa-circle-check mr-2 text-blue-400"></i> **網卡** / Wi-Fi **機**  
                    </div>  
                    <button onclick="this.parentElement.remove()" class="text-gray-300"><i class="fa-solid fa-xmark"></i></button>  
                </li>  
            </ul>  
        </section>  
  
        <section class="bg-blue-900 text-white p-5 rounded-3xl shadow-lg">  
            <div class="flex justify-between items-center mb-3">  
                <h2 class="text-xs font-bold flex items-center"><i class="fa-solid fa-coins mr-2 text-yellow-400"></i> **匯率換算** (0.21)</h2>  
            </div>  
            <div class="grid grid-cols-2 gap-3">  
                <div class="bg-blue-800/50 p-2 rounded-xl">  
                    <span class="text-**[**9px**]** text-blue-300 block mb-1 uppercase">JPY</span>  
                    <input type="number" id="jpyVal" oninput="convert('jpy')" class="bg-transparent border-none text-lg font-bold w-full outline-none" placeholder="0">  
                </div>  
                <div class="bg-blue-800/50 p-2 rounded-xl">  
                    <span class="text-**[**9px**]** text-blue-300 block mb-1 uppercase">TWD</span>  
                    <input type="number" id="twdVal" oninput="convert('twd')" class="bg-transparent border-none text-lg font-bold w-full outline-none" placeholder="0">  
                </div>  
            </div>  
        </section>  
  
    </main>  
  
    <script>  
        // 1. **倒數計時功能**  
        function updateCountdown() {  
            const target = new Date('2026/04/08 00:00:00');  
            const now = new Date();  
            const diff = target - now;  
            const days = Math.ceil(diff / (1000 * 60 * 60 * 24));  
            document.getElementById('countdownDisplay').innerHTML = days > 0 ? `**距離出發還有** ${days} **天**` : `**享受你的東京之旅！**`;  
        }  
        updateCountdown();  
  
        // 2. **航班切換邏輯**  
        const flights = {  
            go: {  
                from: 'TPE', to: 'NRT', timeF: '13:10', timeT: '17:35',   
                info: 'GK 14 | **航站** 1 → 3', seat: '10B', luggage: '7KG'  
            },  
            back: {  
                from: 'NRT', to: 'TPE', timeF: '22:40', timeT: '01:30 (+1)',   
                info: 'GK 11 | **航站** 3 → 1', seat: '10F', luggage: '25KG'  
            }  
        };  
  
        function toggleFlight(type) {  
            const f = flights**[**type**]**;  
            const content = document.getElementById('flightContent');  
            const goBtn = document.getElementById('goBtn');  
            const backBtn = document.getElementById('backBtn');  
  
            goBtn.className = `tab-btn flex-1 py-2 rounded-lg ${type === 'go' ? 'active' : ''}`;  
            backBtn.className = `tab-btn flex-1 py-2 rounded-lg ${type === 'back' ? 'active' : ''}`;  
  
            content.innerHTML = `  
                <div class="flex justify-between items-center text-center">  
                    <div><p class="text-3xl font-black text-blue-900">${f.from}</p><p class="text-**[**10px**]** text-gray-400">${f.timeF}</p></div>  
                    <div class="flex-1 px-4 relative">  
                        <div class="border-t-2 border-dashed border-gray-200 w-full mt-2"></div>  
                        <i class="fa-solid fa-plane text-blue-500 absolute top-**[**-8px**]** left-1/2 -translate-x-1/2 bg-white px-2"></i>  
                        <p class="text-**[**9px**]** mt-1 text-blue-400 font-bold tracking-widest">${f.info}</p>  
                    </div>  
                    <div><p class="text-3xl font-black text-blue-900">${f.to}</p><p class="text-**[**10px**]** text-gray-400">${f.timeT}</p></div>  
                </div>  
                <div class="mt-4 pt-3 border-t border-gray-50 flex justify-around text-**[**10px**]** text-gray-500 font-bold">  
                    <span><i class="fa-solid fa-chair mr-1"></i> **座位** ${f.seat}</span>  
                    <span><i class="fa-solid fa-suitcase mr-1"></i> **托運** ${f.luggage}</span>  
                </div>  
            `;  
        }  
        toggleFlight('go'); // **初始顯示去程**  
  
        // 3. **行前準備清單**  
        function addTodo() {  
            const input = document.getElementById('todoInput');  
            if (!input.value) return;  
            const li = document.createElement('li');  
            li.className = "flex items-center justify-between p-2 bg-gray-50 rounded-lg";  
            li.innerHTML = `  
                <div onclick="this.parentElement.classList.toggle('checked-item')" class="flex items-center cursor-pointer">  
                    <i class="fa-regular fa-circle-check mr-2 text-blue-400"></i> ${input.value}  
                </div>  
                <button onclick="this.parentElement.remove()" class="text-gray-300"><i class="fa-solid fa-xmark"></i></button>  
            `;  
            document.getElementById('todoList').appendChild(li);  
            input.value = "";  
        }  
  
        // 4. **匯率換算**  
        function convert(type) {  
            const rate = 0.21;  
            const jpy = document.getElementById('jpyVal');  
            const twd = document.getElementById('twdVal');  
            if(type === 'jpy') twd.value = Math.round(jpy.value * rate);  
            else jpy.value = Math.round(twd.value / rate);  
        }  
    </script>  
</body>  
</html>  
