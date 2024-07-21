<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Proposal Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f0f8ff;
            display: flex;
            flex-direction: column;
            justify-content: center;
            height: 100vh;
            margin: 0;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h1 {
            color: #ff69b4;
        }
        .buttons {
            margin-top: 20px;
        }
        .button {
            padding: 10px 20px;
            margin: 5px;
            border: none;
            border-radius: 5px;
            background-color: #ff69b4;
            color: white;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s;
        }
        .button:hover {
            background-color: #ff1493;
        }
        .button.no {
            position: relative;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Will you be my Valentine?</h1>
        <div class="buttons">
            <button class="button yes">Yes</button>
            <button class="button no" id="noButton">No</button>
        </div>
    </div>
    <script>
        const noButton = document.getElementById('noButton');

        noButton.addEventListener('mouseover', () => {
            const container = document.querySelector('.container');
            const containerRect = container.getBoundingClientRect();
            const buttonRect = noButton.getBoundingClientRect();
            
            let newLeft, newTop;

            do {
                newLeft = Math.random() * (containerRect.width - buttonRect.width);
                newTop = Math.random() * (containerRect.height - buttonRect.height);
            } while (
                newLeft < 0 || newTop < 0 ||
                newLeft + buttonRect.width > containerRect.width ||
                newTop + buttonRect.height > containerRect.height
            );

            noButton.style.position = 'absolute';
            noButton.style.left = `${newLeft}px`;
            noButton.style.top = `${newTop}px`;
        });

        document.querySelector('.yes').addEventListener('click', () => {
            alert('Yay! You accepted! ❤️');
        });
    </script>
</body>
</html>
