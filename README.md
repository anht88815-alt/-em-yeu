
<html lang="vi">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Dỗ người yêu</title>
  <style>
    body { 
      font-family: "Segoe UI", Roboto, sans-serif; 
      background: #f9aab6; /* nền hồng */
      margin:0; 
      padding:20px;
      min-height: 100vh;
      text-align:center;
      overflow:hidden;
    }
    h2 { 
      margin-top:20px; 
      color:#fff; 
      text-shadow: 0 2px 4px rgba(0,0,0,0.2);
    }
    button { 
      padding:12px 18px; 
      margin:8px; 
      border:none; 
      border-radius:10px; 
      font-weight:600; 
      cursor:pointer; 
      font-size:15px; 
      transition:transform 0.2s; 
    }
    .btn { background:#ff4f70; color:white; }
    .btn:hover { background:#e13c5e; transform:scale(1.05); }
    #msg { 
      margin-top:20px; 
      font-size:20px; 
      min-height:60px; 
      line-height:1.5; 
      color:#fff; 
      text-shadow: 0 2px 4px rgba(0,0,0,0.3);
      opacity:0; 
    }
    #cat { 
      margin-top:20px; 
      max-width:100%; 
      border-radius:12px; 
      box-shadow:0 4px 12px rgba(0,0,0,0.15); 
      display:none; 
    }
    .fade-in { animation: fadeIn 0.6s ease forwards; }
    @keyframes fadeIn {
      from { opacity:0; transform: translateY(10px) scale(0.97); }
      to { opacity:1; transform: translateY(0) scale(1); }
    }

    /* Mèo hôn cố định */
    #kiss-cat {
      position: fixed;
      bottom: 10px;
      left: 50%;
      transform: translateX(-50%);
      width: 140px;
      z-index: 200;
      border-radius: 12px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.25);
    }

    /* Nụ hôn bay */
    .kiss {
      position: absolute;
      font-size: 28px;
      animation: floatUp 3s linear forwards;
      pointer-events: none;
      z-index: 150;
    }
    @keyframes floatUp {
      0% { transform: translateY(0) scale(1); opacity: 1; }
      50% { transform: translateY(-100px) scale(1.3); opacity: 0.8; }
      100% { transform: translateY(-200px) scale(0.8); opacity: 0; }
    }
    
  </style>
</head>
<body>
  <h2>💌 gửi em yêu  🐱</h2>
  <button class="btn" id="gen">bấm vào nè bà xã</button>
  
  <div id="msg">Nhấn nút để có câu ngọt.</div>
  <img id="cat" src="" alt="Mèo dễ thương" />
  <!-- Thêm nút bật nhạc vào <body> -->
<button id="playMusic" style="
  position: fixed; top: 15px; right: 15px;
  background:#ff4f70; color:white;
  border:none; border-radius:10px;
  padding:10px 14px; font-size:14px;
  cursor:pointer; z-index:500;
">
▶️ Bật nhạc
</button>

<audio id="bg-music" loop>
  <source src="https://www.bensound.com/bensound-music/bensound-littleidea.mp3" type="audio/mpeg">
</audio>

<script>
  const musicBtn = document.getElementById("playMusic");
  const music = document.getElementById("bg-music");

  musicBtn.addEventListener("click", () => {
    music.play();
    musicBtn.style.display = "none"; // ẩn nút sau khi bấm
  });
</script>

  <!-- Mèo hôn cố định -->
  <img id="kiss-cat" src="https://media.giphy.com/media/MDJ9IbxxvDUQM/giphy.gif" alt="Mèo hôn cute" />

  <!-- Nhạc nền dễ thương -->
  <audio id="bg-music" autoplay loop>
    <source src="https://www.bensound.com/bensound-music/bensound-littleidea.mp3" type="audio/mpeg">
  </audio>

  <script>
    const messages = [
      "Anh xin lỗi nhé… cười lại với anh đi anh dẫn đi ăn kem 🤗",
      "Đừng giận lâu, anh không chịu nổi cảnh em lạnh lùng với anh đâu 😢",
      "Anh biết lỗi rồi, đổi lại cho anh cơ hội làm em vui nhé 💙",
      "yêu em lắn đừng dận nữa , mai đi ăn với anh nha 😌",
      "Nè, cho anh được làm lý do để em cười lại hôm nay nha 🌸",
      "Nếu một cái ôm có thể sửa lỗi, anh sẵn sàng ôm em cả ngày 🤍",
      "Em quan trọng hơn mấy cuộc cãi vã nhỏ nhặt này nhiều lắm đó ❤️",
      "Anh chỉ muốn thấy em vui vẻ, không muốn thấy em buồn vì anh 🥺",
      "Tuy em đang giận, nhưng anh vẫn thương em nhất 🌷",
      "Xin lỗi nhé, anh hứa lần sau sẽ nghe em nhiều hơn 💭"
    ];

    const cats = [
      "https://media.giphy.com/media/MCfhrrNN1goH6/giphy.gif",
      "https://media.giphy.com/media/12PA1eI8FBqEBa/giphy.gif",
      "https://media.giphy.com/media/10dU7AN7xsi1I4/giphy.gif",
      "https://media.giphy.com/media/11s7Ke7jcNxCHS/giphy.gif",
      "https://media.giphy.com/media/13borq7Zo2kulO/giphy.gif",
      "https://media.giphy.com/media/krP2NRkLqnKEg/giphy.gif"
    ];

    const msg = document.getElementById("msg");
    const cat = document.getElementById("cat");

    function createKiss() {
      const kiss = document.createElement("div");
      kiss.className = "kiss";
      kiss.textContent = "💋";
      kiss.style.left = Math.random() * window.innerWidth + "px";
      kiss.style.bottom = "20px";
      document.body.appendChild(kiss);
      setTimeout(() => kiss.remove(), 3000);
    }

    document.getElementById("gen").addEventListener("click", () => {
      msg.textContent = messages[Math.floor(Math.random() * messages.length)];
      msg.classList.remove("fade-in"); void msg.offsetWidth; msg.classList.add("fade-in");

      cat.src = cats[Math.floor(Math.random() * cats.length)];
      cat.style.display = "block";
      cat.classList.remove("fade-in"); void cat.offsetWidth; cat.classList.add("fade-in");

      // Tạo 5 nụ hôn bay
      for (let i = 0; i < 5; i++) {
        setTimeout(createKiss, i * 300);
      }
    });

    document.getElementById("copy").addEventListener("click", async () => {
      const txt = msg.textContent;
      if (!txt) return;
      try {
        await navigator.clipboard.writeText(txt);
        alert("Đã copy, dán vào Messenger/Zalo thôi!");
      } catch {
        const ta = document.createElement("textarea");
        ta.value = txt; document.body.appendChild(ta);
        ta.select(); document.execCommand("copy"); ta.remove();
        alert("Copy thành công (fallback).");
      }
    });
    
  </script>
</body>
</html>
