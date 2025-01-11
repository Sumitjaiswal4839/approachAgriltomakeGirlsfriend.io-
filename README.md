<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Approach a Girl</title>
    <style>
        body {
            background-color: rgb(210, 36, 213);
            font-family: Algerian, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 95vh;
        }

        .container {
            position: relative;
            max-width: 90%;
            width: 600px;
            text-align: center;
            overflow: hidden;
        }

        .media-container {
            position: relative;
            width: 100%;
        }

        .media {
            width: 100%;
            height: auto;
            display: block;
            border-radius: 15px;
            max-height: 500px;
            object-fit: contain;
        }

        .overlay-text {
            position: absolute;
            bottom: 50px;
            left: 50%;
            transform: translateX(-50%);
            color: white;
            font-family: Algerian, Arial, sans-serif;
            font-size: 16px;
            text-align: center;
            background-color: rgba(0, 0, 0, 0.5);
            padding: 10px;
            border-radius: 8px;
        }
        
        .action-button {
            background-color: rgba(0, 0, 0, 0.7);
            color: white;
            border: none;
            padding: 10px 20px;
            cursor: pointer;
            font-size: 16px;
            border-radius: 5px;
            transition: background-color 0.3s;
            margin-top: 10px;
        }

        .action-button:hover {
            background-color: rgba(255, 255, 255, 0.9);
            color: black;
        }

        video {
            width: 100%;
            height: auto;
            max-height: 500px;
            object-fit: contain;
            border-radius: 15px;
            display: none;
        }

    </style>
</head>
<body>
    <div class="container">
        <div class="media-container">
            <img id="currentImage" class="media" src="images/heart.png" alt="current media">
            <video id="currentVideo" class="media" controls>
                <source id="videoSource" src="" type="video/mp4">
                Your browser does not support the video tag.
            </video>
            <div class="overlay-text" id="overlayText">This is something special for you ❤️</div>
            <button id="actionButton" class="action-button">Kya</button>
        </div>
    </div>

    <script>
        const media = [
            { type: "image", url: "images/heart.png", text: "This 🕵️‍♂️is something special for you ❤️😍😘🥰🥰😍😘", buttonText: "Kya" },
            { type: "image", url: "images/aayen.jpg", text: "Wait ✋kro thoda saa yaar baata hun? ❤️", buttonText: "Ok" },
            { type: "image", url: "images/ruk ja.webp", text: "Are toh ruk bhi 👌jaao itni jaldi bhi kya hai? ❤️", buttonText: "Thik hai" },
            { type: "image", url: "images/angry.webp", text: "Okk thik hai smajh🙌 gya gussa aa rha hai ? ❤️", buttonText: "Jyada nhi hoo gya" },
            { type: "image", url: "images/angry2.jpg", text: "Thik hai bta rha hun ruk jao  ? ❤️", buttonText: "Jyada nhi hoo rha hai ab" },
            { type: "image", url: "images/funnyboy.png", text: "Yeh last hai pkkaa thik check kro ab👍  ? ❤️", buttonText: "Pccua" },
            { type: "video", url: "images/video.mp4", text: " ", buttonText: "acha ji" },
            { type: "image", url: "images/di2.jpg", text: "Na mat bolna please🙏🙏 na  mat bolna 😥😥🙄😭😭? ❤️", buttonText: "nhi" },
            { type: "image", url: "images/di4.png", text: "yha tak aaye ho mtlb ha 😁😁hai please maan jaao 😍", buttonText: "nhi" },
            { type: "image", url: "images/di5.jpg", text: " 🥰", buttonText: "okk" },
        ];

        let currentIndex = 0;
        const imageElement = document.getElementById("currentImage");
        const videoElement = document.getElementById("currentVideo");
        const videoSource = document.getElementById("videoSource");
        const overlayElement = document.getElementById("overlayText");
        const actionButton = document.getElementById("actionButton");

        const audio = new Audio('romantic-music.mp3');
        audio.loop = true;
        audio.play();

        function updateMedia() {
            const currentMedia = media[currentIndex];
            if (currentMedia.type === "video") {
                imageElement.style.display = 'none';
                videoSource.src = currentMedia.url;
                videoElement.style.display = 'block';
                videoElement.load();
                videoElement.play();
            } else {
                videoElement.style.display = 'none';
                imageElement.style.display = 'block';
                imageElement.src = currentMedia.url;
            }
            overlayElement.textContent = currentMedia.text;
            actionButton.textContent = currentMedia.buttonText;

            if (currentIndex === media.length - 1) {
                actionButton.onclick = () => {
                    window.open("https://wa.me/?text=Okk%20I%20love%20you", "_blank");
                };
            } else {
                actionButton.onclick = () => {
                    currentIndex = (currentIndex + 1) % media.length;
                    updateMedia();
                };
            }
        }

        updateMedia();
    </script>
</body>
</html>