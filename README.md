<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>Ma Valentine 💖</title>
<style>
    body {
        margin: 0;
        padding: 0;
        background: linear-gradient(135deg, #ff4f81, #ffb6c1);
        font-family: 'Comic Sans MS', cursive, sans-serif;
        overflow: hidden;
        text-align: center;
        color: white;
    }

    h1 {
        margin-top: 80px;
        font-size: 40px;
        text-shadow: 2px 2px 8px #ff1e62;
    }

    .container {
        margin-top: 100px;
        position: relative;
    }

    button {
        padding: 15px 35px;
        font-size: 20px;
        border: none;
        border-radius: 50px;
        cursor: pointer;
        transition: 0.3s;
        position: absolute;
    }

    #yesBtn {
        background-color: #ff1e62;
        color: white;
        left: 40%;
        transform: translateX(-50%);
    }

    #noBtn {
        background-color: white;
        color: #ff1e62;
        left: 60%;
        transform: translateX(-50%);
    }

    .heart {
        position: fixed;
        color: red;
        font-size: 20px;
        animation: float 3s linear infinite;
    }

    @keyframes float {
        0% { transform: translateY(0); opacity: 1; }
        100% { transform: translateY(-200px); opacity: 0; }
    }

    #message {
        display: none;
        font-size: 45px;
        margin-top: 200px;
        animation: pop 1s ease forwards;
    }

    @keyframes pop {
        0% { transform: scale(0); }
        100% { transform: scale(1); }
    }
</style>
</head>
<body>

<h1>💌 Veux-tu être ma valentine Ana ? 💖</h1>

<div class="container">
    <button id="yesBtn">Oui 💘</button>
    <button id="noBtn">Non 💔</button>
</div>

<div id="message">✨ Tu viens de faire de moi le plus heureux 💖✨</div>

<script>
const yesBtn = document.getElementById("yesBtn");
const noBtn = document.getElementById("noBtn");
const message = document.getElementById("message");

let yesSize = 20;

noBtn.addEventListener("mouseover", moveNoButton);
noBtn.addEventListener("click", moveNoButton);

function moveNoButton() {
    const x = Math.random() * (window.innerWidth - 100);
    const y = Math.random() * (window.innerHeight - 50);
    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";
}

yesBtn.addEventListener("click", function() {
    yesSize += 20;
    yesBtn.style.fontSize = yesSize + "px";
    yesBtn.style.padding = (yesSize/2) + "px " + (yesSize) + "px";
    
    if (yesSize > 80) {
        document.querySelector(".container").style.display = "none";
        message.style.display = "block";
        launchHearts();
    }
});

function launchHearts() {
    setInterval(() => {
        const heart = document.createElement("div");
        heart.classList.add("heart");
        heart.innerHTML = "💖";
        heart.style.left = Math.random() * window.innerWidth + "px";
        heart.style.bottom = "0px";
        heart.style.fontSize = (Math.random() * 30 + 10) + "px";
        document.body.appendChild(heart);

        setTimeout(() => {
            heart.remove();
        }, 3000);
    }, 200);
}
</script>

</body>
</html>
