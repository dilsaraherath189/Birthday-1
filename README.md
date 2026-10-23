<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Akka 🎂🤍</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow-x: hidden;
    font-family: "Trebuchet MS", sans-serif;
    background: linear-gradient(135deg, #ffe0ed, #fff0f5, #fff4d9);
    color: #854c68;
    padding: 20px;
}

.container {
    width: 100%;
    max-width: 420px;
    text-align: center;
    padding: 30px 22px;
    border-radius: 30px;
    background: rgba(255,255,255,0.8);
    border: 2px solid white;
    box-shadow: 0 12px 40px rgba(206,111,157,0.18);
    position: relative;
    z-index: 2;
}

.top-decor {
    font-size: 28px;
    margin-bottom: 18px;
}

h1 {
    color: #e75491;
    font-size: 29px;
    margin: 12px 0;
}

.subtitle {
    font-size: 15px;
    line-height: 1.7;
    margin-bottom: 20px;
}

.gift {
    font-size: 105px;
    cursor: pointer;
    border: none;
    background: transparent;
    display: block;
    margin: 12px auto;
    animation: bounce 1.5s infinite;
}

.tap-text {
    font-size: 14px;
    color: #b66b91;
    animation: pulse 1.5s infinite;
}

#surprise {
    display: none;
    animation: appear 1s ease;
}

#surprise h1 {
    font-size: 32px;
    line-height: 1.4;
}

.wish {
    font-size: 17px;
    line-height: 1.9;
    margin: 22px 0;
    color: #79455f;
}

.sinhala {
    font-size: 19px;
    font-weight: bold;
    margin-top: 20px;
    color: #df528d;
}

.cake {
    font-size: 48px;
    margin: 15px 0;
}

.again {
    border: none;
    border-radius: 25px;
    background: #ed72a9;
    color: white;
    padding: 13px 22px;
    font-size: 15px;
    font-weight: bold;
    margin-top: 15px;
    cursor: pointer;
}

.footer {
    font-size: 12px;
    margin-top: 25px;
    color: #b27d98;
}

.heart, .confetti {
    position: fixed;
    pointer-events: none;
    z-index: 5;
}

.heart {
    bottom: -40px;
    animation: floatUp 5s linear forwards;
}

.confetti {
    top: -20px;
    animation: fall 3s linear forwards;
}

@keyframes bounce {
    0%,100% { transform: translateY(0) rotate(-3deg); }
    50% { transform: translateY(-12px) rotate(3deg); }
}

@keyframes pulse {
    0%,100% { opacity: 1; }
    50% { opacity: 0.55; }
}

@keyframes appear {
    from { opacity: 0; transform: translateY(20px) scale(.95); }
    to { opacity: 1; transform: translateY(0) scale(1); }
}

@keyframes floatUp {
    to { transform: translateY(-110vh) rotate(360deg); opacity: 0; }
}

@keyframes fall {
    to { transform: translateY(110vh) rotate(720deg); opacity: 0; }
}

@media (prefers-reduced-motion: reduce) {
    *, *::before, *::after {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
    }
}
</style>
</head>

<body>

<div class="container">

    <div class="top-decor">🎀 🤍 🎀</div>

    <div id="intro">
        <p class="subtitle">
            Someone has a little surprise for you... 🥹💗
        </p>

        <h1>Hey, Akka! 🎀</h1>

        <button class="gift" id="giftButton"
                aria-label="Open your birthday gift">
            🎁
        </button>

        <p class="tap-text">Tap the gift to open it! 👆💗</p>
    </div>

    <div id="surprise" aria-live="polite">

        <div class="cake">🎂🥳🤍</div>

        <h1>
            Happy birthday<br>
            akkaaa! 🥳🎂🤍
        </h1>

        <div class="wish">
            Wishing you endless happiness and success in every tiny bit of your life🥹🫶

            <div class="sinhala">
                හැමදාම හිනාවෙලා ඉන්න!!🤍
            </div>
        </div>

        <div style="font-size:29px;line-height:2;">
            🎉 💗 🌸 🧁 🦋 💝 🎈
        </div>

        <p class="subtitle">
            Hope your day is filled with happiness and beautiful memories! 🫶
        </p>

        <button class="again" id="againButton">
            Celebrate again! 🎉
        </button>

    </div>

    <div class="footer">
        A little birthday surprise made with 🤍
    </div>

</div>

<script>
const giftButton = document.getElementById("giftButton");
const intro = document.getElementById("intro");
const surprise = document.getElementById("surprise");
const againButton = document.getElementById("againButton");

function makeAnimation(items, className, count, duration) {
    for (let i = 0; i < count; i++) {
        setTimeout(() => {
            const item = document.createElement("div");
            item.className = className;
            item.textContent =
                items[Math.floor(Math.random() * items.length)];

            item.style.left = Math.random() * 100 + "vw";
            item.style.fontSize = (16 + Math.random() * 20) + "px";
            item.style.animationDuration =
                (duration + Math.random() * 2) + "s";

            document.body.appendChild(item);
            setTimeout(() => item.remove(), (duration + 3) * 1000);
        }, i * 70);
    }
}

function openGift() {
    intro.style.display = "none";
    surprise.style.display = "block";

    makeAnimation(
        ["💗", "💕", "🤍", "💖", "🎀", "🌸"],
        "heart", 22, 3
    );

    makeAnimation(
        ["🎉", "✨", "💗", "🎊", "🌸", "🤍"],
        "confetti", 35, 2
    );
}

function resetGift() {
    intro.style.display = "block";
    surprise.style.display = "none";
}

giftButton.addEventListener("click", openGift);
againButton.addEventListener("click", resetGift);
</script>

</body>
</html>
