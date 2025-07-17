<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Olaf & Rizvy</title>
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Cormorant+Garamond:wght@400;600&display=swap" rel="stylesheet" />
  <style>
    :root {
      --bg: #1a1a2e;
      --text-light: #f0e6f6;
      --accent: #ff7f50;
      --soft-pink: #f8cdda;
      --soft-purple: #d6a5d6;
      --shadow: rgba(255, 127, 80, 0.4);
      --star-color: #fff8ea;
      --heart-color: #ff6f91;
    }
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      background: var(--bg);
      color: var(--text-light);
      font-family: 'Cormorant Garamond', serif;
      line-height: 1.6;
      padding: 0 1.5rem 4rem;
      overflow-x: hidden;
      min-height: 100vh;
      position: relative;
    }
    header {
      padding: 4rem 1rem 3rem;
      text-align: center;
      position: relative;
      z-index: 10;
    }
    header h1 {
      font-family: 'Cormorant Garamond', serif;
      font-style: italic;
      font-size: 3.5rem;
      color: var(--accent);
      text-shadow: 0 0 8px var(--accent);
    }
    header p.subtitle {
      font-size: 1.3rem;
      color: var(--soft-pink);
      font-style: italic;
    }
    header p.timer {
      font-size: 1.15rem;
      color: var(--soft-purple);
      font-weight: 600;
      margin-top: 0.5rem;
      white-space: pre-line;
    }
    section {
      max-width: 720px;
      margin: 2rem auto;
      background: rgba(255, 255, 255, 0.07);
      border-radius: 18px;
      padding: 2rem 2.5rem;
      box-shadow: 0 0 30px var(--shadow);
      backdrop-filter: blur(10px);
      position: relative;
      z-index: 10;
    }
    section h2 {
      font-family: 'Great Vibes', cursive;
      font-size: 2.5rem;
      color: var(--soft-purple);
      text-align: center;
      margin-bottom: 1.2rem;
    }
    section p {
      font-size: 1.15rem;
      text-align: center;
      color: var(--text-light);
    }
    .btn {
      background: var(--accent);
      color: var(--bg);
      border: none;
      padding: 0.75rem 1.5rem;
      border-radius: 30px;
      font-weight: 600;
      font-size: 1rem;
      cursor: pointer;
      box-shadow: 0 4px 10px var(--shadow);
      transition: background 0.3s ease;
      display: inline-block;
      margin: 0.5rem auto;
    }
    .btn:hover {
      background: var(--soft-purple);
      color: var(--text-light);
      box-shadow: 0 6px 20px var(--soft-purple);
    }
    .love-message {
      margin-top: 1rem;
      color: var(--soft-pink);
      font-size: 1.3rem;
      text-align: center;
      font-style: italic;
      opacity: 0;
      transition: opacity 0.6s ease;
    }
    .love-message.show { opacity: 1; }
    .audio-player {
      text-align: center;
      margin-top: 1rem;
    }
    audio {
      width: 100%;
      max-width: 400px;
      border-radius: 12px;
      box-shadow: 0 4px 20px var(--shadow);
    }
    .upload-section { text-align: center; }
    .gallery {
      display: flex;
      gap: 1rem;
      flex-wrap: wrap;
      justify-content: center;
      margin-top: 1rem;
    }
    .gallery img {
      width: 180px;
      height: 120px;
      object-fit: cover;
      border-radius: 14px;
      box-shadow: 0 4px 10px var(--shadow);
      transition: transform 0.3s ease;
      cursor: pointer;
    }
    .gallery img:hover {
      transform: scale(1.05);
      box-shadow: 0 8px 20px var(--accent);
    }
    footer {
      text-align: center;
      color: #aaa;
      font-size: 0.9rem;
      padding: 3rem 1rem 1rem;
      font-style: italic;
      z-index: 10;
    }
    .stars {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: transparent;
      z-index: 1;
      pointer-events: none;
    }
    .star {
      position: absolute;
      background: var(--star-color);
      border-radius: 50%;
      opacity: 0.9;
      animation: twinkle 3s ease-in-out infinite;
      filter: drop-shadow(0 0 3px var(--star-color));
    }
    @keyframes twinkle {
      0%, 100% {opacity: 0.9;}
      50% {opacity: 0.3;}
    }
    #hearts {
      position: fixed;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      overflow: hidden;
      z-index: 2;
    }
    .heart-float {
      position: absolute;
      color: var(--heart-color);
      font-size: 18px;
      opacity: 0.8;
      animation: floatHeart 6s linear forwards;
      filter: drop-shadow(0 0 4px var(--heart-color));
    }
    @keyframes floatHeart {
      0% { transform: translateY(0) scale(1); opacity: 0.8; }
      100% { transform: translateY(-200px) scale(1.3); opacity: 0; }
    }
    .bg-music {
      position: absolute;
      opacity: 0;
      pointer-events: none;
    }
    @media (max-width: 600px) {
      header h1 { font-size: 2.8rem; }
      section h2 { font-size: 1.8rem; }
      .gallery img { width: 140px; height: 90px; }
    }
  </style>
</head>
<body>
  <div class="stars"></div>
  <div id="hearts"></div>
  <audio class="bg-music" autoplay loop>
    <source src="https://dl.sndup.net/xfgv/A%20Thousand%20Years%20-%20Christina%20Perri%20(Piano%20Cover).mp3" type="audio/mpeg" />
  </audio>
  <header>
    <h1>Olaf & Rizvy</h1>
    <p class="subtitle">Even through time and distance, Forever in Love</p>
    <p class="timer">Together since<br>14.10.2024</p>
  </header>
  <section>
    <h2>Our Journey</h2>
    <p>From the first hello to countless shared dreams, our love has grown stronger with each moment. Through time zones and miles, we keep the flame alive.</p>
  </section>
  <section>
    <h2>Photo Memories</h2>
    <div class="upload-section">
      <input type="file" id="photoUpload" accept="image/*" multiple />
    </div>
    <div class="gallery" id="preview"></div>
  </section>
  <section>
    <h2>Poetry for You</h2>
    <p>“I’ll love you for a thousand lifetimes more,<br/>Through storms and stars, oceans and shores.<br/>If forever has a face, it’s yours to me,<br/>My heart, my soul, my destiny.”</p>
  </section>
  <section>
    <h2>Music of Our Hearts</h2>
    <div class="audio-player">
      <audio controls>
        <source src="https://cdn.pixabay.com/download/audio/2022/03/04/audio_148209ab51.mp3?filename=romantic-guitar-6000.mp3" type="audio/mpeg" />
        Your browser does not support the audio element.
      </audio>
    </div>
  </section>
  <section class="more-content">
    <h2>To Us, Forever</h2>
    <p>Here’s to the sunsets we’ll watch, the rain we’ll dance under, and the love that stays long after the music fades. To every whispered dream, every promise made, and the endless tomorrows waiting for us.</p>
  </section>
  <section style="text-align:center;">
    <button class="btn" onclick="sendLove()">Send Love</button>
    <div id="loveMessage" class="love-message">I Love you Today, Tomorrow and FOREVER Olaf</div>
  </section>
  <footer>
    Made with love for– Olaf
  </footer>
  <script>
    const starContainer = document.querySelector('.stars');
    for (let i = 0; i < 60; i++) {
      const star = document.createElement('div');
      star.classList.add('star');
      const size = Math.random() * 3 + 1;
      star.style.width = size + 'px';
      star.style.height = size + 'px';
      star.style.top = Math.random() * 100 + '%';
      star.style.left = Math.random() * 100 + '%';
      starContainer.appendChild(star);
    }
    setInterval(() => {
      const heart = document.createElement('div');
      heart.classList.add('heart-float');
      heart.textContent = '❤';
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.fontSize = Math.random() * 10 + 14 + 'px';
      document.getElementById('hearts').appendChild(heart);
      setTimeout(() => heart.remove(), 6000);
    }, 1200);
    function sendLove() {
      for (let i = 0; i < 12; i++) {
        const heart = document.createElement('div');
        heart.classList.add('heart-float');
        heart.textContent = '❤';
        heart.style.left = Math.random() * 100 + 'vw';
        heart.style.fontSize = Math.random() * 14 + 16 + 'px';
        document.getElementById('hearts').appendChild(heart);
        setTimeout(() => heart.remove(), 6000);
      }
      document.getElementById("loveMessage").classList.add("show");
    }
    const uploadInput = document.getElementById('photoUpload');
    const preview = document.getElementById('preview');
    uploadInput.addEventListener('change', () => {
      preview.innerHTML = '';
      Array.from(uploadInput.files).forEach(file => {
        const reader = new FileReader();
        reader.onload = e => {
          const img = document.createElement('img');
          img.src = e.target.result;
          preview.appendChild(img);
        };
        reader.readAsDataURL(file);
      });
    });
  </script>
</body>
</html>
