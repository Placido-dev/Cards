# HTML:

<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Carrossel de Cards</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="carousel-container">
        <button class="prev-btn" onclick="prevCard()">&#10094;</button>
        <div class="card-container">
            <div class="card">
                <div class="card-frente">Frente (Front) 1</div>
                <div class="card-verso">Verso (Back) 1</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 2</div>
                <div class="card-verso">Verso (Back) 2</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 3</div>
                <div class="card-verso">Verso (Back) 3</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 4</div>
                <div class="card-verso">Verso (Back) 4</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 5</div>
                <div class="card-verso">Verso (Back) 5</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 6</div>
                <div class="card-verso">Verso (Back) 6</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 7</div>
                <div class="card-verso">Verso (Back) 7</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 8</div>
                <div class="card-verso">Verso (Back) 8</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 9</div>
                <div class="card-verso">Verso (Back) 9</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 10</div>
                <div class="card-verso">Verso (Back) 10</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 11</div>
                <div class="card-verso">Verso (Back) 11</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 12</div>
                <div class="card-verso">Verso (Back) 12</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 13</div>
                <div class="card-verso">Verso (Back) 13</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 14</div>
                <div class="card-verso">Verso (Back) 14</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 15</div>
                <div class="card-verso">Verso (Back) 15</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 16</div>
                <div class="card-verso">Verso (Back) 16</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 17</div>
                <div class="card-verso">Verso (Back) 17</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 18</div>
                <div class="card-verso">Verso (Back) 18</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 19</div>
                <div class="card-verso">Verso (Back) 19</div>
            </div>
            <div class="card">
                <div class="card-frente">Frente (Front) 20</div>
                <div class="card-verso">Verso (Back) 20</div>
            </div>
        </div>
        <button class="next-btn" onclick="nextCard()">&#10095;</button>
    </div>

    <script src="script.js"></script>
</body>
</html>

# CSS:

body {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #868484;
    margin: 0;
    font-family: Arial, sans-serif;
}

.carousel-container {
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    width: 20rem;
}

.card-container {
    width: 15rem;
    height: 20rem;
    display: flex;
    overflow: hidden;
    position: relative;
}

.card {
    min-width: 100%;
    transition: transform 0.5s ease-in-out;
    position: absolute;
    cursor: pointer;
}

.card-frente,
.card-verso {
    height: 20rem;
    border-radius: 20px;
    transition: all 0.9s ease;
    backface-visibility: hidden;
    position: absolute;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    width: 95%;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
}


.card-frente {
    background-image: linear-gradient(to right top, #8a0df0, #dceb0f);
}

.card-verso {
    transform: rotateY(-180deg);
    background-image: linear-gradient(to right top, #dceb0f, #8a0df0);
}

.card:hover .card-frente {
    transform: rotateY(180deg);
}

.card:hover .card-verso {
    transform: rotateY(0deg);
}

.prev-btn,
.next-btn {
    background-color: transparent;
    border: none;
    color: white;
    padding: 10px;
    cursor: pointer;
    margin: 0 10px;
    border-radius: 5px;
    font-size: 1rem;
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
}

.prev-btn {
    left: -2rem;
}

.next-btn {
    right: -2rem;
}

# JS:

let currentCardIndex = 0;

function showCard(index) {
    const cards = document.querySelectorAll('.card');
    if (index >= cards.length) {
        currentCardIndex = 0;
    } else if (index < 0) {
        currentCardIndex = cards.length - 1;
    } else {
        currentCardIndex = index;
    }
    cards.forEach((card, idx) => {
        card.style.transform = `translateX(${(idx - currentCardIndex) * 100}%)`;
    });
}

function nextCard() {
    showCard(currentCardIndex + 1);
}

function prevCard() {
    showCard(currentCardIndex - 1);
}

showCard(currentCardIndex);
