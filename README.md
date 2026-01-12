<html lang="th" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>เกมผันคำกริยา て形</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;500;700&amp;family=Noto+Sans+Thai:wght@400;500;600;700&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
    }
    * {
      font-family: 'Noto Sans Thai', 'Noto Sans JP', sans-serif;
    }
    .japanese {
      font-family: 'Noto Sans JP', 'Noto Sans Thai', sans-serif;
      font-weight: 500;
    }
    .tab-active {
      background: linear-gradient(135deg, #ff6b9d 0%, #c06c84 100%);
      color: white;
      transform: translateY(-2px);
      box-shadow: 0 4px 15px rgba(255, 107, 157, 0.4);
    }
    .card-hover:hover {
      transform: translateY(-4px);
      box-shadow: 0 12px 40px rgba(0, 0, 0, 0.15);
    }
    .shake {
      animation: shake 0.5s ease-in-out;
    }
    @keyframes shake {
      0%, 100% { transform: translateX(0); }
      25% { transform: translateX(-10px); }
      75% { transform: translateX(10px); }
    }
    .bounce-in {
      animation: bounceIn 0.5s ease-out;
    }
    @keyframes bounceIn {
      0% { transform: scale(0.3); opacity: 0; }
      50% { transform: scale(1.05); }
      100% { transform: scale(1); opacity: 1; }
    }
    .fade-in {
      animation: fadeIn 0.4s ease-out;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
    .flashcard {
      perspective: 1000px;
      height: 200px;
    }
    .flashcard-inner {
      position: relative;
      width: 100%;
      height: 100%;
      transition: transform 0.6s;
      transform-style: preserve-3d;
    }
    .flashcard.flipped .flashcard-inner {
      transform: rotateY(180deg);
    }
    .flashcard-front, .flashcard-back {
      position: absolute;
      width: 100%;
      height: 100%;
      backface-visibility: hidden;
      border-radius: 1rem;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      padding: 1.5rem;
      cursor: pointer;
    }
    .flashcard-front {
      background: linear-gradient(135deg, #ffffff 0%, #f8fafc 100%);
      border: 2px solid #e2e8f0;
    }
    .flashcard-back {
      background: linear-gradient(135deg, #ffeaa7 0%, #fdcb6e 100%);
      color: #2d3436;
      transform: rotateY(180deg);
    }
    .progress-bar {
      background: linear-gradient(90deg, #10b981 0%, #34d399 100%);
      transition: width 0.5s ease-out;
    }
    .memory-card {
      perspective: 1000px;
      cursor: pointer;
      height: 140px;
    }
    .memory-card-inner {
      position: relative;
      width: 100%;
      height: 100%;
      transition: transform 0.6s;
      transform-style: preserve-3d;
    }
    .memory-card.flipped .memory-card-inner,
    .memory-card.matched .memory-card-inner {
      transform: rotateY(180deg);
    }
    .memory-card-front, .memory-card-back {
      position: absolute;
      width: 100%;
      height: 100%;
      backface-visibility: hidden;
      border-radius: 0.75rem;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 1rem;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }
    .memory-card-front {
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      font-size: 3rem;
    }
    .memory-card-back {
      background: white;
      transform: rotateY(180deg);
      border: 2px solid #e2e8f0;
    }
    .memory-card.matched .memory-card-back {
      background: linear-gradient(135deg, #84fab0 0%, #8fd3f4 100%);
      border-color: #10b981;
    }
    .memory-card.wrong {
      animation: wrongShake 0.5s ease-in-out;
    }
    @keyframes wrongShake {
      0%, 100% { transform: translateX(0); }
      25% { transform: translateX(-5px) rotate(-2deg); }
      75% { transform: translateX(5px) rotate(2deg); }
    }
    .pulse {
      animation: pulse 1s ease-in-out infinite;
    }
    @keyframes pulse {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.05); }
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full bg-gradient-to-br from-pink-100 via-purple-100 to-blue-100">
  <div id="app" class="h-full w-full overflow-auto">
   <header class="bg-white/80 backdrop-blur-sm shadow-sm sticky top-0 z-50">
    <div class="max-w-6xl mx-auto px-4 py-4">
     <h1 id="main-title" class="text-2xl md:text-3xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-pink-600 to-purple-600 text-center japanese">🎌 เกมผันคำกริยา～て形</h1>
     <p id="subtitle" class="text-center text-gray-600 mt-1">เรียนรู้การผันคำกริยาภาษาญี่ปุ่นอย่างสนุกสนาน!</p>
    </div>
   </header>
   <nav class="max-w-6xl mx-auto px-4 mt-6">
    <div class="flex flex-wrap justify-center gap-2 md:gap-3"><button onclick="window.showTab('group1')" id="tab-group1" class="tab-btn px-4 py-2 md:px-6 md:py-3 rounded-xl font-semibold transition-all duration-300 bg-white shadow-md hover:shadow-lg text-gray-700 text-sm md:text-base"> 📚 กลุ่ม 1 </button> <button onclick="window.showTab('group2')" id="tab-group2" class="tab-btn px-4 py-2 md:px-6 md:py-3 rounded-xl font-semibold transition-all duration-300 bg-white shadow-md hover:shadow-lg text-gray-700 text-sm md:text-base"> 📗 กลุ่ม 2 </button> <button onclick="window.showTab('group3')" id="tab-group3" class="tab-btn px-4 py-2 md:px-6 md:py-3 rounded-xl font-semibold transition-all duration-300 bg-white shadow-md hover:shadow-lg text-gray-700 text-sm md:text-base"> 📙 กลุ่ม 3 </button> <button onclick="window.showTab('quiz')" id="tab-quiz" class="tab-btn px-4 py-2 md:px-6 md:py-3 rounded-xl font-semibold transition-all duration-300 bg-white shadow-md hover:shadow-lg text-gray-700 text-sm md:text-base"> 🎯 แบบทดสอบ </button> <button onclick="window.showTab('memory')" id="tab-memory" class="tab-btn px-4 py-2 md:px-6 md:py-3 rounded-xl font-semibold transition-all duration-300 bg-white shadow-md hover:shadow-lg text-gray-700 text-sm md:text-base"> 🎴 เกมจับคู่ </button>
    </div>
   </nav>
   <main class="max-w-6xl mx-auto px-4 py-6">
    <section id="content-group1" class="content-section" style="display: none;">
     <div class="bg-white rounded-2xl shadow-xl p-6 md:p-8 fade-in">
      <div class="flex items-center gap-3 mb-6"><span class="text-4xl">📚</span>
       <div>
        <h2 class="text-2xl font-bold text-indigo-700">กลุ่ม 1 (五段動詞 / Godan)</h2>
        <p class="text-gray-600">คำกริยาที่ลงท้ายด้วย う、く、ぐ、す、つ、ぬ、ぶ、む、る</p>
       </div>
      </div>
      <div class="bg-gradient-to-r from-blue-50 to-cyan-50 rounded-xl p-5 mb-6 border-l-4 border-blue-400">
       <h3 class="font-bold text-blue-800 mb-3 text-lg">📝 กฎการผัน</h3>
       <div class="grid grid-cols-1 md:grid-cols-2 gap-3 text-sm md:text-base">
        <div class="bg-white/70 rounded-lg p-3"><span class="font-bold text-red-500 japanese">う・つ・る</span> → <span class="font-bold text-green-600 japanese">って</span>
        </div>
        <div class="bg-white/70 rounded-lg p-3"><span class="font-bold text-red-500 japanese">む・ぬ・ぶ</span> → <span class="font-bold text-green-600 japanese">んで</span>
        </div>
        <div class="bg-white/70 rounded-lg p-3"><span class="font-bold text-red-500 japanese">く</span> → <span class="font-bold text-green-600 japanese">いて</span>
        </div>
        <div class="bg-white/70 rounded-lg p-3"><span class="font-bold text-red-500 japanese">ぐ</span> → <span class="font-bold text-green-600 japanese">いで</span>
        </div>
        <div class="bg-white/70 rounded-lg p-3"><span class="font-bold text-red-500 japanese">す</span> → <span class="font-bold text-green-600 japanese">して</span>
        </div>
        <div class="bg-white/70 rounded-lg p-3 md:col-span-2 bg-yellow-50 border border-yellow-300"><span class="text-yellow-700">⚠️ ยกเว้น:</span> <span class="font-bold japanese">行く（いく）</span> → <span class="font-bold text-green-600 japanese">行って（いって）</span>
        </div>
       </div>
      </div>
      <h3 class="font-bold text-gray-800 mb-4 text-lg">📚 คำศัพท์ JLPT N5</h3>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4" id="group1-cards"></div>
     </div>
    </section>
    <section id="content-group2" class="content-section" style="display: none;">
     <div class="bg-white rounded-2xl shadow-xl p-6 md:p-8 fade-in">
      <div class="flex items-center gap-3 mb-6"><span class="text-4xl">📗</span>
       <div>
        <h2 class="text-2xl font-bold text-emerald-700">กลุ่ม 2 (一段動詞 / Ichidan)</h2>
        <p class="text-gray-600">คำกริยาที่ลงท้ายด้วย いる、える</p>
       </div>
      </div>
      <div class="bg-gradient-to-r from-green-50 to-teal-50 rounded-xl p-5 mb-6 border-l-4 border-green-400">
       <h3 class="font-bold text-green-800 mb-3 text-lg">📝 กฎการผัน</h3>
       <div class="bg-white/70 rounded-lg p-4">
        <p class="text-lg">ตัด <span class="font-bold text-red-500 japanese">る</span> แล้วเติม <span class="font-bold text-green-600 japanese">て</span></p>
        <p class="text-gray-600 mt-2">ตัวอย่าง: <span class="japanese">食べる → 食べて</span></p>
       </div>
      </div>
      <h3 class="font-bold text-gray-800 mb-4 text-lg">📚 คำศัพท์ JLPT N5</h3>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4" id="group2-cards"></div>
     </div>
    </section>
    <section id="content-group3" class="content-section" style="display: none;">
     <div class="bg-white rounded-2xl shadow-xl p-6 md:p-8 fade-in">
      <div class="flex items-center gap-3 mb-6"><span class="text-4xl">📙</span>
       <div>
        <h2 class="text-2xl font-bold text-orange-700">กลุ่ม 3 (不規則動詞 / Irregular)</h2>
        <p class="text-gray-600">คำกริยาพิเศษ (する、来る)</p>
       </div>
      </div>
      <div class="bg-gradient-to-r from-orange-50 to-yellow-50 rounded-xl p-5 mb-6 border-l-4 border-orange-400">
       <h3 class="font-bold text-orange-800 mb-3 text-lg">📝 กฎการผัน</h3>
       <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
        <div class="bg-white/70 rounded-lg p-4"><span class="font-bold japanese text-lg">する</span> → <span class="font-bold text-green-600 japanese text-lg">して</span>
         <p class="text-gray-600 text-sm mt-1">ทำ</p>
        </div>
        <div class="bg-white/70 rounded-lg p-4"><span class="font-bold japanese text-lg">来る（くる）</span> → <span class="font-bold text-green-600 japanese text-lg">来て（きて）</span>
         <p class="text-gray-600 text-sm mt-1">มา</p>
        </div>
       </div>
      </div>
      <h3 class="font-bold text-gray-800 mb-4 text-lg">📚 คำศัพท์ JLPT N5</h3>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4" id="group3-cards"></div>
     </div>
    </section>
    <section id="content-quiz" class="content-section" style="display: none;">
     <div class="bg-white rounded-2xl shadow-xl p-6 md:p-8 fade-in">
      <div class="flex items-center justify-between mb-6 flex-wrap gap-4">
       <div class="flex items-center gap-3"><span class="text-4xl">🎯</span>
        <div>
         <h2 class="text-2xl font-bold text-purple-700">แบบทดสอบ</h2>
         <p class="text-gray-600">ทดสอบความรู้การผัน て形</p>
        </div>
       </div><button onclick="window.startQuiz()" id="start-quiz-btn" class="px-6 py-3 bg-gradient-to-r from-pink-500 to-purple-500 text-white rounded-xl font-semibold hover:shadow-lg transition-all duration-300 hover:scale-105"> 🚀 เริ่มทำแบบทดสอบ </button>
      </div>
      <div id="quiz-settings" class="bg-gradient-to-r from-purple-50 to-indigo-50 rounded-xl p-5 mb-6">
       <h3 class="font-bold text-purple-800 mb-4">⚙️ ตั้งค่าแบบทดสอบ</h3>
       <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div><label class="block text-gray-700 font-medium mb-2">จำนวนข้อ</label> <select id="quiz-count" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-purple-500 focus:border-transparent"> <option value="5">5 ข้อ</option> <option value="10" selected>10 ข้อ</option> <option value="15">15 ข้อ</option> <option value="20">20 ข้อ</option> </select>
        </div>
        <div><label class="block text-gray-700 font-medium mb-2">เลือกกลุ่ม</label> <select id="quiz-group" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-purple-500 focus:border-transparent"> <option value="all" selected>ทุกกลุ่ม</option> <option value="1">กลุ่ม 1 เท่านั้น</option> <option value="2">กลุ่ม 2 เท่านั้น</option> <option value="3">กลุ่ม 3 เท่านั้น</option> </select>
        </div>
       </div>
      </div>
      <div id="quiz-area" style="display: none;">
       <div class="mb-6">
        <div class="flex justify-between text-sm text-gray-600 mb-2"><span id="quiz-progress-text">ข้อ 1 / 10</span> <span id="quiz-score-text">คะแนน: 0</span>
        </div>
        <div class="h-3 bg-gray-200 rounded-full overflow-hidden">
         <div id="quiz-progress-bar" class="h-full progress-bar" style="width: 0%"></div>
        </div>
       </div>
       <div id="quiz-question-card" class="bg-gradient-to-br from-pink-100 to-purple-100 rounded-2xl p-6 md:p-8 text-center mb-6">
        <p class="text-gray-600 mb-2" id="quiz-group-label">กลุ่ม 1</p>
        <p class="text-4xl md:text-5xl font-bold japanese mb-4" id="quiz-word">書く</p>
        <p class="text-gray-600" id="quiz-reading">（かく）</p>
        <p class="text-lg text-gray-700 mt-2" id="quiz-meaning">เขียน</p>
       </div>
       <div class="mb-6"><label class="block text-gray-700 font-medium mb-2 text-center">พิมพ์รูป て形</label> <input type="text" id="quiz-answer" class="w-full p-4 text-2xl text-center border-2 border-gray-300 rounded-xl focus:ring-2 focus:ring-purple-500 focus:border-purple-500 japanese" placeholder="พิมพ์คำตอบที่นี่...">
        <p class="text-center text-sm text-gray-500 mt-2">พิมพ์ด้วยฮิรางานะหรือคันจิ แล้วกด Enter หรือคลิกปุ่มตรวจ</p>
       </div>
       <div class="flex justify-center gap-4 flex-wrap"><button onclick="window.checkAnswer()" class="px-8 py-3 bg-gradient-to-r from-green-400 to-teal-400 text-white rounded-xl font-semibold hover:shadow-lg transition-all duration-300 hover:scale-105"> ✅ ตรวจคำตอบ </button> <button onclick="window.showHint()" id="hint-btn" class="px-8 py-3 bg-gradient-to-r from-yellow-400 to-orange-400 text-white rounded-xl font-semibold hover:shadow-lg transition-all duration-300 hover:scale-105"> 💡 ดูคำใบ้ </button> <button onclick="window.skipQuestion()" class="px-8 py-3 bg-gray-400 text-white rounded-xl font-semibold hover:shadow-lg transition-all duration-300 hover:scale-105 hover:bg-gray-500"> ⏭️ ข้ามข้อ </button>
       </div>
       <div id="hint-area" style="display: none;" class="mt-4 bg-yellow-50 border border-yellow-300 rounded-xl p-4 text-center">
        <p class="text-yellow-800" id="hint-text"></p>
       </div>
       <div id="feedback-area" style="display: none;" class="mt-6"></div>
      </div>
      <div id="results-area" style="display: none;">
       <div class="text-center">
        <div class="text-6xl mb-4" id="result-emoji">
         🎉
        </div>
        <h3 class="text-2xl font-bold text-gray-800 mb-2" id="result-title">ยินดีด้วย!</h3>
        <p class="text-gray-600 mb-6" id="result-message">คุณทำได้ดีมาก!</p>
        <div class="bg-gradient-to-r from-pink-100 to-purple-100 rounded-2xl p-6 mb-6 inline-block">
         <p class="text-5xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-pink-600 to-purple-600" id="final-score">8 / 10</p>
         <p class="text-gray-600 mt-2" id="score-percentage">80%</p>
        </div>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6">
         <div class="bg-green-50 rounded-xl p-4">
          <p class="text-3xl font-bold text-green-600" id="correct-count">8</p>
          <p class="text-gray-600">ถูกต้อง</p>
         </div>
         <div class="bg-red-50 rounded-xl p-4">
          <p class="text-3xl font-bold text-red-600" id="wrong-count">2</p>
          <p class="text-gray-600">ผิด</p>
         </div>
         <div class="bg-gray-50 rounded-xl p-4">
          <p class="text-3xl font-bold text-gray-600" id="skip-count">0</p>
          <p class="text-gray-600">ข้าม</p>
         </div>
        </div>
        <div id="advice-section" class="bg-gradient-to-r from-blue-50 to-indigo-50 rounded-xl p-5 mb-6 text-left">
         <h4 class="font-bold text-indigo-800 mb-3">💡 คำแนะนำสำหรับคุณ</h4>
         <div id="advice-content"></div>
        </div>
        <div id="mistakes-section" style="display: none;" class="mb-6">
         <h4 class="font-bold text-gray-800 mb-3 text-left">📝 ทบทวนข้อที่ผิด</h4>
         <div id="mistakes-list" class="space-y-3"></div>
        </div>
        <div class="flex justify-center gap-4 flex-wrap"><button onclick="window.startQuiz()" class="px-8 py-3 bg-gradient-to-r from-pink-500 to-purple-500 text-white rounded-xl font-semibold hover:shadow-lg transition-all duration-300 hover:scale-105"> 🔁 ทำแบบทดสอบใหม่ </button> <button onclick="window.showTab('group1')" class="px-8 py-3 bg-gradient-to-r from-blue-500 to-blue-600 text-white rounded-xl font-semibold hover:shadow-lg transition-all duration-300 hover:scale-105"> 📚 กลับไปทบทวน </button>
        </div>
       </div>
      </div>
     </div>
    </section>
    <section id="content-memory" class="content-section" style="display: none;">
     <div class="bg-white rounded-2xl shadow-xl p-6 md:p-8 fade-in">
      <div class="flex items-center justify-between mb-6 flex-wrap gap-4">
       <div class="flex items-center gap-3"><span class="text-4xl">🎴</span>
        <div>
         <h2 class="text-2xl font-bold text-pink-700">เกมจับคู่บัตรคำ</h2>
         <p class="text-gray-600">พลิกบัตรและจับคู่กริยากับรูป て形</p>
        </div>
       </div><button onclick="window.startMemoryGame()" id="start-memory-btn" class="px-6 py-3 bg-gradient-to-r from-pink-500 to-purple-500 text-white rounded-xl font-semibold hover:shadow-lg transition-all duration-300 hover:scale-105"> 🚀 เริ่มเกม </button>
      </div>
      <div id="memory-settings" class="bg-gradient-to-r from-pink-50 to-purple-50 rounded-xl p-5 mb-6">
       <h3 class="font-bold text-purple-800 mb-4">⚙️ ตั้งค่าเกม</h3>
       <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div><label class="block text-gray-700 font-medium mb-2">จำนวนคู่</label> <select id="memory-pairs" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-pink-500 focus:border-transparent"> <option value="4">4 คู่ (ง่าย)</option> <option value="6" selected>6 คู่ (ปานกลาง)</option> <option value="8">8 คู่ (ยาก)</option> </select>
        </div>
        <div><label class="block text-gray-700 font-medium mb-2">เวลาจับคู่</label> <select id="memory-time" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-pink-500 focus:border-transparent"> <option value="15">15 วินาที (ยาก)</option> <option value="20" selected>20 วินาที (ปานกลาง)</option> <option value="25">25 วินาที (ง่าย)</option> </select>
        </div>
       </div>
      </div>
      <div id="memory-game-area" style="display: none;">
       <div class="mb-6">
        <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-4">
         <div class="bg-gradient-to-r from-blue-50 to-blue-100 rounded-xl p-3 text-center">
          <p class="text-2xl font-bold text-blue-600" id="memory-score">0</p>
          <p class="text-xs text-gray-600">คะแนน</p>
         </div>
         <div class="bg-gradient-to-r from-green-50 to-green-100 rounded-xl p-3 text-center">
          <p class="text-2xl font-bold text-green-600" id="memory-matched">0</p>
          <p class="text-xs text-gray-600">จับคู่ได้</p>
         </div>
         <div class="bg-gradient-to-r from-orange-50 to-orange-100 rounded-xl p-3 text-center">
          <p class="text-2xl font-bold text-orange-600" id="memory-moves">0</p>
          <p class="text-xs text-gray-600">ครั้งที่พลิก</p>
         </div>
         <div class="bg-gradient-to-r from-red-50 to-red-100 rounded-xl p-3 text-center">
          <p class="text-2xl font-bold text-red-600" id="memory-timer">20</p>
          <p class="text-xs text-gray-600">วินาที</p>
         </div>
        </div>
        <div id="memory-board" class="grid grid-cols-3 sm:grid-cols-4 md:grid-cols-6 gap-3"></div>
       </div>
      </div>
      <div id="memory-results" style="display: none;" class="text-center">
       <div class="text-6xl mb-4" id="memory-result-emoji">
        🎉
       </div>
       <h3 class="text-2xl font-bold text-gray-800 mb-2" id="memory-result-title">ยอดเยี่ยม!</h3>
       <p class="text-gray-600 mb-6" id="memory-result-message">คุณจับคู่ได้หมดภายในเวลาที่กำหนด!</p>
       <div class="bg-gradient-to-r from-pink-100 to-purple-100 rounded-2xl p-6 mb-6 inline-block">
        <p class="text-5xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-pink-600 to-purple-600" id="memory-final-score">100</p>
        <p class="text-gray-600 mt-2">คะแนน</p>
       </div>
       <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6 max-w-2xl mx-auto">
        <div class="bg-blue-50 rounded-xl p-4">
         <p class="text-3xl font-bold text-blue-600" id="memory-final-time">15</p>
         <p class="text-gray-600">วินาทีที่ใช้</p>
        </div>
        <div class="bg-green-50 rounded-xl p-4">
         <p class="text-3xl font-bold text-green-600" id="memory-final-moves">12</p>
         <p class="text-gray-600">ครั้งที่พลิก</p>
        </div>
        <div class="bg-purple-50 rounded-xl p-4">
         <p class="text-3xl font-bold text-purple-600" id="memory-final-accuracy">100%</p>
         <p class="text-gray-600">ความแม่นยำ</p>
        </div>
       </div>
       <div class="flex justify-center gap-4 flex-wrap"><button onclick="window.startMemoryGame()" class="px-8 py-3 bg-gradient-to-r from-pink-500 to-purple-500 text-white rounded-xl font-semibold hover:shadow-lg transition-all duration-300 hover:scale-105"> 🔁 เล่นอีกครั้ง </button> <button onclick="window.showTab('group1')" class="px-8 py-3 bg-gradient-to-r from-blue-500 to-blue-600 text-white rounded-xl font-semibold hover:shadow-lg transition-all duration-300 hover:scale-105"> 📚 กลับไปทบทวน </button>
       </div>
      </div>
     </div>
    </section>
   </main>
   <footer class="text-center py-6 text-gray-600 text-base font-medium">
    <p>🌸 ニコニコ日本語ｂｙエー先生 ⭐</p>
   </footer>
  </div>
  <script>
    const defaultConfig = {
      main_title: '🎌 เกมผันคำกริยา～て形',
      subtitle: 'เรียนรู้การผันคำกริยาภาษาญี่ปุ่นอย่างสนุกสนาน!'
    };

    const group1Verbs = [
      { dict: '書く', reading: 'かく', te: '書いて', teReading: 'かいて', meaning: 'เขียน', rule: 'く→いて' },
      { dict: '聞く', reading: 'きく', te: '聞いて', teReading: 'きいて', meaning: 'ฟัง', rule: 'く→いて' },
      { dict: '行く', reading: 'いく', te: '行って', teReading: 'いって', meaning: 'ไป', rule: 'ยกเว้น! く→って' },
      { dict: '泳ぐ', reading: 'およぐ', te: '泳いで', teReading: 'およいで', meaning: 'ว่ายน้ำ', rule: 'ぐ→いで' },
      { dict: '話す', reading: 'はなす', te: '話して', teReading: 'はなして', meaning: 'พูด', rule: 'す→して' },
      { dict: '待つ', reading: 'まつ', te: '待って', teReading: 'まって', meaning: 'รอ', rule: 'つ→って' },
      { dict: '持つ', reading: 'もつ', te: '持って', teReading: 'もって', meaning: 'ถือ', rule: 'つ→って' },
      { dict: '死ぬ', reading: 'しぬ', te: '死んで', teReading: 'しんで', meaning: 'ตาย', rule: 'ぬ→んで' },
      { dict: '読む', reading: 'よむ', te: '読んで', teReading: 'よんで', meaning: 'อ่าน', rule: 'む→んで' },
      { dict: '飲む', reading: 'のむ', te: '飲んで', teReading: 'のんで', meaning: 'ดื่ม', rule: 'む→んで' },
      { dict: '遊ぶ', reading: 'あそぶ', te: '遊んで', teReading: 'あそんで', meaning: 'เล่น', rule: 'ぶ→んで' },
      { dict: '呼ぶ', reading: 'よぶ', te: '呼んで', teReading: 'よんで', meaning: 'เรียก', rule: 'ぶ→んで' },
      { dict: '買う', reading: 'かう', te: '買って', teReading: 'かって', meaning: 'ซื้อ', rule: 'う→って' },
      { dict: '会う', reading: 'あう', te: '会って', teReading: 'あって', meaning: 'พบ', rule: 'う→って' },
      { dict: '歌う', reading: 'うたう', te: '歌って', teReading: 'うたって', meaning: 'ร้องเพลง', rule: 'う→って' },
      { dict: '作る', reading: 'つくる', te: '作って', teReading: 'つくって', meaning: 'ทำ/สร้าง', rule: 'る→って' },
      { dict: '撮る', reading: 'とる', te: '撮って', teReading: 'とって', meaning: 'ถ่ายรูป', rule: 'る→って' },
      { dict: '分かる', reading: 'わかる', te: '分かって', teReading: 'わかって', meaning: 'เข้าใจ', rule: 'る→って' },
      { dict: '帰る', reading: 'かえる', te: '帰って', teReading: 'かえって', meaning: 'กลับบ้าน', rule: 'る→って' },
      { dict: '入る', reading: 'はいる', te: '入って', teReading: 'はいって', meaning: 'เข้า', rule: 'る→って' },
      { dict: '乗る', reading: 'のる', te: '乗って', teReading: 'のって', meaning: 'ขึ้น(ยานพาหนะ)', rule: 'る→って' },
      { dict: '走る', reading: 'はしる', te: '走って', teReading: 'はしって', meaning: 'วิ่ง', rule: 'る→って' },
      { dict: '立つ', reading: 'たつ', te: '立って', teReading: 'たって', meaning: 'ยืน', rule: 'つ→って' },
      { dict: '座る', reading: 'すわる', te: '座って', teReading: 'すわって', meaning: 'นั่ง', rule: 'る→って' },
      { dict: '使う', reading: 'つかう', te: '使って', teReading: 'つかって', meaning: 'ใช้', rule: 'う→って' }
    ];

    const group2Verbs = [
      { dict: '食べる', reading: 'たべる', te: '食べて', teReading: 'たべて', meaning: 'กิน', rule: 'る→て' },
      { dict: '見る', reading: 'みる', te: '見て', teReading: 'みて', meaning: 'ดู', rule: 'る→て' },
      { dict: '寝る', reading: 'ねる', te: '寝て', teReading: 'ねて', meaning: 'นอน', rule: 'る→て' },
      { dict: '起きる', reading: 'おきる', te: '起きて', teReading: 'おきて', meaning: 'ตื่น', rule: 'る→て' },
      { dict: '開ける', reading: 'あける', te: '開けて', teReading: 'あけて', meaning: 'เปิด', rule: 'る→て' },
      { dict: '閉める', reading: 'しめる', te: '閉めて', teReading: 'しめて', meaning: 'ปิด', rule: 'る→て' },
      { dict: '教える', reading: 'おしえる', te: '教えて', teReading: 'おしえて', meaning: 'สอน', rule: 'る→て' },
      { dict: '覚える', reading: 'おぼえる', te: '覚えて', teReading: 'おぼえて', meaning: 'จำ', rule: 'る→て' },
      { dict: '忘れる', reading: 'わすれる', te: '忘れて', teReading: 'わすれて', meaning: 'ลืม', rule: 'る→て' },
      { dict: '着る', reading: 'きる', te: '着て', teReading: 'きて', meaning: 'สวม', rule: 'る→て' },
      { dict: '出る', reading: 'でる', te: '出て', teReading: 'でて', meaning: 'ออก', rule: 'る→て' },
      { dict: 'いる', reading: 'いる', te: 'いて', teReading: 'いて', meaning: 'อยู่(สิ่งมีชีวิต)', rule: 'る→て' },
      { dict: '浴びる', reading: 'あびる', te: '浴びて', teReading: 'あびて', meaning: 'อาบ', rule: 'る→て' },
      { dict: '借りる', reading: 'かりる', te: '借りて', teReading: 'かりて', meaning: 'ยืม', rule: 'る→て' },
      { dict: '降りる', reading: 'おりる', te: '降りて', teReading: 'おりて', meaning: 'ลง', rule: 'る→て' }
    ];

    const group3Verbs = [
      { dict: 'する', reading: 'する', te: 'して', teReading: 'して', meaning: 'ทำ', rule: 'する→して' },
      { dict: '来る', reading: 'くる', te: '来て', teReading: 'きて', meaning: 'มา', rule: '来る→来て' },
      { dict: '勉強する', reading: 'べんきょうする', te: '勉強して', teReading: 'べんきょうして', meaning: 'เรียน', rule: 'する→して' },
      { dict: '散歩する', reading: 'さんぽする', te: '散歩して', teReading: 'さんぽして', meaning: 'เดินเล่น', rule: 'する→して' },
      { dict: '買い物する', reading: 'かいものする', te: '買い物して', teReading: 'かいものして', meaning: 'ช็อปปิ้ง', rule: 'する→して' },
      { dict: '掃除する', reading: 'そうじする', te: '掃除して', teReading: 'そうじして', meaning: 'ทำความสะอาด', rule: 'する→して' },
      { dict: '洗濯する', reading: 'せんたくする', te: '洗濯して', teReading: 'せんたくして', meaning: 'ซักผ้า', rule: 'する→して' },
      { dict: '料理する', reading: 'りょうりする', te: '料理して', teReading: 'りょうりして', meaning: 'ทำอาหาร', rule: 'する→して' },
      { dict: '電話する', reading: 'でんわする', te: '電話して', teReading: 'でんわして', meaning: 'โทรศัพท์', rule: 'する→して' },
      { dict: '結婚する', reading: 'けっこんする', te: '結婚して', teReading: 'けっこんして', meaning: 'แต่งงาน', rule: 'する→して' }
    ];

    let quizState = {
      questions: [],
      currentIndex: 0,
      score: 0,
      wrongAnswers: [],
      skipped: 0,
      isActive: false
    };

    let memoryState = {
      cards: [],
      flippedCards: [],
      matchedPairs: 0,
      moves: 0,
      score: 0,
      timeLimit: 20,
      timeLeft: 20,
      timerInterval: null,
      isActive: false,
      canFlip: true,
      totalPairs: 0
    };

    function speak(text) {
      if ('speechSynthesis' in window) {
        window.speechSynthesis.cancel();
        const utterance = new SpeechSynthesisUtterance(text);
        utterance.lang = 'ja-JP';
        utterance.rate = 0.8;
        utterance.pitch = 1;
        window.speechSynthesis.speak(utterance);
      }
    }

    function init() {
      renderVocabularyCards();
      showTab('group1');
      const answerInput = document.getElementById('quiz-answer');
      if (answerInput) {
        answerInput.addEventListener('keypress', function(e) {
          if (e.key === 'Enter') {
            e.preventDefault();
            checkAnswer();
          }
        });
      }
    }

    function renderVocabularyCards() {
      const g1Container = document.getElementById('group1-cards');
      const g2Container = document.getElementById('group2-cards');
      const g3Container = document.getElementById('group3-cards');
      
      if (g1Container) g1Container.innerHTML = group1Verbs.map(v => createVerbCard({...v, group: 1}, 'indigo')).join('');
      if (g2Container) g2Container.innerHTML = group2Verbs.map(v => createVerbCard({...v, group: 2}, 'emerald')).join('');
      if (g3Container) g3Container.innerHTML = group3Verbs.map(v => createVerbCard({...v, group: 3}, 'orange')).join('');
    }

    function createVerbCard(verb, color) {
      const cardId = 'card-' + Math.random().toString(36).substr(2, 9);
      return `
        <div class="flashcard" id="${cardId}" onclick="window.flipCard('${cardId}')">
          <div class="flashcard-inner">
            <div class="flashcard-front shadow-lg">
              <div class="text-xs bg-${color}-100 text-${color}-700 px-3 py-1 rounded-full mb-2">กลุ่ม ${verb.group}</div>
              <div class="text-4xl font-bold japanese mb-1">${verb.dict}</div>
              <div class="text-gray-500 text-base">（${verb.reading}）</div>
              <div class="mt-3 text-xs text-gray-400">👆 คลิกเพื่อพลิก</div>
            </div>
            <div class="flashcard-back shadow-xl">
              <div class="text-xs bg-orange-200 text-orange-800 px-3 py-1 rounded-full mb-2">${verb.rule}</div>
              <div class="flex items-center justify-center gap-2 mb-1">
                <span class="text-4xl font-bold japanese">${verb.te}</span>
                <button onclick="event.stopPropagation(); window.speak('${verb.teReading}')" class="text-2xl hover:scale-125 transition-transform duration-200" title="ฟังเสียง">
                  🔊
                </button>
              </div>
              <div class="text-gray-700 text-base mb-2">（${verb.teReading}）</div>
              <div class="text-xl font-semibold mt-2">📖 ${verb.meaning}</div>
              <div class="mt-3 text-xs text-gray-600">👆 คลิกเพื่อพลิกกลับ</div>
            </div>
          </div>
        </div>
      `;
    }

    function flipCard(cardId) {
      const card = document.getElementById(cardId);
      if (card) card.classList.toggle('flipped');
    }

    function showTab(tabId) {
      document.querySelectorAll('.content-section').forEach(s => s.style.display = 'none');
      document.querySelectorAll('.tab-btn').forEach(t => t.classList.remove('tab-active'));
      const contentEl = document.getElementById('content-' + tabId);
      const tabEl = document.getElementById('tab-' + tabId);
      if (contentEl) contentEl.style.display = 'block';
      if (tabEl) tabEl.classList.add('tab-active');
    }

    function startQuiz() {
      const countEl = document.getElementById('quiz-count');
      const groupEl = document.getElementById('quiz-group');
      if (!countEl || !groupEl) return;
      
      const count = parseInt(countEl.value);
      const group = groupEl.value;
      let availableVerbs = [];
      
      if (group === 'all') {
        availableVerbs = [...group1Verbs.map(v => ({...v, group: 1})), ...group2Verbs.map(v => ({...v, group: 2})), ...group3Verbs.map(v => ({...v, group: 3}))];
      } else if (group === '1') {
        availableVerbs = group1Verbs.map(v => ({...v, group: 1}));
      } else if (group === '2') {
        availableVerbs = group2Verbs.map(v => ({...v, group: 2}));
      } else {
        availableVerbs = group3Verbs.map(v => ({...v, group: 3}));
      }
      
      const shuffled = availableVerbs.sort(() => Math.random() - 0.5);
      quizState = {
        questions: shuffled.slice(0, Math.min(count, shuffled.length)),
        currentIndex: 0,
        score: 0,
        wrongAnswers: [],
        skipped: 0,
        isActive: true
      };
      
      const settingsEl = document.getElementById('quiz-settings');
      const startBtnEl = document.getElementById('start-quiz-btn');
      const areaEl = document.getElementById('quiz-area');
      const resultsEl = document.getElementById('results-area');
      
      if (settingsEl) settingsEl.style.display = 'none';
      if (startBtnEl) startBtnEl.style.display = 'none';
      if (areaEl) areaEl.style.display = 'block';
      if (resultsEl) resultsEl.style.display = 'none';
      
      showQuestion();
    }

    function showQuestion() {
      const q = quizState.questions[quizState.currentIndex];
      const groupLabelEl = document.getElementById('quiz-group-label');
      const wordEl = document.getElementById('quiz-word');
      const readingEl = document.getElementById('quiz-reading');
      const meaningEl = document.getElementById('quiz-meaning');
      const answerEl = document.getElementById('quiz-answer');
      const hintAreaEl = document.getElementById('hint-area');
      const feedbackEl = document.getElementById('feedback-area');
      const hintBtnEl = document.getElementById('hint-btn');
      
      if (groupLabelEl) groupLabelEl.textContent = 'กลุ่ม ' + q.group;
      if (wordEl) wordEl.textContent = q.dict;
      if (readingEl) readingEl.textContent = '（' + q.reading + '）';
      if (meaningEl) meaningEl.textContent = q.meaning;
      if (answerEl) {
        answerEl.value = '';
        answerEl.focus();
      }
      if (hintAreaEl) hintAreaEl.style.display = 'none';
      if (feedbackEl) feedbackEl.style.display = 'none';
      if (hintBtnEl) hintBtnEl.disabled = false;
      
      updateProgress();
    }

    function updateProgress() {
      const total = quizState.questions.length;
      const current = quizState.currentIndex + 1;
      const progress = (quizState.currentIndex / total) * 100;
      
      const progressTextEl = document.getElementById('quiz-progress-text');
      const scoreTextEl = document.getElementById('quiz-score-text');
      const progressBarEl = document.getElementById('quiz-progress-bar');
      
      if (progressTextEl) progressTextEl.textContent = 'ข้อ ' + current + ' / ' + total;
      if (scoreTextEl) scoreTextEl.textContent = 'คะแนน: ' + quizState.score;
      if (progressBarEl) progressBarEl.style.width = progress + '%';
    }

    function showHint() {
      const q = quizState.questions[quizState.currentIndex];
      const hintTextEl = document.getElementById('hint-text');
      const hintAreaEl = document.getElementById('hint-area');
      const hintBtnEl = document.getElementById('hint-btn');
      
      if (hintTextEl) hintTextEl.innerHTML = 'กฎการผัน: ' + q.rule + '<br>คำตอบขึ้นต้นด้วย: <span class="japanese font-bold">' + q.te.charAt(0) + '</span>';
      if (hintAreaEl) hintAreaEl.style.display = 'block';
      if (hintBtnEl) hintBtnEl.disabled = true;
    }

    function checkAnswer() {
      if (!quizState.isActive) return;
      const answerEl = document.getElementById('quiz-answer');
      if (!answerEl) return;
      
      const userAnswer = answerEl.value.trim();
      const q = quizState.questions[quizState.currentIndex];
      const correctAnswers = [q.te, q.teReading];
      const feedbackArea = document.getElementById('feedback-area');
      
      if (!feedbackArea) return;
      feedbackArea.style.display = 'block';
      
      if (correctAnswers.includes(userAnswer)) {
        quizState.score++;
        feedbackArea.innerHTML = '<div class="bg-green-100 border border-green-400 rounded-xl p-4 text-center bounce-in"><p class="text-2xl mb-2">🎉 ถูกต้อง!</p><p class="text-green-700 japanese text-xl">' + q.dict + ' → ' + q.te + '</p></div>';
      } else {
        quizState.wrongAnswers.push({question: q, userAnswer: userAnswer || '(ไม่ได้ตอบ)'});
        feedbackArea.innerHTML = '<div class="bg-red-100 border border-red-400 rounded-xl p-4 text-center shake"><p class="text-2xl mb-2">❌ ไม่ถูกต้อง</p><p class="text-gray-700">คำตอบที่ถูกคือ: <span class="font-bold japanese text-xl text-red-700">' + q.te + '</span> (' + q.teReading + ')</p><p class="text-gray-600 mt-2">กฎ: ' + q.rule + '</p></div>';
      }
      
      setTimeout(nextQuestion, 1500);
    }

    function skipQuestion() {
      if (!quizState.isActive) return;
      const q = quizState.questions[quizState.currentIndex];
      quizState.skipped++;
      quizState.wrongAnswers.push({question: q, userAnswer: '(ข้าม)'});
      
      const feedbackEl = document.getElementById('feedback-area');
      if (feedbackEl) {
        feedbackEl.style.display = 'block';
        feedbackEl.innerHTML = '<div class="bg-gray-100 border border-gray-400 rounded-xl p-4 text-center"><p class="text-xl mb-2">⏭️ ข้ามข้อนี้</p><p class="text-gray-700">คำตอบคือ: <span class="font-bold japanese text-xl">' + q.te + '</span></p></div>';
      }
      
      setTimeout(nextQuestion, 1500);
    }

    function nextQuestion() {
      quizState.currentIndex++;
      if (quizState.currentIndex >= quizState.questions.length) {
        showResults();
      } else {
        showQuestion();
      }
    }

    function showResults() {
      quizState.isActive = false;
      
      const areaEl = document.getElementById('quiz-area');
      const resultsEl = document.getElementById('results-area');
      
      if (areaEl) areaEl.style.display = 'none';
      if (resultsEl) resultsEl.style.display = 'block';
      
      const total = quizState.questions.length;
      const score = quizState.score;
      const percentage = Math.round((score / total) * 100);
      const wrong = total - score;
      
      const finalScoreEl = document.getElementById('final-score');
      const scorePercentEl = document.getElementById('score-percentage');
      const correctCountEl = document.getElementById('correct-count');
      const wrongCountEl = document.getElementById('wrong-count');
      const skipCountEl = document.getElementById('skip-count');
      
      if (finalScoreEl) finalScoreEl.textContent = score + ' / ' + total;
      if (scorePercentEl) scorePercentEl.textContent = percentage + '%';
      if (correctCountEl) correctCountEl.textContent = score;
      if (wrongCountEl) wrongCountEl.textContent = wrong - quizState.skipped;
      if (skipCountEl) skipCountEl.textContent = quizState.skipped;
      
      const resultEmoji = document.getElementById('result-emoji');
      const resultTitle = document.getElementById('result-title');
      const resultMessage = document.getElementById('result-message');
      
      if (percentage >= 90) {
        if (resultEmoji) resultEmoji.textContent = '🏆';
        if (resultTitle) resultTitle.textContent = 'ยอดเยี่ยมมาก!';
        if (resultMessage) resultMessage.textContent = 'คุณเก่งมากๆ เลย! เป็นผู้ชำนาญ て形 แล้ว!';
      } else if (percentage >= 70) {
        if (resultEmoji) resultEmoji.textContent = '🎉';
        if (resultTitle) resultTitle.textContent = 'ดีมาก!';
        if (resultMessage) resultMessage.textContent = 'คุณทำได้ดีมาก! ฝึกฝนอีกนิดจะเก่งขึ้นอีก!';
      } else if (percentage >= 50) {
        if (resultEmoji) resultEmoji.textContent = '👍';
        if (resultTitle) resultTitle.textContent = 'พอใช้ได้!';
        if (resultMessage) resultMessage.textContent = 'กำลังพัฒนาได้ดี ลองทบทวนกฎและฝึกเพิ่มนะ!';
      } else {
        if (resultEmoji) resultEmoji.textContent = '💪';
        if (resultTitle) resultTitle.textContent = 'สู้ๆ นะ!';
        if (resultMessage) resultMessage.textContent = 'อย่าท้อนะ! ลองกลับไปดูกฎการผันแล้วฝึกใหม่อีกครั้ง!';
      }
      
      generateAdvice(percentage);
      
      const mistakesSection = document.getElementById('mistakes-section');
      const mistakesList = document.getElementById('mistakes-list');
      
      if (quizState.wrongAnswers.length > 0 && mistakesList) {
        if (mistakesSection) mistakesSection.style.display = 'block';
        mistakesList.innerHTML = quizState.wrongAnswers.map(item => 
          '<div class="bg-red-50 border border-red-200 rounded-lg p-3 text-left"><div class="flex justify-between items-start"><div><span class="font-bold japanese">' + item.question.dict + '</span><span class="text-gray-500 text-sm">(' + item.question.reading + ')</span></div><span class="text-xs bg-gray-200 px-2 py-1 rounded">กลุ่ม ' + item.question.group + '</span></div><p class="text-sm text-gray-600 mt-1">คำตอบของคุณ: <span class="text-red-600">' + item.userAnswer + '</span></p><p class="text-sm text-gray-600">คำตอบที่ถูก: <span class="text-green-600 font-bold japanese">' + item.question.te + '</span> (' + item.question.teReading + ')</p><p class="text-xs text-gray-500 mt-1">กฎ: ' + item.question.rule + '</p></div>'
        ).join('');
      } else {
        if (mistakesSection) mistakesSection.style.display = 'none';
      }
    }

    function generateAdvice(percentage) {
      const wrongGroups = {1: 0, 2: 0, 3: 0};
      quizState.wrongAnswers.forEach(item => wrongGroups[item.question.group]++);
      
      let advice = [];
      
      if (wrongGroups[1] > 0) {
        advice.push('<div class="bg-indigo-50 rounded-lg p-3 mb-2"><p class="font-semibold text-indigo-800">📚 กลุ่ม 1 (' + wrongGroups[1] + ' ข้อ)</p><p class="text-sm text-gray-700">ทบทวนกฎ: う・つ・る→って, む・ぬ・ぶ→んで, く→いて, ぐ→いで, す→して</p><p class="text-sm text-gray-600">💡 จำง่ายๆ: "อิ-ชิ-ต๊ะ-นะ" (いて・して・って・んで)</p></div>');
      }
      
      if (wrongGroups[2] > 0) {
        advice.push('<div class="bg-emerald-50 rounded-lg p-3 mb-2"><p class="font-semibold text-emerald-800">📗 กลุ่ม 2 (' + wrongGroups[2] + ' ข้อ)</p><p class="text-sm text-gray-700">กฎง่ายที่สุด: แค่ตัด る แล้วเติม て</p><p class="text-sm text-gray-600">⚠️ ระวัง! บางคำที่ลงท้าย いる/える อาจเป็นกลุ่ม 1 ก็ได้</p></div>');
      }
      
      if (wrongGroups[3] > 0) {
        advice.push('<div class="bg-orange-50 rounded-lg p-3 mb-2"><p class="font-semibold text-orange-800">📙 กลุ่ม 3 (' + wrongGroups[3] + ' ข้อ)</p><p class="text-sm text-gray-700">จำแค่ 2 คำ: する→して และ 来る→来て</p><p class="text-sm text-gray-600">💡 คำที่ลงท้าย する ทั้งหมดผันเป็น して</p></div>');
      }
      
      if (percentage >= 90) {
        advice.push('<div class="bg-green-50 rounded-lg p-3"><p class="font-semibold text-green-800">⭐ คำแนะนำระดับสูง</p><p class="text-sm text-gray-700">คุณเก่งมากแล้ว! ลองฝึกใช้ て形 ในประโยคจริง เช่น:</p><p class="text-sm japanese mt-1">• ～てください (กรุณา...)</p><p class="text-sm japanese">• ～ている (กำลัง...)</p><p class="text-sm japanese">• ～てもいい (ขอ...ได้ไหม)</p></div>');
      } else if (percentage < 50) {
        advice.push('<div class="bg-yellow-50 rounded-lg p-3"><p class="font-semibold text-yellow-800">🚀 เริ่มต้นใหม่</p><p class="text-sm text-gray-700">แนะนำให้:</p><p class="text-sm">1. ทบทวนกฎแต่ละกลุ่มอีกครั้ง</p><p class="text-sm">2. ท่องจำคำกริยาพร้อมรูป て形</p><p class="text-sm">3. ฝึกทำแบบทดสอบทีละกลุ่ม</p></div>');
      }
      
      const adviceContent = document.getElementById('advice-content');
      if (adviceContent) adviceContent.innerHTML = advice.join('');
    }

    async function onConfigChange(newConfig) {
      const titleEl = document.getElementById('main-title');
      const subtitleEl = document.getElementById('subtitle');
      
      if (titleEl) titleEl.textContent = newConfig.main_title || defaultConfig.main_title;
      if (subtitleEl) subtitleEl.textContent = newConfig.subtitle || defaultConfig.subtitle;
    }

    function startMemoryGame() {
      const pairsEl = document.getElementById('memory-pairs');
      const timeEl = document.getElementById('memory-time');
      if (!pairsEl || !timeEl) return;
      
      const pairs = parseInt(pairsEl.value);
      const timeLimit = parseInt(timeEl.value);
      
      let allVerbs = [...group1Verbs, ...group2Verbs, ...group3Verbs];
      allVerbs = allVerbs.sort(() => Math.random() - 0.5).slice(0, pairs);
      
      let cards = [];
      allVerbs.forEach((verb, index) => {
        cards.push({
          id: 'dict-' + index,
          type: 'dict',
          verb: verb,
          text: verb.dict,
          subtext: verb.reading
        });
        cards.push({
          id: 'te-' + index,
          type: 'te',
          verb: verb,
          text: verb.te,
          subtext: verb.teReading
        });
      });
      
      cards = cards.sort(() => Math.random() - 0.5);
      
      memoryState = {
        cards: cards,
        flippedCards: [],
        matchedPairs: 0,
        moves: 0,
        score: 0,
        timeLimit: timeLimit,
        timeLeft: timeLimit,
        timerInterval: null,
        isActive: true,
        canFlip: true,
        totalPairs: pairs
      };
      
      const settingsEl = document.getElementById('memory-settings');
      const startBtnEl = document.getElementById('start-memory-btn');
      const gameAreaEl = document.getElementById('memory-game-area');
      const resultsEl = document.getElementById('memory-results');
      
      if (settingsEl) settingsEl.style.display = 'none';
      if (startBtnEl) startBtnEl.style.display = 'none';
      if (gameAreaEl) gameAreaEl.style.display = 'block';
      if (resultsEl) resultsEl.style.display = 'none';
      
      renderMemoryBoard();
      updateMemoryStats();
      startMemoryTimer();
    }

    function renderMemoryBoard() {
      const board = document.getElementById('memory-board');
      if (!board) return;
      
      board.innerHTML = memoryState.cards.map(card => `
        <div class="memory-card" id="card-${card.id}" onclick="window.flipMemoryCard('${card.id}')">
          <div class="memory-card-inner">
            <div class="memory-card-front">
              🎴
            </div>
            <div class="memory-card-back">
              <div class="text-center">
                <div class="text-2xl font-bold japanese">${card.text}</div>
                <div class="text-xs text-gray-500 japanese mt-1">${card.subtext}</div>
              </div>
            </div>
          </div>
        </div>
      `).join('');
    }

    function flipMemoryCard(cardId) {
      if (!memoryState.isActive || !memoryState.canFlip) return;
      
      const cardElement = document.getElementById('card-' + cardId);
      if (!cardElement) return;
      if (cardElement.classList.contains('flipped') || cardElement.classList.contains('matched')) return;
      
      cardElement.classList.add('flipped');
      const card = memoryState.cards.find(c => c.id === cardId);
      memoryState.flippedCards.push(card);
      
      if (memoryState.flippedCards.length === 2) {
        memoryState.canFlip = false;
        memoryState.moves++;
        updateMemoryStats();
        checkMemoryMatch();
      }
    }

    function checkMemoryMatch() {
      const [card1, card2] = memoryState.flippedCards;
      const card1Element = document.getElementById('card-' + card1.id);
      const card2Element = document.getElementById('card-' + card2.id);
      
      if (!card1Element || !card2Element) return;
      
      setTimeout(() => {
        if (card1.verb === card2.verb && card1.type !== card2.type) {
          card1Element.classList.add('matched');
          card2Element.classList.add('matched');
          memoryState.matchedPairs++;
          memoryState.score += 10;
          
          if (memoryState.matchedPairs === memoryState.totalPairs) {
            setTimeout(() => endMemoryGame(true), 500);
          }
        } else {
          card1Element.classList.add('wrong');
          card2Element.classList.add('wrong');
          
          setTimeout(() => {
            card1Element.classList.remove('flipped', 'wrong');
            card2Element.classList.remove('flipped', 'wrong');
          }, 800);
        }
        
        memoryState.flippedCards = [];
        memoryState.canFlip = true;
        updateMemoryStats();
      }, 600);
    }

    function startMemoryTimer() {
      memoryState.timerInterval = setInterval(() => {
        memoryState.timeLeft--;
        updateMemoryStats();
        
        if (memoryState.timeLeft <= 0) {
          endMemoryGame(false);
        } else if (memoryState.timeLeft <= 5) {
          const timerEl = document.getElementById('memory-timer');
          if (timerEl && timerEl.parentElement) {
            timerEl.parentElement.classList.add('pulse');
          }
        }
      }, 1000);
    }

    function updateMemoryStats() {
      const scoreEl = document.getElementById('memory-score');
      const matchedEl = document.getElementById('memory-matched');
      const movesEl = document.getElementById('memory-moves');
      const timerEl = document.getElementById('memory-timer');
      
      if (scoreEl) scoreEl.textContent = memoryState.score;
      if (matchedEl) matchedEl.textContent = memoryState.matchedPairs + ' / ' + memoryState.totalPairs;
      if (movesEl) movesEl.textContent = memoryState.moves;
      if (timerEl) timerEl.textContent = memoryState.timeLeft;
    }

    function endMemoryGame(won) {
      memoryState.isActive = false;
      if (memoryState.timerInterval) clearInterval(memoryState.timerInterval);
      
      const gameAreaEl = document.getElementById('memory-game-area');
      const resultsEl = document.getElementById('memory-results');
      
      if (gameAreaEl) gameAreaEl.style.display = 'none';
      if (resultsEl) resultsEl.style.display = 'block';
      
      const timeUsed = memoryState.timeLimit - memoryState.timeLeft;
      const accuracy = memoryState.moves > 0 ? Math.round((memoryState.matchedPairs * 2 / memoryState.moves) * 100) : 100;
      
      const emojiEl = document.getElementById('memory-result-emoji');
      const titleEl = document.getElementById('memory-result-title');
      const messageEl = document.getElementById('memory-result-message');
      
      if (won) {
        const timeBonus = memoryState.timeLeft * 2;
        memoryState.score += timeBonus;
        
        if (emojiEl) emojiEl.textContent = '🏆';
        if (titleEl) titleEl.textContent = 'ยอดเยี่ยม!';
        if (messageEl) messageEl.textContent = 'คุณจับคู่ได้หมดภายในเวลาที่กำหนด!';
      } else {
        if (emojiEl) emojiEl.textContent = '⏰';
        if (titleEl) titleEl.textContent = 'หมดเวลา!';
        if (messageEl) messageEl.textContent = 'ลองใหม่อีกครั้งนะ! คุณเกือบได้แล้ว';
      }
      
      const finalScoreEl = document.getElementById('memory-final-score');
      const finalTimeEl = document.getElementById('memory-final-time');
      const finalMovesEl = document.getElementById('memory-final-moves');
      const finalAccuracyEl = document.getElementById('memory-final-accuracy');
      
      if (finalScoreEl) finalScoreEl.textContent = memoryState.score;
      if (finalTimeEl) finalTimeEl.textContent = timeUsed + ' วินาที';
      if (finalMovesEl) finalMovesEl.textContent = memoryState.moves;
      if (finalAccuracyEl) finalAccuracyEl.textContent = accuracy + '%';
    }

    // Make functions globally accessible
    window.showTab = showTab;
    window.flipCard = flipCard;
    window.speak = speak;
    window.startQuiz = startQuiz;
    window.checkAnswer = checkAnswer;
    window.showHint = showHint;
    window.skipQuestion = skipQuestion;
    window.startMemoryGame = startMemoryGame;
    window.flipMemoryCard = flipMemoryCard;

    // Initialize Element SDK
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities: () => ({
          recolorables: [],
          borderables: [],
          fontEditable: undefined,
          fontSizeable: undefined
        }),
        mapToEditPanelValues: () => new Map([
          ['main_title', window.elementSdk.config.main_title || defaultConfig.main_title],
          ['subtitle', window.elementSdk.config.subtitle || defaultConfig.subtitle]
        ])
      });
    }

    // Initialize app when DOM is ready
    if (document.readyState === 'loading') {
      document.addEventListener('DOMContentLoaded', init);
    } else {
      init();
    }
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9bc6b279275845b9',t:'MTc2ODE1ODQ0OC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
