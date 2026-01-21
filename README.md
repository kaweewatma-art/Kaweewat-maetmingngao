<html lang="th" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>คณิตศาสตร์การเงิน ป.5</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;600;700&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
      font-family: 'Kanit', sans-serif;
    }
    .coin {
      animation: bounce 2s infinite;
    }
    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }
    .sparkle {
      animation: sparkle 1.5s infinite;
    }
    @keyframes sparkle {
      0%, 100% { opacity: 1; transform: scale(1); }
      50% { opacity: 0.5; transform: scale(1.2); }
    }
    .slide-in {
      animation: slideIn 0.5s ease-out;
    }
    @keyframes slideIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    .correct-answer {
      animation: correctPulse 0.5s ease-out;
    }
    @keyframes correctPulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.1); }
      100% { transform: scale(1); }
    }
    .wrong-answer {
      animation: shake 0.5s ease-out;
    }
    @keyframes shake {
      0%, 100% { transform: translateX(0); }
      25% { transform: translateX(-10px); }
      75% { transform: translateX(10px); }
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full">
  <div id="app-container" class="h-full overflow-auto" style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);"><!-- หน้าหลัก -->
   <div id="home-screen" class="min-h-full p-4 md:p-8">
    <div class="max-w-4xl mx-auto"><!-- Header -->
     <div class="text-center mb-8 slide-in">
      <div class="inline-block mb-4">
       <svg class="w-20 h-20 coin" viewbox="0 0 100 100"><circle cx="50" cy="50" r="45" fill="#FFD700" stroke="#DAA520" stroke-width="4" /> <circle cx="50" cy="50" r="35" fill="none" stroke="#DAA520" stroke-width="2" /> <text x="50" y="58" text-anchor="middle" font-size="28" font-weight="bold" fill="#8B4513">
         ฿
        </text>
       </svg>
      </div>
      <h1 id="main-title" class="text-3xl md:text-4xl font-bold text-white mb-2 drop-shadow-lg">คณิตศาสตร์การเงิน ป.5</h1>
      <p id="welcome-text" class="text-lg text-purple-100">เรียนรู้เรื่องเงินอย่างสนุก! 💰</p>
     </div><!-- เมนูห��ัก -->
     <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-8"><!-- บทเรียน --> <button onclick="showLessons()" class="bg-white rounded-2xl p-6 shadow-xl hover:shadow-2xl transform hover:scale-105 transition-all duration-300 text-left">
       <div class="flex items-center gap-4">
        <div class="w-16 h-16 bg-gradient-to-br from-green-400 to-green-600 rounded-xl flex items-center justify-center text-3xl">
         📚
        </div>
        <div>
         <h3 class="text-xl font-bold text-gray-800">บทเรียน</h3>
         <p class="text-gray-500">เรียนรู้เรื่องเงินและการคำนวณ</p>
        </div>
       </div></button> <!-- แบบฝึกหัด --> <button onclick="showPractice()" class="bg-white rounded-2xl p-6 shadow-xl hover:shadow-2xl transform hover:scale-105 transition-all duration-300 text-left">
       <div class="flex items-center gap-4">
        <div class="w-16 h-16 bg-gradient-to-br from-blue-400 to-blue-600 rounded-xl flex items-center justify-center text-3xl">
         ✏️
        </div>
        <div>
         <h3 class="text-xl font-bold text-gray-800">แบบฝึกหัด</h3>
         <p class="text-gray-500">ฝึกคำนวณเงินหลายรูปแบบ</p>
        </div>
       </div></button> <!-- เกมจับคู่ --> <button onclick="showGame()" class="bg-white rounded-2xl p-6 shadow-xl hover:shadow-2xl transform hover:scale-105 transition-all duration-300 text-left">
       <div class="flex items-center gap-4">
        <div class="w-16 h-16 bg-gradient-to-br from-orange-400 to-red-500 rounded-xl flex items-center justify-center text-3xl">
         🎮
        </div>
        <div>
         <h3 class="text-xl font-bold text-gray-800">เกมนับเงิน</h3>
         <p class="text-gray-500">สนุกกับการนับเหรียญและธนบัตร</p>
        </div>
       </div></button> <!-- ร้านค้าจำลอง --> <button onclick="showShop()" class="bg-white rounded-2xl p-6 shadow-xl hover:shadow-2xl transform hover:scale-105 transition-all duration-300 text-left">
       <div class="flex items-center gap-4">
        <div class="w-16 h-16 bg-gradient-to-br from-pink-400 to-purple-500 rounded-xl flex items-center justify-center text-3xl">
         🛒
        </div>
        <div>
         <h3 class="text-xl font-bold text-gray-800">ร้านค้าจำลอง</h3>
         <p class="text-gray-500">ฝึกซื้อของและทอนเงิน</p>
        </div>
       </div></button>
     </div><!-- คะแนน -->
     <div class="bg-white/20 backdrop-blur rounded-2xl p-6 text-center mb-4">
      <h3 class="text-white font-bold mb-2">🏆 คะแนนรวม</h3>
      <p id="total-score" class="text-4xl font-bold text-yellow-300">0</p>
      <p class="text-purple-100 text-sm">คะแนน</p>
     </div><!-- ผู้สร้าง -->
     <div class="bg-white/10 backdrop-blur rounded-2xl p-4 text-center">
      <p class="text-purple-100 text-sm mb-1">👨‍🎓 ผู้สร้าง</p>
      <p id="creator-name" class="text-white font-bold">เด็กชายกวีวัธน์ แมดมิ่งเหง้า</p>
      <p class="text-purple-200 text-sm">ชั้นประถมศึกษาปีที่ 5</p>
     </div>
    </div>
   </div><!-- หน้าบทเรียน -->
   <div id="lessons-screen" class="min-h-full p-4 md:p-8 hidden">
    <div class="max-w-4xl mx-auto"><button onclick="goHome()" class="mb-6 bg-white/20 hover:bg-white/30 text-white px-4 py-2 rounded-full flex items-center gap-2 transition-all"> ← กลับหน้าหลัก </button>
     <h2 class="text-2xl md:text-3xl font-bold text-white mb-6 text-center">📚 บทเรียน</h2>
     <div class="space-y-4"><!-- บทที่ 1 -->
      <div class="bg-white rounded-2xl p-6 shadow-xl slide-in">
       <h3 class="text-xl font-bold text-gray-800 mb-4">💵 บทที่ 1: รู้จักธนบัตรและเหรียญไทย</h3>
       <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-4">
        <div class="bg-green-100 rounded-xl p-3 text-center">
         <div class="text-3xl mb-1">
          🟤
         </div>
         <p class="font-bold text-green-700">25 สตางค์</p>
        </div>
        <div class="bg-green-100 rounded-xl p-3 text-center">
         <div class="text-3xl mb-1">
          ⚪
         </div>
         <p class="font-bold text-green-700">50 สตางค์</p>
        </div>
        <div class="bg-yellow-100 rounded-xl p-3 text-center">
         <div class="text-3xl mb-1">
          🪙
         </div>
         <p class="font-bold text-yellow-700">1 บาท</p>
        </div>
        <div class="bg-yellow-100 rounded-xl p-3 text-center">
         <div class="text-3xl mb-1">
          🥇
         </div>
         <p class="font-bold text-yellow-700">2 บาท</p>
        </div>
        <div class="bg-blue-100 rounded-xl p-3 text-center">
         <div class="text-3xl mb-1">
          🔵
         </div>
         <p class="font-bold text-blue-700">5 บาท</p>
        </div>
        <div class="bg-purple-100 rounded-xl p-3 text-center">
         <div class="text-3xl mb-1">
          🟣
         </div>
         <p class="font-bold text-purple-700">10 บาท</p>
        </div>
       </div>
       <div class="grid grid-cols-2 md:grid-cols-3 gap-4">
        <div class="bg-green-200 rounded-xl p-3 text-center">
         <p class="text-2xl mb-1">💵</p>
         <p class="font-bold text-green-800">20 บาท</p>
        </div>
        <div class="bg-red-200 rounded-xl p-3 text-center">
         <p class="text-2xl mb-1">💴</p>
         <p class="font-bold text-red-800">100 บาท</p>
        </div>
        <div class="bg-purple-200 rounded-xl p-3 text-center">
         <p class="text-2xl mb-1">💶</p>
         <p class="font-bold text-purple-800">500 บาท</p>
        </div>
        <div class="bg-gray-200 rounded-xl p-3 text-center">
         <p class="text-2xl mb-1">💷</p>
         <p class="font-bold text-gray-800">1,000 บาท</p>
        </div>
       </div>
      </div><!-- บทที่ 2 -->
      <div class="bg-white rounded-2xl p-6 shadow-xl slide-in" style="animation-delay: 0.1s;">
       <h3 class="text-xl font-bold text-gray-800 mb-4">🔢 บทที่ 2: การแลกเงิน</h3>
       <div class="bg-blue-50 rounded-xl p-4 space-y-2">
        <p class="text-gray-700">• 100 สตางค์ = <strong>1 บาท</strong></p>
        <p class="text-gray-700">• 10 บาท = <strong>1,000 สตางค์</strong></p>
        <p class="text-gray-700">• เหรียญ 5 บาท × 20 = <strong>100 บาท</strong></p>
        <p class="text-gray-700">• เหรียญ 10 บาท × 10 = <strong>100 บาท</strong></p>
        <p class="text-gray-700">• ธนบัตร 20 บาท × 5 = <strong>100 บาท</strong></p>
       </div>
      </div><!-- บทที่ 3 -->
      <div class="bg-white rounded-2xl p-6 shadow-xl slide-in" style="animation-delay: 0.2s;">
       <h3 class="text-xl font-bold text-gray-800 mb-4">🧮 บทที่ 3: การคำนวณเงินทอน</h3>
       <div class="bg-yellow-50 rounded-xl p-4">
        <p class="text-gray-700 mb-3"><strong>สูตร:</strong> เงินทอน = เงินที่จ่าย - ราคาสินค้า</p>
        <div class="bg-white rounded-lg p-3 border-2 border-yellow-300">
         <p class="text-gray-600 mb-1">ตัวอย่าง:</p>
         <p class="text-gray-800">���ื้อขนม 35 บาท จ่าย 50 บาท</p>
         <p class="text-green-600 font-bold">เงินทอน = 50 - 35 = 15 บาท</p>
        </div>
       </div>
      </div>
     </div>
    </div>
   </div><!-- หน้าแบบฝึกหัด -->
   <div id="practice-screen" class="min-h-full p-4 md:p-8 hidden">
    <div class="max-w-2xl mx-auto"><button onclick="goHome()" class="mb-6 bg-white/20 hover:bg-white/30 text-white px-4 py-2 rounded-full flex items-center gap-2 transition-all"> ← กลับหน้าหลัก </button>
     <div class="bg-white rounded-2xl p-6 shadow-xl">
      <div class="flex justify-between items-center mb-6">
       <h2 class="text-xl font-bold text-gray-800">✏️ แบบฝึกหัด</h2>
       <div class="bg-purple-100 px-4 py-2 rounded-full"><span class="text-purple-700 font-bold">ข้อ <span id="current-question">1</span>/10</span>
       </div>
      </div>
      <div id="practice-question" class="text-center mb-6">
       <p class="text-lg text-gray-600 mb-4" id="question-text">กำลังโหลดคำถาม...</p>
       <div class="text-5xl mb-4" id="question-emoji">
        💰
       </div>
      </div>
      <div id="practice-options" class="grid grid-cols-2 gap-3 mb-6"><!-- ตัวเลือกจะถูกสร้างโดย JavaScript -->
      </div>
      <div id="practice-feedback" class="text-center hidden">
       <p class="text-lg font-bold" id="feedback-text"></p>
      </div>
      <div class="flex justify-between items-center mt-6 pt-4 border-t">
       <div class="text-gray-600">
        คะแนน: <span id="practice-score" class="font-bold text-purple-600">0</span>
       </div><button onclick="nextQuestion()" id="next-btn" class="bg-purple-500 hover:bg-purple-600 text-white px-6 py-2 rounded-full font-bold transition-all hidden"> ข้อถัดไป → </button>
      </div>
     </div>
    </div>
   </div><!-- หน้าเกม -->
   <div id="game-screen" class="min-h-full p-4 md:p-8 hidden">
    <div class="max-w-2xl mx-auto"><button onclick="goHome()" class="mb-6 bg-white/20 hover:bg-white/30 text-white px-4 py-2 rounded-full flex items-center gap-2 transition-all"> ← กลับหน้าหลัก </button>
     <div class="bg-white rounded-2xl p-6 shadow-xl">
      <h2 class="text-xl font-bold text-gray-800 text-center mb-6">🎮 เกมนับเงิน</h2>
      <div class="bg-gradient-to-r from-yellow-100 to-orange-100 rounded-xl p-6 mb-6">
       <p class="text-center text-gray-700 mb-4">นับเงินรวมจากเหรียญและธนบัตรด้านล่���ง</p>
       <div id="game-money" class="flex flex-wrap justify-center gap-2 min-h-20"><!-- เงินจะถูกสร้างโดย JavaScript -->
       </div>
      </div>
      <div class="text-center mb-6">
       <p class="text-gray-600 mb-2">จำนวนเงินรวมเท่าไร?</p>
       <div class="flex justify-center items-center gap-2"><input type="number" id="game-answer" class="w-32 text-center text-2xl font-bold border-2 border-purple-300 rounded-xl px-4 py-2 focus:border-purple-500 focus:outline-none" placeholder="0"> <span class="text-xl font-bold text-gray-700">บาท</span>
       </div>
      </div>
      <div class="flex justify-center gap-4"><button onclick="checkGameAnswer()" class="bg-green-500 hover:bg-green-600 text-white px-8 py-3 rounded-full font-bold transition-all"> ✓ ตรวจคำตอบ </button> <button onclick="newGameRound()" class="bg-blue-500 hover:bg-blue-600 text-white px-8 py-3 rounded-full font-bold transition-all"> 🔄 ข้อใหม่ </button>
      </div>
      <div id="game-feedback" class="text-center mt-4 hidden">
       <p class="text-lg font-bold" id="game-feedback-text"></p>
      </div>
      <div class="text-center mt-6 pt-4 border-t">
       <p class="text-gray-600">คะแนนเกม: <span id="game-score" class="font-bold text-orange-600">0</span></p>
      </div>
     </div>
    </div>
   </div><!-- หน้าร้านค้า -->
   <div id="shop-screen" class="min-h-full p-4 md:p-8 hidden">
    <div class="max-w-4xl mx-auto"><button onclick="goHome()" class="mb-6 bg-white/20 hover:bg-white/30 text-white px-4 py-2 rounded-full flex items-center gap-2 transition-all"> ← กลั���หน้าหลัก </button>
     <div class="bg-white rounded-2xl p-6 shadow-xl mb-6">
      <h2 class="text-xl font-bold text-gray-800 text-center mb-2">🛒 ร้านค้าจำลอง</h2>
      <p class="text-center text-gray-500 mb-6">เลือกซื้อสินค้าและฝึกคำนวณเงินทอน</p><!-- กระเป๋าเงิน -->
      <div class="bg-gradient-to-r from-green-400 to-emerald-500 rounded-xl p-4 mb-6">
       <div class="flex justify-between items-center text-white"><span class="font-bold">💰 เงินในกระเป๋า:</span> <span id="wallet-amount" class="text-2xl font-bold">500 บาท</span>
       </div>
      </div><!-- สินค้า -->
      <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-6">
       <div class="shop-item bg-pink-50 rounded-xl p-4 text-center cursor-pointer hover:bg-pink-100 transition-all" onclick="addToCart('ขนมปัง', 25)">
        <div class="text-4xl mb-2">
         🍞
        </div>
        <p class="font-bold text-gray-800">ขนมปัง</p>
        <p class="text-pink-600 font-bold">25 บาท</p>
       </div>
       <div class="shop-item bg-yellow-50 rounded-xl p-4 text-center cursor-pointer hover:bg-yellow-100 transition-all" onclick="addToCart('นม', 15)">
        <div class="text-4xl mb-2">
         🥛
        </div>
        <p class="font-bold text-gray-800">นม</p>
        <p class="text-yellow-600 font-bold">15 บาท</p>
       </div>
       <div class="shop-item bg-red-50 rounded-xl p-4 text-center cursor-pointer hover:bg-red-100 transition-all" onclick="addToCart('แอปเปิ้ล', 30)">
        <div class="text-4xl mb-2">
         🍎
        </div>
        <p class="font-bold text-gray-800">แอปเปิ้ล</p>
        <p class="text-red-600 font-bold">30 บาท</p>
       </div>
       <div class="shop-item bg-blue-50 rounded-xl p-4 text-center cursor-pointer hover:bg-blue-100 transition-all" onclick="addToCart('น้ำ', 10)">
        <div class="text-4xl mb-2">
         💧
        </div>
        <p class="font-bold text-gray-800">น้ำ</p>
        <p class="text-blue-600 font-bold">10 บาท</p>
       </div>
       <div class="shop-item bg-orange-50 rounded-xl p-4 text-center cursor-pointer hover:bg-orange-100 transition-all" onclick="addToCart('ส้ม', 20)">
        <div class="text-4xl mb-2">
         🍊
        </div>
        <p class="font-bold text-gray-800">ส้ม</p>
        <p class="text-orange-600 font-bold">20 บาท</p>
       </div>
       <div class="shop-item bg-purple-50 rounded-xl p-4 text-center cursor-pointer hover:bg-purple-100 transition-all" onclick="addToCart('องุ่น', 45)">
        <div class="text-4xl mb-2">
         🍇
        </div>
        <p class="font-bold text-gray-800">องุ่น</p>
        <p class="text-purple-600 font-bold">45 บาท</p>
       </div>
       <div class="shop-item bg-green-50 rounded-xl p-4 text-center cursor-pointer hover:bg-green-100 transition-all" onclick="addToCart('สลัด', 35)">
        <div class="text-4xl mb-2">
         🥗
        </div>
        <p class="font-bold text-gray-800">สลัด</p>
        <p class="text-green-600 font-bold">35 บาท</p>
       </div>
       <div class="shop-item bg-amber-50 rounded-xl p-4 text-center cursor-pointer hover:bg-amber-100 transition-all" onclick="addToCart('ขนม', 12)">
        <div class="text-4xl mb-2">
         🍪
        </div>
        <p class="font-bold text-gray-800">ขนม</p>
        <p class="text-amber-600 font-bold">12 บาท</p>
       </div>
      </div><!-- ตะกร้า -->
      <div class="bg-gray-100 rounded-xl p-4 mb-4">
       <h3 class="font-bold text-gray-800 mb-3">🧺 ตะกร้าสินค้า</h3>
       <div id="cart-items" class="space-y-2 mb-4 min-h-12">
        <p class="text-gray-400 text-center" id="empty-cart-msg">ยังไม่มีสินค้าในตะกร้า</p>
       </div>
       <div class="flex justify-between items-center pt-3 border-t border-gray-300"><span class="font-bold text-gray-700">รวมทั้งหมด:</span> <span id="cart-total" class="text-xl font-bold text-purple-600">0 บาท</span>
       </div>
      </div>
      <div class="flex gap-4"><button onclick="clearCart()" class="flex-1 bg-gray-400 hover:bg-gray-500 text-white py-3 rounded-full font-bold transition-all"> 🗑️ ล้างตะกร้า </button> <button onclick="checkout()" class="flex-1 bg-green-500 hover:bg-green-600 text-white py-3 rounded-full font-bold transition-all"> 💳 ชำระเงิน </button>
      </div><!-- ผลการชำระเงิน -->
      <div id="checkout-result" class="hidden mt-6 bg-gradient-to-r from-green-100 to-emerald-100 rounded-xl p-6">
       <h3 class="font-bold text-green-800 text-center text-xl mb-4">✅ ชำระเงินสำเร็จ!</h3>
       <div class="space-y-2 text-center">
        <p class="text-gray-700">จ่ายเงิน: <span id="paid-amount" class="font-bold">0</span> บาท</p>
        <p class="text-gray-700">ราคาสินค้า: <span id="item-total" class="font-bold">0</span> บาท</p>
        <p class="text-2xl text-green-600 font-bold mt-4">เงินทอน: <span id="change-amount">0</span> บาท</p>
       </div>
      </div>
     </div>
    </div>
   </div>
  </div>
  <script>
    // Config และ State
    const defaultConfig = {
      app_title: 'คณิตศาสตร์การเงิน ป.5',
      welcome_message: 'เรียนรู้เรื่องเงิ��อย่างสนุก!',
      creator_name: 'เด็กชายกวีวัธน์ แมดมิ่งเหง้า',
      background_color: '#667eea',
      secondary_color: '#ffffff',
      text_color: '#1f2937',
      primary_action_color: '#8b5cf6',
      secondary_action_color: '#10b981',
      font_family: 'Kanit',
      font_size: 16
    };

    let totalScore = 0;
    let practiceScore = 0;
    let gameScore = 0;
    let currentQuestionIndex = 0;
    let questions = [];
    let currentGameAnswer = 0;
    let cart = [];
    let wallet = 500;

    // คำถามแบบฝึก��ัด
    function generateQuestions() {
      questions = [
        { q: 'เหรียญ 5 บาท 4 เหรียญ รวมเป็นกี่บาท?', a: 20, options: [15, 20, 25, 30], emoji: '🪙' },
        { q: 'ธนบัตร 20 บาท 3 ใบ รวมเป็นกี่บาท?', a: 60, options: [40, 50, 60, 80], emoji: '💵' },
        { q: 'ซื้อขนม 35 บาท จ่าย 50 บาท ได้เงินทอนกี่บาท?', a: 15, options: [10, 15, 20, 25], emoji: '🍬' },
        { q: 'เหรียญ 10 บาท 7 เหรียญ รวมเป็นกี่บาท?', a: 70, options: [60, 70, 80, 90], emoji: '🥇' },
        { q: 'ซื้อนม 18 บาท จ่าย 100 บาท ได้เงินทอนกี่บาท?', a: 82, options: [72, 82, 92, 78], emoji: '🥛' },
        { q: 'เหรียญ 2 บาท 15 เหรียญ รวมเป็นกี่บาท?', a: 30, options: [25, 30, 35, 40], emoji: '��' },
        { q: 'ซื้อผลไม้ 47 บาท จ่าย 100 บาท ได้เงินทอนกี่บาท?', a: 53, options: [43, 53, 63, 57], emoji: '🍎' },
        { q: 'ธนบัตร 100 บาท แลกเป็นเหรียญ 10 บาท ได้กี่เหรียญ?', a: 10, options: [5, 10, 15, 20], emoji: '💴' },
        { q: 'เหรียญ 1 บาท 25 เหรียญ รวมเป็นกี่บาท?', a: 25, options: [20, 25, 30, 35], emoji: '🪙' },
        { q: 'ซื้อของ 156 บาท จ่าย 200 บาท ได้เงินทอนกี่บาท?', a: 44, options: [34, 44, 54, 46], emoji: '🛍️' }
      ];
    }

    // ฟังก์ชันนำทาง
    function goHome() {
      hideAllScreens();
      document.getElementById('home-screen').classList.remove('hidden');
    }

    function showLessons() {
      hideAllScreens();
      document.getElementById('lessons-screen').classList.remove('hidden');
    }

    function showPractice() {
      hideAllScreens();
      document.getElementById('practice-screen').classList.remove('hidden');
      generateQuestions();
      currentQuestionIndex = 0;
      practiceScore = 0;
      updatePracticeScore();
      showQuestion();
    }

    function showGame() {
      hideAllScreens();
      document.getElementById('game-screen').classList.remove('hidden');
      newGameRound();
    }

    function showShop() {
      hideAllScreens();
      document.getElementById('shop-screen').classList.remove('hidden');
      wallet = 500;
      cart = [];
      updateShopUI();
    }

    function hideAllScreens() {
      document.getElementById('home-screen').classList.add('hidden');
      document.getElementById('lessons-screen').classList.add('hidden');
      document.getElementById('practice-screen').classList.add('hidden');
      document.getElementById('game-screen').classList.add('hidden');
      document.getElementById('shop-screen').classList.add('hidden');
    }

    // แบบฝึกหัด
    function showQuestion() {
      if (currentQuestionIndex >= questions.length) {
        showPracticeComplete();
        return;
      }

      const q = questions[currentQuestionIndex];
      document.getElementById('question-text').textContent = q.q;
      document.getElementById('question-emoji').textContent = q.emoji;
      document.getElementById('current-question').textContent = currentQuestionIndex + 1;
      
      const optionsDiv = document.getElementById('practice-options');
      optionsDiv.innerHTML = '';
      
      q.options.forEach(opt => {
        const btn = document.createElement('button');
        btn.className = 'bg-purple-100 hover:bg-purple-200 text-purple-800 font-bold py-4 px-6 rounded-xl text-xl transition-all';
        btn.textContent = opt + ' บาท';
        btn.onclick = () => checkAnswer(opt, q.a, btn);
        optionsDiv.appendChild(btn);
      });

      document.getElementById('practice-feedback').classList.add('hidden');
      document.getElementById('next-btn').classList.add('hidden');
    }

    function checkAnswer(selected, correct, btn) {
      const feedback = document.getElementById('practice-feedback');
      const feedbackText = document.getElementById('feedback-text');
      const buttons = document.querySelectorAll('#practice-options button');
      
      buttons.forEach(b => b.disabled = true);

      if (selected === correct) {
        btn.classList.remove('bg-purple-100', 'hover:bg-purple-200');
        btn.classList.add('bg-green-500', 'text-white', 'correct-answer');
        feedbackText.textContent = '🎉 ถูกต้อง! เก่งมาก!';
        feedbackText.className = 'text-lg font-bold text-green-600';
        practiceScore += 10;
        totalScore += 10;
        updatePracticeScore();
        updateTotalScore();
      } else {
        btn.classList.remove('bg-purple-100', 'hover:bg-purple-200');
        btn.classList.add('bg-red-500', 'text-white', 'wrong-answer');
        feedbackText.textContent = `❌ ไม่ถูกต้อง คำตอบคือ ${correct} บาท`;
        feedbackText.className = 'text-lg font-bold text-red-600';
        
        buttons.forEach(b => {
          if (parseInt(b.textContent) === correct) {
            b.classList.remove('bg-purple-100');
            b.classList.add('bg-green-500', 'text-white');
          }
        });
      }

      feedback.classList.remove('hidden');
      document.getElementById('next-btn').classList.remove('hidden');
    }

    function nextQuestion() {
      currentQuestionIndex++;
      showQuestion();
    }

    function showPracticeComplete() {
      const optionsDiv = document.getElementById('practice-options');
      document.getElementById('question-text').textContent = '🎊 ทำแบบฝึกหัดครบแล้ว!';
      document.getElementById('question-emoji').textContent = '🏆';
      optionsDiv.innerHTML = `
        <div class="col-span-2 text-center">
          <p class="text-2xl font-bold text-purple-600 mb-4">คะแนนที่ได้: ${practiceScore}/100</p>
          <button onclick="showPractice()" class="bg-purple-500 hover:bg-purple-600 text-white px-8 py-3 rounded-full font-bold transition-all">
            🔄 เริ่มใหม่
          </button>
        </div>
      `;
      document.getElementById('practice-feedback').classList.add('hidden');
      document.getElementById('next-btn').classList.add('hidden');
    }

    function updatePracticeScore() {
      document.getElementById('practice-score').textContent = practiceScore;
    }

    function updateTotalScore() {
      document.getElementById('total-score').textContent = totalScore;
    }

    // เกมนับเงิน
    function newGameRound() {
      const moneyDiv = document.getElementById('game-money');
      moneyDiv.innerHTML = '';
      currentGameAnswer = 0;
      
      const moneyTypes = [
        { value: 1, emoji: '🪙', label: '1฿', bg: 'bg-yellow-200' },
        { value: 2, emoji: '🥈', label: '2฿', bg: 'bg-gray-200' },
        { value: 5, emoji: '🔵', label: '5฿', bg: 'bg-blue-200' },
        { value: 10, emoji: '🟣', label: '10฿', bg: 'bg-purple-200' },
        { value: 20, emoji: '💵', label: '20฿', bg: 'bg-green-200' },
        { value: 50, emoji: '💶', label: '50฿', bg: 'bg-teal-200' },
        { value: 100, emoji: '💴', label: '100฿', bg: 'bg-red-200' }
      ];

      const numItems = 4 + Math.floor(Math.random() * 4);
      
      for (let i = 0; i < numItems; i++) {
        const money = moneyTypes[Math.floor(Math.random() * moneyTypes.length)];
        currentGameAnswer += money.value;
        
        const div = document.createElement('div');
        div.className = `${money.bg} rounded-xl p-3 text-center min-w-16 slide-in`;
        div.style.animationDelay = `${i * 0.1}s`;
        div.innerHTML = `
          <div class="text-2xl">${money.emoji}</div>
          <div class="font-bold text-sm">${money.label}</div>
        `;
        moneyDiv.appendChild(div);
      }

      document.getElementById('game-answer').value = '';
      document.getElementById('game-feedback').classList.add('hidden');
    }

    function checkGameAnswer() {
      const userAnswer = parseInt(document.getElementById('game-answer').value) || 0;
      const feedback = document.getElementById('game-feedback');
      const feedbackText = document.getElementById('game-feedback-text');

      if (userAnswer === currentGameAnswer) {
        feedbackText.textContent = '🎉 ถูกต้อง! เก่งมาก!';
        feedbackText.className = 'text-lg font-bold text-green-600';
        gameScore += 10;
        totalScore += 10;
        document.getElementById('game-score').textContent = gameScore;
        updateTotalScore();
      } else {
        feedbackText.textContent = `❌ คำตอบที่ถูกคือ ${currentGameAnswer} บาท`;
        feedbackText.className = 'text-lg font-bold text-red-600';
      }

      feedback.classList.remove('hidden');
    }

    // ร้านค้าจำลอง
    function addToCart(name, price) {
      cart.push({ name, price });
      updateShopUI();
    }

    function clearCart() {
      cart = [];
      document.getElementById('checkout-result').classList.add('hidden');
      updateShopUI();
    }

    function updateShopUI() {
      document.getElementById('wallet-amount').textContent = wallet + ' บาท';
      
      const cartItemsDiv = document.getElementById('cart-items');
      const emptyMsg = document.getElementById('empty-cart-msg');
      
      if (cart.length === 0) {
        emptyMsg.classList.remove('hidden');
        cartItemsDiv.querySelectorAll('.cart-item').forEach(el => el.remove());
      } else {
        emptyMsg.classList.add('hidden');
        cartItemsDiv.innerHTML = '';
        cart.forEach((item, index) => {
          const div = document.createElement('div');
          div.className = 'cart-item flex justify-between items-center bg-white rounded-lg p-2';
          div.innerHTML = `
            <span>${item.name}</span>
            <div class="flex items-center gap-2">
              <span class="font-bold">${item.price} บาท</span>
              <button onclick="removeFromCart(${index})" class="text-red-500 hover:text-red-700">✕</button>
            </div>
          `;
          cartItemsDiv.appendChild(div);
        });
      }

      const total = cart.reduce((sum, item) => sum + item.price, 0);
      document.getElementById('cart-total').textContent = total + ' บาท';
    }

    function removeFromCart(index) {
      cart.splice(index, 1);
      updateShopUI();
    }

    function checkout() {
      if (cart.length === 0) {
        const feedback = document.getElementById('checkout-result');
        feedback.innerHTML = '<p class="text-center text-orange-600 font-bold">⚠️ กรุณาเลือกสินค้าก่อนชำระเงิน</p>';
        feedback.className = 'mt-6 bg-orange-100 rounded-xl p-6';
        feedback.classList.remove('hidden');
        return;
      }

      const total = cart.reduce((sum, item) => sum + item.price, 0);
      
      if (total > wallet) {
        const feedback = document.getElementById('checkout-result');
        feedback.innerHTML = '<p class="text-center text-red-600 font-bold">❌ เงินไม่พอ! กรุณานำสินค้าบางอ���่างออก</p>';
        feedback.className = 'mt-6 bg-red-100 rounded-xl p-6';
        feedback.classList.remove('hidden');
        return;
      }

      const change = wallet - total;
      
      document.getElementById('paid-amount').textContent = wallet;
      document.getElementById('item-total').textContent = total;
      document.getElementById('change-amount').textContent = change;
      
      const feedback = document.getElementById('checkout-result');
      feedback.className = 'mt-6 bg-gradient-to-r from-green-100 to-emerald-100 rounded-xl p-6';
      feedback.innerHTML = `
        <h3 class="font-bold text-green-800 text-center text-xl mb-4">✅ ชำระเงินสำเร็จ!</h3>
        <div class="space-y-2 text-center">
          <p class="text-gray-700">จ่ายเงิน: <span class="font-bold">${wallet}</span> บาท</p>
          <p class="text-gray-700">ราคาสินค้า: <span class="font-bold">${total}</span> บาท</p>
          <p class="text-2xl text-green-600 font-bold mt-4">เงินทอน: ${change} บาท</p>
        </div>
      `;
      feedback.classList.remove('hidden');
      
      totalScore += 5;
      updateTotalScore();
      
      wallet = change;
      cart = [];
      updateShopUI();
    }

    // Element SDK
    async function onConfigChange(config) {
      const title = config.app_title || defaultConfig.app_title;
      const welcome = config.welcome_message || defaultConfig.welcome_message;
      const creator = config.creator_name || defaultConfig.creator_name;
      const bgColor = config.background_color || defaultConfig.background_color;
      const secondaryColor = config.secondary_color || defaultConfig.secondary_color;
      const textColor = config.text_color || defaultConfig.text_color;
      const primaryAction = config.primary_action_color || defaultConfig.primary_action_color;
      const secondaryAction = config.secondary_action_color || defaultConfig.secondary_action_color;
      const fontFamily = config.font_family || defaultConfig.font_family;
      const fontSize = config.font_size || defaultConfig.font_size;

      document.getElementById('main-title').textContent = title;
      document.getElementById('welcome-text').textContent = welcome + ' 💰';
      document.getElementById('creator-name').textContent = creator;
      
      document.getElementById('app-container').style.background = `linear-gradient(135deg, ${bgColor} 0%, ${adjustColor(bgColor, -20)} 100%)`;
      
      document.querySelectorAll('.bg-white').forEach(el => {
        el.style.backgroundColor = secondaryColor;
      });
      
      document.body.style.fontFamily = `${fontFamily}, Kanit, sans-serif`;
      document.body.style.fontSize = `${fontSize}px`;
    }

    function adjustColor(color, amount) {
      const hex = color.replace('#', '');
      const r = Math.max(0, Math.min(255, parseInt(hex.substr(0, 2), 16) + amount));
      const g = Math.max(0, Math.min(255, parseInt(hex.substr(2, 2), 16) + amount));
      const b = Math.max(0, Math.min(255, parseInt(hex.substr(4, 2), 16) + amount));
      return `#${r.toString(16).padStart(2, '0')}${g.toString(16).padStart(2, '0')}${b.toString(16).padStart(2, '0')}`;
    }

    function mapToCapabilities(config) {
      return {
        recolorables: [
          {
            get: () => config.background_color || defaultConfig.background_color,
            set: (value) => { config.background_color = value; window.elementSdk.setConfig({ background_color: value }); }
          },
          {
            get: () => config.secondary_color || defaultConfig.secondary_color,
            set: (value) => { config.secondary_color = value; window.elementSdk.setConfig({ secondary_color: value }); }
          },
          {
            get: () => config.text_color || defaultConfig.text_color,
            set: (value) => { config.text_color = value; window.elementSdk.setConfig({ text_color: value }); }
          },
          {
            get: () => config.primary_action_color || defaultConfig.primary_action_color,
            set: (value) => { config.primary_action_color = value; window.elementSdk.setConfig({ primary_action_color: value }); }
          },
          {
            get: () => config.secondary_action_color || defaultConfig.secondary_action_color,
            set: (value) => { config.secondary_action_color = value; window.elementSdk.setConfig({ secondary_action_color: value }); }
          }
        ],
        borderables: [],
        fontEditable: {
          get: () => config.font_family || defaultConfig.font_family,
          set: (value) => { config.font_family = value; window.elementSdk.setConfig({ font_family: value }); }
        },
        fontSizeable: {
          get: () => config.font_size || defaultConfig.font_size,
          set: (value) => { config.font_size = value; window.elementSdk.setConfig({ font_size: value }); }
        }
      };
    }

    function mapToEditPanelValues(config) {
      return new Map([
        ['app_title', config.app_title || defaultConfig.app_title],
        ['welcome_message', config.welcome_message || defaultConfig.welcome_message],
        ['creator_name', config.creator_name || defaultConfig.creator_name]
      ]);
    }

    // Initialize
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities,
        mapToEditPanelValues
      });
    }

    generateQuestions();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9c1343a0d6f97335',t:'MTc2ODk2MTMxMS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
