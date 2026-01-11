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
      font-weight: 400;
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
    .glow {
      box-shadow: 0 0 20px rgba(102, 126, 234, 0.5);
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
    <div class="flex flex-wrap justify-center gap-2 md:gap-3"><button onclick="showTab('group1')" id="tab-group1" class="tab-btn px-4 py-2 md:px-6 md:py-3 rounded-xl font-semibold transition-all duration-300 bg-white shadow-md hover:shadow-lg text-gray-700 text-sm md:text-base"> 📚 กลุ่ม 1 </button> <button onclick="showTab('group2')" id="tab-group2" class="tab-btn px-4 py-2 md:px-6 md:py-3 rounded-xl font-semibold transition-all duration-300 bg-white shadow-md hover:shadow-lg text-gray-700 text-sm md:text-base"> 📗 กลุ่ม 2 </button> <button onclick="showTab('group3')" id="tab-group3" class="tab-btn px-4 py-2 md:px-6 md:py-3 rounded-xl font-semibold transition-all duration-300 bg-white shadow-md hover:shadow-lg text-gray-700 text-sm md:text-base"> 📙 กลุ่ม 3 </button> <button onclick="showTab('quiz')" id="tab-quiz" class="tab-btn px-4 py-2 md:px-6 md:py-3 rounded-xl font-semibold transition-all duration-300 bg-white shadow-md hover:shadow-lg text-gray-700 text-sm md:text-base"> 🎯 แบบทดสอบ </button>
    </div>
   </nav>
   <main class="max-w-6xl mx-auto px-4 py-6">
    <section id="content-group1" class="content-section hidden">
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
    <section id="content-group2" class="content-section hidden">
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
    <section id="content-group3" class="content-section hidden">
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
    <section id="content-quiz" class="content-section hidden">
     <div class="bg-white rounded-2xl shadow-xl p-6 md:p-8 fade-in">
      <div class="flex items-center justify-between mb-6 flex-wrap gap-4">
       <div class="flex items-center gap-3"><span class="text-4xl">🎯</span>
        <div>
         <h2 class="text-2xl font-bold text-purple-700">แบบทดสอบ</h2>
         <p class="text-gray-600">ทดสอบความรู้การผัน て形</p>
        </div>
       </div><button onclick="startQuiz()" id="start-quiz-btn" class="px-6 py-3 bg-gradient-to-r from-pink-500 to-purple-500 text-white rounded-xl font-semibold hover:shadow-lg transition-all duration-300 hover:scale-105"> 🚀 เริ่มทำแบบทดสอบ </button>
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
      <div id="quiz-area" class="hidden">
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
       <div class="flex justify-center gap-4 flex-wrap"><button onclick="checkAnswer()" class="px-8 py-3 bg-gradient-to-r from-green-400 to-teal-400 text-white rounded-xl font-semibold hover:shadow-lg transition-all duration-300 hover:scale-105"> ✅ ตรวจคำตอบ </button> <button onclick="showHint()" id="hint-btn" class="px-8 py-3 bg-gradient-to-r from-yellow-400 to-orange-400 text-white rounded-xl font-semibold hover:shadow-lg transition-all duration-300 hover:scale-105"> 💡 ดูคำใบ้ </button> <button onclick="skipQuestion()" class="px-8 py-3 bg-gray-400 text-white rounded-xl font-semibold hover:shadow-lg transition-all duration-300 hover:scale-105 hover:bg-gray-500"> ⏭️ ข้ามข้อ </button>
       </div>
       <div id="hint-area" class="hidden mt-4 bg-yellow-50 border border-yellow-300 rounded-xl p-4 text-center">
        <p class="text-yellow-800" id="hint-text"></p>
       </div>
       <div id="feedback-area" class="hidden mt-6"></div>
      </div>
      <div id="results-area" class="hidden">
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
        <div id="mistakes-section" class="hidden mb-6">
         <h4 class="font-bold text-gray-800 mb-3 text-left">📝 ทบทวนข้อที่ผิด</h4>
         <div id="mistakes-list" class="space-y-3"></div>
        </div>
        <div class="flex justify-center gap-4 flex-wrap"><button onclick="startQuiz()" class="px-8 py-3 bg-gradient-to-r from-pink-500 to-purple-500 text-white rounded-xl font-semibold hover:shadow-lg transition-all duration-300 hover:scale-105"> 🔁 ทำแบบทดสอบใหม่ </button> <button onclick="showTab('group1')" class="px-8 py-3 bg-gradient-to-r from-blue-500 to-blue-600 text-white rounded-xl font-semibold hover:shadow-lg transition-all duration-300 hover:scale-105"> 📚 กลับไปทบทวน </button> <button onclick="resetToHome()" class="px-8 py-3 bg-gradient-to-r from-gray-500 to-gray-600 text-white rounded-xl font-semibold hover:shadow-lg transition-all duration-300 hover:scale-105"> 🏠 กลับหน้าแรก </button>
        </div>
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
      subtitle: 'เรียนรู้การผันคำกริยาภาษาญี่ปุ่นอย่างสนุกสนาน!',
      background_color: '#fce7f3',
      surface_color: '#ffffff',
      text_color: '#374151',
      primary_action_color: '#ff6b9d',
      secondary_action_color: '#fbbf24'
    };

    let config = { ...defaultConfig };

    const group1Verbs = [
      { dict: '書く', reading: 'かく', te: '書いて', teReading: 'かいて', meaning: 'เขียน', rule: 'く→いて' },
      { dict: '聞く', reading: 'きく', te: '聞いて', teReading: 'きいて', meaning: 'ฟัง', rule: 'く→いて' },
      { dict: '行く', reading: 'いく', te: '行って', teReading: 'いって', meaning: 'ไป', rule: 'ยกเว้น! く→って' },
      { dict: '泳ぐ', reading: 'およぐ', te: '泳いで', teReading: 'およいで', meaning: 'ว่ายน้ำ', rule: 'ぐ→いで' },
      { dict: '話す', reading: 'はなす', te: '話して', teReading: 'はなして', meaning: 'พูด', rule: 'す→して' },
      { dict: '待つ', reading: 'まつ', te: '待って', teReading: 'まっ���', meaning: 'รอ', rule: 'つ→って' },
      { dict: '持つ', reading: 'もつ', te: '持って', teReading: 'もって', meaning: 'ถือ', rule: 'つ→って' },
      { dict: '死ぬ', reading: 'しぬ', te: '死んで', teReading: 'しんで', meaning: 'ตาย', rule: 'ぬ→んで' },
      { dict: '読む', reading: 'よむ', te: '読んで', teReading: 'よんで', meaning: 'อ่าน', rule: 'む→んで' },
      { dict: '飲む', reading: 'のむ', te: '飲んで', teReading: 'のんで', meaning: 'ดื่ม', rule: 'む→んで' },
      { dict: '遊ぶ', reading: 'あそぶ', te: '遊んで', teReading: 'あそんで', meaning: 'เล่น', rule: 'ぶ→んで' },
      { dict: '呼ぶ', reading: 'よぶ', te: '呼んで', teReading: 'よんで', meaning: 'เรียก', rule: 'ぶ→んで' },
      { dict: '買う', reading: 'かう', te: '買って', teReading: '��って', meaning: 'ซื้อ', rule: 'う→って' },
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
      { dict: '見る', reading: 'みる', te: '見て', teReading: 'みて', meaning: 'ด��', rule: 'る→て' },
      { dict: '寝る', reading: 'ねる', te: '寝て', teReading: 'ねて', meaning: 'นอน', rule: 'る→て' },
      { dict: '起きる', reading: 'おきる', te: '起きて', teReading: 'おきて', meaning: 'ตื่น', rule: 'る→て' },
      { dict: '開ける', reading: 'あける', te: '開けて', teReading: 'あけて', meaning: 'เปิด', rule: 'る→て' },
      { dict: '閉める', reading: 'しめる', te: '閉めて', teReading: 'しめて', meaning: 'ปิด', rule: 'る→て' },
      { dict: '教える', reading: 'お��える', te: '教えて', teReading: 'おしえて', meaning: 'สอ��', rule: 'る→て' },
      { dict: '覚える', reading: 'おぼえる', te: '覚えて', teReading: 'おぼえて', meaning: 'จำ', rule: 'る→て' },
      { dict: '忘れる', reading: 'わすれる', te: '忘れて', teReading: 'わすれて', meaning: 'ลืม', rule: 'る→て' },
      { dict: '着る', reading: 'きる', te: '着て', teReading: 'きて', meaning: 'สวม', rule: 'る→て' },
      { dict: '出る', reading: 'でる', te: '出て', teReading: 'でて', meaning: 'ออก', rule: 'る→て' },
      { dict: 'いる', reading: 'いる', te: 'いて', teReading: 'いて', meaning: 'อยู่(สิ่งมีชีวิต)', rule: 'る→て' },
      { dict: '浴びる', reading: 'あびる', te: '浴びて', teReading: 'あびて', meaning: 'อาบ', rule: 'る→て' },
      { dict: '借りる', reading: 'かりる', te: '借りて', teReading: 'かりて', meaning: 'ยื��', rule: 'る→て' },
      { dict: '降りる', reading: 'おりる', te: '降りて', teReading: 'おりて', meaning: 'ลง', rule: 'る→て' }
    ];

    const group3Verbs = [
      { dict: 'する', reading: 'する', te: 'して', teReading: 'して', meaning: 'ทำ', rule: 'する→して' },
      { dict: '来る', reading: 'くる', te: '来て', teReading: 'きて', meaning: 'มา', rule: '来る→来て' },
      { dict: '勉強する', reading: 'べんきょうする', te: '勉強して', teReading: 'べんきょうして', meaning: 'เรียน', rule: 'する→して' },
      { dict: '散歩する', reading: 'さんぽする', te: '散歩して', teReading: 'さんぽして', meaning: 'เดินเล่น', rule: 'する→して' },
      { dict: '買い物する', reading: 'かいものする', te: '買い物して', teReading: 'かいものして', meaning: 'ช็อปปิ้ง', rule: 'する→して' },
      { dict: '掃除する', reading: 'そう���する', te: '掃除して', teReading: 'そうじして', meaning: 'ท���ความสะอาด', rule: 'する→して' },
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
      document.getElementById('quiz-answer').addEventListener('keypress', function(e) {
        if (e.key === 'Enter') checkAnswer();
      });
    }

    function renderVocabularyCards() {
      document.getElementById('group1-cards').innerHTML = group1Verbs.map(v => createVerbCard({...v, group: 1}, 'indigo')).join('');
      document.getElementById('group2-cards').innerHTML = group2Verbs.map(v => createVerbCard({...v, group: 2}, 'emerald')).join('');
      document.getElementById('group3-cards').innerHTML = group3Verbs.map(v => createVerbCard({...v, group: 3}, 'orange')).join('');
    }

    function createVerbCard(verb, color) {
      const cardId = 'card-' + Math.random().toString(36).substr(2, 9);
      return `
        <div class="flashcard" id="${cardId}" onclick="flipCard('${cardId}')">
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
                <button onclick="event.stopPropagation(); speak('${verb.teReading}')" class="text-2xl hover:scale-125 transition-transform duration-200" title="ฟังเสียง">
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
      document.querySelectorAll('.content-section').forEach(s => s.classList.add('hidden'));
      document.querySelectorAll('.tab-btn').forEach(t => t.classList.remove('tab-active'));
      document.getElementById('content-' + tabId).classList.remove('hidden');
      document.getElementById('tab-' + tabId).classList.add('tab-active');
    }

    function startQuiz() {
      const count = parseInt(document.getElementById('quiz-count').value);
      const group = document.getElementById('quiz-group').value;
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
      document.getElementById('quiz-settings').classList.add('hidden');
      document.getElementById('start-quiz-btn').classList.add('hidden');
      document.getElementById('quiz-area').classList.remove('hidden');
      document.getElementById('results-area').classList.add('hidden');
      showQuestion();
    }

    function showQuestion() {
      const q = quizState.questions[quizState.currentIndex];
      document.getElementById('quiz-group-label').textContent = 'กลุ่ม ' + q.group;
      document.getElementById('quiz-word').textContent = q.dict;
      document.getElementById('quiz-reading').textContent = '（' + q.reading + '）';
      document.getElementById('quiz-meaning').textContent = q.meaning;
      document.getElementById('quiz-answer').value = '';
      document.getElementById('quiz-answer').focus();
      document.getElementById('hint-area').classList.add('hidden');
      document.getElementById('feedback-area').classList.add('hidden');
      document.getElementById('hint-btn').disabled = false;
      updateProgress();
    }

    function updateProgress() {
      const total = quizState.questions.length;
      const current = quizState.currentIndex + 1;
      const progress = (quizState.currentIndex / total) * 100;
      document.getElementById('quiz-progress-text').textContent = 'ข้อ ' + current + ' / ' + total;
      document.getElementById('quiz-score-text').textContent = 'คะแนน: ' + quizState.score;
      document.getElementById('quiz-progress-bar').style.width = progress + '%';
    }

    function showHint() {
      const q = quizState.questions[quizState.currentIndex];
      document.getElementById('hint-text').innerHTML = 'กฎการผัน: ' + q.rule + '<br>คำตอบขึ้นต้นด้วย: <span class="japanese font-bold">' + q.te.charAt(0) + '</span>';
      document.getElementById('hint-area').classList.remove('hidden');
      document.getElementById('hint-btn').disabled = true;
    }

    function checkAnswer() {
      if (!quizState.isActive) return;
      const userAnswer = document.getElementById('quiz-answer').value.trim();
      const q = quizState.questions[quizState.currentIndex];
      const correctAnswers = [q.te, q.teReading];
      const feedbackArea = document.getElementById('feedback-area');
      feedbackArea.classList.remove('hidden');
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
      document.getElementById('feedback-area').classList.remove('hidden');
      document.getElementById('feedback-area').innerHTML = '<div class="bg-gray-100 border border-gray-400 rounded-xl p-4 text-center"><p class="text-xl mb-2">⏭️ ข้ามข้อนี้</p><p class="text-gray-700">คำตอบคือ: <span class="font-bold japanese text-xl">' + q.te + '</span></p></div>';
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
      document.getElementById('quiz-area').classList.add('hidden');
      document.getElementById('results-area').classList.remove('hidden');
      const total = quizState.questions.length;
      const score = quizState.score;
      const percentage = Math.round((score / total) * 100);
      const wrong = total - score;
      document.getElementById('final-score').textContent = score + ' / ' + total;
      document.getElementById('score-percentage').textContent = percentage + '%';
      document.getElementById('correct-count').textContent = score;
      document.getElementById('wrong-count').textContent = wrong - quizState.skipped;
      document.getElementById('skip-count').textContent = quizState.skipped;
      const resultEmoji = document.getElementById('result-emoji');
      const resultTitle = document.getElementById('result-title');
      const resultMessage = document.getElementById('result-message');
      if (percentage >= 90) {
        resultEmoji.textContent = '🏆';
        resultTitle.textContent = 'ยอดเยี่ยมมาก!';
        resultMessage.textContent = 'คุณเก่งมากๆ เลย! เป็นผู้ชำนาญ て形 แล้ว!';
      } else if (percentage >= 70) {
        resultEmoji.textContent = '🎉';
        resultTitle.textContent = 'ดีมาก!';
        resultMessage.textContent = 'คุณทำได้ดีมาก! ฝึกฝนอีกนิดจะเก่งขึ้นอีก!';
      } else if (percentage >= 50) {
        resultEmoji.textContent = '👍';
        resultTitle.textContent = 'พอใช้ได้!';
        resultMessage.textContent = 'กำลังพัฒนาได้ดี ลองทบทวนกฎและฝึกเพิ่มนะ!';
      } else {
        resultEmoji.textContent = '💪';
        resultTitle.textContent = 'สู้ๆ นะ!';
        resultMessage.textContent = 'อย่าท้อนะ! ลองกลับไปดูกฎการผันแล้วฝึกใหม่อีกครั้ง!';
      }
      generateAdvice(percentage);
      if (quizState.wrongAnswers.length > 0) {
        document.getElementById('mistakes-section').classList.remove('hidden');
        document.getElementById('mistakes-list').innerHTML = quizState.wrongAnswers.map(item => 
          '<div class="bg-red-50 border border-red-200 rounded-lg p-3 text-left"><div class="flex justify-between items-start"><div><span class="font-bold japanese">' + item.question.dict + '</span><span class="text-gray-500 text-sm">(' + item.question.reading + ')</span></div><span class="text-xs bg-gray-200 px-2 py-1 rounded">กลุ่ม ' + item.question.group + '</span></div><p class="text-sm text-gray-600 mt-1">คำตอบของคุณ: <span class="text-red-600">' + item.userAnswer + '</span></p><p class="text-sm text-gray-600">คำตอบที่ถูก: <span class="text-green-600 font-bold japanese">' + item.question.te + '</span> (' + item.question.teReading + ')</p><p class="text-xs text-gray-500 mt-1">กฎ: ' + item.question.rule + '</p></div>'
        ).join('');
      } else {
        document.getElementById('mistakes-section').classList.add('hidden');
      }
    }

    function resetToHome() {
      document.getElementById('quiz-settings').classList.remove('hidden');
      document.getElementById('start-quiz-btn').classList.remove('hidden');
      document.getElementById('quiz-area').classList.add('hidden');
      document.getElementById('results-area').classList.add('hidden');
      showTab('group1');
    }

    function generateAdvice(percentage) {
      const wrongGroups = {1: 0, 2: 0, 3: 0};
      quizState.wrongAnswers.forEach(item => wrongGroups[item.question.group]++);
      let advice = [];
      if (wrongGroups[1] > 0) {
        advice.push('<div class="bg-indigo-50 rounded-lg p-3 mb-2"><p class="font-semibold text-indigo-800">📚 กลุ่ม 1 (' + wrongGroups[1] + ' ข้อ)</p><p class="text-sm text-gray-700">ทบทวนกฎ: う・つ・る→って, む・ぬ・ぶ→んで, く→いて, ぐ→いで, す→して</p><p class="text-sm text-gray-600">💡 จำง่ายๆ: "อิ-ชิ-ตะ-นะ" (いて・して・って・んで)</p></div>');
      }
      if (wrongGroups[2] > 0) {
        advice.push('<div class="bg-emerald-50 rounded-lg p-3 mb-2"><p class="font-semibold text-emerald-800">📗 กลุ่ม 2 (' + wrongGroups[2] + ' ข้อ)</p><p class="text-sm text-gray-700">กฎง่ายที่สุด: แค่ตัด る แล้วเติม て</p><p class="text-sm text-gray-600">⚠️ ระวัง! บางค��ที่ลงท้าย いる/える อาจเป็นกลุ่ม 1 ก็ได���</p></div>');
      }
      if (wrongGroups[3] > 0) {
        advice.push('<div class="bg-orange-50 rounded-lg p-3 mb-2"><p class="font-semibold text-orange-800">📙 กลุ่ม 3 (' + wrongGroups[3] + ' ข้อ)</p><p class="text-sm text-gray-700">จำแค่ 2 คำ: する→して และ 来る→来て</p><p class="text-sm text-gray-600">💡 คำที่ลงท้าย する ทั้งหมดผันเป็น して</p></div>');
      }
      if (percentage >= 90) {
        advice.push('<div class="bg-green-50 rounded-lg p-3"><p class="font-semibold text-green-800">⭐ คำแนะนำระดับสูง</p><p class="text-sm text-gray-700">คุณเก่งมากแล้ว! ลองฝึกใช้ て形 ในประโยคจริง เช่น:</p><p class="text-sm japanese mt-1">• ～てください (กรุณา...)</p><p class="text-sm japanese">• ～ている (กำลัง...)</p><p class="text-sm japanese">• ～てもいい (ขอ...ได้ไหม)</p></div>');
      } else if (percentage < 50) {
        advice.push('<div class="bg-yellow-50 rounded-lg p-3"><p class="font-semibold text-yellow-800">🚀 เริ่มต้นใหม่</p><p class="text-sm text-gray-700">แนะนำให้:</p><p class="text-sm">1. ทบทวนกฎแต่ละกลุ่มอีกครั้ง</p><p class="text-sm">2. ท่อ���จำคำกริยาพร้อมรูป て形</p><p class="text-sm">3. ฝึกทำแบบทดสอบทีละกลุ่ม</p></div>');
      }
      document.getElementById('advice-content').innerHTML = advice.join('');
    }

    async function onConfigChange(newConfig) {
      document.getElementById('main-title').textContent = newConfig.main_title || defaultConfig.main_title;
      document.getElementById('subtitle').textContent = newConfig.subtitle || defaultConfig.subtitle;
      const app = document.getElementById('app');
      app.style.background = 'linear-gradient(135deg, ' + (newConfig.background_color || defaultConfig.background_color) + ' 0%, #e9d5ff 50%, #dbeafe 100%)';
    }

    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities: (cfg) => ({
          recolorables: [
            { get: () => cfg.background_color || defaultConfig.background_color, set: (v) => { cfg.background_color = v; window.elementSdk.setConfig({ background_color: v }); }},
            { get: () => cfg.surface_color || defaultConfig.surface_color, set: (v) => { cfg.surface_color = v; window.elementSdk.setConfig({ surface_color: v }); }},
            { get: () => cfg.text_color || defaultConfig.text_color, set: (v) => { cfg.text_color = v; window.elementSdk.setConfig({ text_color: v }); }},
            { get: () => cfg.primary_action_color || defaultConfig.primary_action_color, set: (v) => { cfg.primary_action_color = v; window.elementSdk.setConfig({ primary_action_color: v }); }},
            { get: () => cfg.secondary_action_color || defaultConfig.secondary_action_color, set: (v) => { cfg.secondary_action_color = v; window.elementSdk.setConfig({ secondary_action_color: v }); }}
          ],
          borderables: [],
          fontEditable: undefined,
          fontSizeable: undefined
        }),
        mapToEditPanelValues: (cfg) => new Map([
          ['main_title', cfg.main_title || defaultConfig.main_title],
          ['subtitle', cfg.subtitle || defaultConfig.subtitle]
        ])
      });
    }

    init();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9bc5658b44032ca3',t:'MTc2ODE0NDgxMS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
