# -qismet-game
Qismət Game - Oyun saytı
from flask import Flask, render_template_string
app = Flask(__name__)

HTML = """
<!DOCTYPE html>
<html lang="az">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Qismət Games</title>

<style>
* {
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
}

body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #0f172a;
    color: white;
}

nav {
    position: sticky;
    top: 0;
    z-index: 10;
    background: #111827;
    padding: 15px;
    display: flex;
    justify-content: center;
    gap: 15px;
    flex-wrap: wrap;
    box-shadow: 0 3px 15px #0008;
}

nav a {
    color: white;
    text-decoration: none;
    padding: 10px 14px;
    border-radius: 8px;
}

nav a:hover {
    background: #2563eb;
}

.hero {
    min-height: 500px;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 30px;
    background:
        linear-gradient(135deg, #2563eb, #7c3aed);
}

.hero h1 {
    font-size: 55px;
    margin-bottom: 10px;
}

.hero p {
    font-size: 20px;
}

.btn {
    display: inline-block;
    margin-top: 20px;
    padding: 13px 25px;
    background: white;
    color: #2563eb;
    border: none;
    border-radius: 10px;
    font-weight: bold;
    cursor: pointer;
}

section {
    padding: 70px 20px;
    text-align: center;
}

section h2 {
    font-size: 35px;
}

.search {
    width: 90%;
    max-width: 500px;
    padding: 15px;
    border: none;
    border-radius: 10px;
    margin: 20px;
    font-size: 16px;
}

.games {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 20px;
}

.game {
    width: 260px;
    padding: 25px;
    background: #1e293b;
    border-radius: 18px;
    box-shadow: 0 5px 20px #0005;
    transition: 0.3s;
}

.game:hover {
    transform: translateY(-7px);
}

.game-icon {
    font-size: 60px;
}

.play {
    background: #2563eb;
    color: white;
    border: none;
    padding: 11px 20px;
    border-radius: 8px;
    cursor: pointer;
}

.play:hover {
    background: #1d4ed8;
}

.profile {
    max-width: 500px;
    margin: auto;
    background: #1e293b;
    padding: 30px;
    border-radius: 20px;
}

.avatar {
    font-size: 80px;
}

footer {
    background: #020617;
    text-align: center;
    padding: 30px;
}
</style>
</head>

<body>

<nav>
    <a href="#ana">🏠 Ana səhifə</a>
    <a href="#oyunlar">🎮 Oyunlar</a>
    <a href="#reytinq">🏆 Reytinq</a>
    <a href="#profil">👤 Profil</a>
    <a href="#haqqimda">👨‍💻 Haqqımda</a>
</nav>

<section id="ana" class="hero">
    <div>
        <h1>🎮 QİSMƏT GAMES</h1>
        <p>Python 3 ilə hazırlanmış oyun dünyasına xoş gəlmisən!</p>

        <a href="#oyunlar">
            <button class="btn">🎮 Oyunlara bax</button>
        </a>
    </div>
</section>

<section id="oyunlar">

    <h2>🎮 Oyunlar</h2>

    <input
        class="search"
        id="search"
        type="text"
        placeholder="🔎 Oyun axtar..."
        onkeyup="searchGames()"
    >

    <div class="games">

        <div class="game">
            <div class="game-icon">🚗</div>
            <h3>GTA Style</h3>
            <p>Açıq dünya oyun layihəsi</p>
            <p>⭐ 4.8</p>
            <button class="play" onclick="startGame('GTA Style')">
                Oyna
            </button>
        </div>

        <div class="game">
            <div class="game-icon">⭐</div>
            <h3>Brawl Style</h3>
            <p>Döyüş oyun layihəsi</p>
            <p>⭐ 4.7</p>
            <button class="play" onclick="startGame('Brawl Style')">
                Oyna
            </button>
        </div>

        <div class="game">
            <div class="game-icon">🐍</div>
            <h3>Python Snake</h3>
            <p>Klassik ilan oyunu</p>
            <p>⭐ 4.9</p>
            <button class="play" onclick="startGame('Python Snake')">
                Oyna
            </button>
        </div>

        <div class="game">
            <div class="game-icon">🚀</div>
            <h3>Space Battle</h3>
            <p>Kosmik döyüş oyunu</p>
            <p>⭐ 4.6</p>
            <button class="play" onclick="startGame('Space Battle')">
                Oyna
            </button>
        </div>

    </div>
</section>

<section id="reytinq">

    <h2>🏆 Reytinq</h2>

    <div class="profile">
        <h3>🥇 1. Qismət</h3>
        <p>⭐ 1250 xal</p>

        <h3>🥈 2. Gamer</h3>
        <p>⭐ 980 xal</p>

        <h3>🥉 3. PythonPlayer</h3>
        <p>⭐ 750 xal</p>
    </div>

</section>

<section id="profil">

    <h2>👤 Profil</h2>

    <div class="profile">
        <div class="avatar">👨‍💻</div>

        <h3>Qismət</h3>

        <p>🎮 Oyunçu</p>
        <p>🐍 Python proqramlaşdırma</p>
        <p>🏆 1250 xal</p>
    </div>

</section>

<section id="haqqimda">

    <h2>👨‍💻 Haqqımda</h2>

    <div class="profile">

        <div class="avatar">👨‍💻</div>

        <h3>Qismət Məmmədzadə</h3>

        <p>11 yaşlı məktəbliyəm.</p>

        <p>
            Python 3 ilə proqramlaşdırma,
            oyun hazırlama və veb sayt yaratmağı öyrənirəm.
        </p>

        <p>🎮 Oyunlar</p>
        <p>🐍 Python</p>
        <p>💻 Proqramlaşdırma</p>

    </div>

</section>

<footer>
    <p>🎮 Qismət Games</p>
    <p>© 2026 Bütün hüquqlar qorunur.</p>
</footer>

<script>

function startGame(name) {
    alert("🎮 " + name + " seçildi! Oyun tezliklə başlayacaq.");
}

function searchGames() {

    let input =
        document.getElementById("search")
        .value
        .toLowerCase();

    let games =
        document.querySelectorAll(".game");

    games.forEach(function(game) {

        let text =
            game.innerText.toLowerCase();

        if (text.includes(input)) {
            game.style.display = "block";
        } else {
            game.style.display = "none";
        }

    });
}

</script>

</body>
</html>
"""

@app.route("/")
def home():
    return render_template_string(HTML)


if __name__ == "__main__":
    app.run(debug=True)
