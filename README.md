<<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ucapan Cinta Ultimate 💖</title>
<style>
    body {
        font-family: 'Comic Sans MS', cursive, sans-serif;
        text-align: center;
        min-height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin: 0;
        overflow: hidden;
        color: #fff;
        transition: background 0.5s ease;
    }

    h1 {
        font-size: 3rem;
        margin-bottom: 20px;
        text-shadow: 2px 2px 5px #eb539c;
    }

    #message {
        font-size: 1.5rem;
        margin: 20px 0;
        padding: 20px;
        border-radius: 15px;
        background-color: rgba(255,255,255,0.2);
        max-width: 600px;
        opacity: 0;
        transform: translateY(-20px);
        transition: all 0.6s ease;
    }

    #message.show {
        opacity: 1;
        transform: translateY(0);
    }

    button {
        padding: 12px 25px;
        font-size: 1.2rem;
        border: none;
        border-radius: 10px;
        cursor: pointer;
        background-color: #fff;
        color: #ff6f91;
        transition: 0.3s;
        margin-top: 10px;
    }

    button:hover {
        background-color: #ff6f91;
        color: #fff;
    }

    input, select {
        padding: 10px;
        font-size: 1rem;
        border-radius: 10px;
        border: none;
        margin-top: 10px;
        width: 250px;
    }

    /* Animasi hati */
    .heart {
        position: absolute;
        width: 20px;
        height: 20px;
        background-color: #ff6f91;
        transform: rotate(-45deg);
        animation: float 4s linear infinite;
        border-radius: 5px 5px 0 0;
    }

    .heart::before,
    .heart::after {
        content: '';
        position: absolute;
        width: 20px;
        height: 20px;
        background-color: #ff6f91;
        border-radius: 50%;
    }

    .heart::before { top: -10px; left: 0; }
    .heart::after { left: 10px; top: 0; }

    @keyframes float {
        0% { transform: translateY(0) rotate(-45deg); opacity: 1; }
        100% { transform: translateY(-800px) rotate(-45deg); opacity: 0; }
    }
</style>
</head>
<body>
<h1>Untuk Kekasihku Nadiya 💖</h1>

<div id="message">Klik tombol di bawah untuk ucapan cinta spesial!</div>

<button onclick="showMessage()">Tampilkan Ucapan</button>

<div>
    <input type="text" id="newMessage" placeholder="Tambahkan ucapanmu sendiri">
    <button onclick="addMessage()">Tambah Ucapan</button>
</div>

<div>
    <label for="theme">Pilih Tema:</label>
    <select id="theme" onchange="changeTheme(this.value)">
        <option value="pink">Pink Romantis</option>
        <option value="purple">Ungu Manis</option>
        <option value="blue">Biru Lembut</option>
        <option value="sunset">Senja Hangat</option>
    </select>
</div>

<div style="margin-top: 10px;">
    <button onclick="copyLink()">Salin Link Ucapan</button>
</div>

<audio id="clickSound" src="https://freesound.org/data/previews/522/522708_7037-lq.mp3"></audio>

<script>
    const messages = [
        "Kamu adalah alasan aku tersenyum setiap hari 😘",
        "Cintaku padamu tumbuh setiap detik yang berlalu ❤️",
        "Bersamamu, dunia terasa lebih indah 🌹",
        "Aku mencintaimu lebih dari kata-kata bisa ungkapkan 💕",
        "Kamu adalah mimpi terindah yang menjadi nyata 😍"
    ];

    const body = document.body;
    const messageDiv = document.getElementById('message');
    const clickSound = document.getElementById('clickSound');

    // Cek URL untuk ucapan custom
    const urlParams = new URLSearchParams(window.location.search);
    const customMessage = urlParams.get('msg');
    if(customMessage) {
        messages.push(customMessage);
        showMessage();
    }

    function showMessage() {
        clickSound.play();
        const randomIndex = Math.floor(Math.random() * messages.length);
        messageDiv.textContent = messages[randomIndex];
        messageDiv.classList.remove('show');
        void messageDiv.offsetWidth;
        messageDiv.classList.add('show');
        createHeart();
    }

    function addMessage() {
        const input = document.getElementById('newMessage');
        if(input.value.trim() !== '') {
            messages.push(input.value.trim());
            alert('Ucapanmu berhasil ditambahkan!');
            input.value = '';
        }
    }

    function createHeart() {
        const heart = document.createElement('div');
        heart.classList.add('heart');
        heart.style.left = Math.random() * window.innerWidth + 'px';
        heart.style.animationDuration = 3 + Math.random() * 2 + 's';
        document.body.appendChild(heart);
        setTimeout(() => heart.remove(), 4000);
    }

    function changeTheme(theme) {
        switch(theme) {
            case 'pink':
                body.style.background = 'linear-gradient(to right, #ff9a9e, #fad0c4)';
                break;
            case 'purple':
                body.style.background = 'linear-gradient(to right, #a18cd1, #fbc2eb)';
                break;
            case 'blue':
                body.style.background = 'linear-gradient(to right, #89f7fe, #66a6ff)';
                break;
            case 'sunset':
                body.style.background = 'linear-gradient(to right, #ffecd2, #fcb69f)';
                break;
        }
    }

    function copyLink() {
        const currentUrl = window.location.href.split('?')[0];
        const link = `${currentUrl}?msg=${encodeURIComponent(messageDiv.textContent)}`;
        navigator.clipboard.writeText(link).then(() => {
            alert('Link ucapan berhasil disalin! 🎉');
        });
    }
</script>
</body>
</html>

