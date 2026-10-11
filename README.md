
<html lang="fa">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>روز دختر مبارک</title>
<style>
  body {
    background: white;
    margin: 0;
    height: 100vh;
    overflow: hidden;
    font-family: sans-serif;
  }

  .top-left {
    position: fixed;
    top: 15px;
    left: 15px;
    color: #0066ff;
    font-size: 14px;
    font-weight: bold;
    z-index: 20;
  }

  .main-text {
    color: #0066ff;
    font-size: 42px;
    font-weight: bold;
    direction: rtl;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    white-space: nowrap;
    z-index: 10;
  }

  .cursor {
    animation: blink 0.8s infinite;
    color: #0066ff;
    font-size: 42px;
    font-weight: bold;
  }

  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }

  .heart {
    position: absolute;
    opacity: 0;
    animation: pop 0.3s forwards;
    z-index: 1;
  }

  @keyframes pop {
    from { opacity: 0; transform: scale(0.1); }
    to { opacity: 1; transform: scale(1); }
  }
</style>
</head>
<body>

  <div class="top-left">456</div>

  <span class="main-text" id="typewriter"></span>
  <span class="cursor" id="cursor">|</span>

<script>
  const text = "روز دختر مبارک";
  const target = document.getElementById('typewriter');
  const cursor = document.getElementById('cursor');
  let i = 0;

  function type() {
    if (i < text.length) {
      target.textContent += text[i];
      i++;
      setTimeout(type, 300);
    } else {
      cursor.style.display = 'none';
      setTimeout(fillRandom, 500);
    }
  }

  function fillRandom() {
    const colors = ['💙', '💚', '💜'];
    const total = 5000;
    let count = 0;

    function addOne() {
      if (count >= total) return;

      const heart = document.createElement('span');
      heart.className = 'heart';
      heart.textContent = colors[Math.floor(Math.random() * colors.length)];

      const x = Math.random() * window.innerWidth;
      const y = Math.random() * window.innerHeight;
      heart.style.left = x + 'px';
      heart.style.top = y + 'px';
      heart.style.fontSize = (12 + Math.random() * 10) + 'px';

      document.body.appendChild(heart);

      count++;
      setTimeout(addOne, 1);
    }

    addOne();
  }

  type();
</script>

</body>
</html>
