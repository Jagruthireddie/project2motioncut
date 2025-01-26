<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Innovative Image Slider</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
        }

        .slider-container {
            position: relative;
            width: 100%;
            height: 100vh;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .slider {
            position: relative;
            width: 100%;
            height: 100%;
        }

        .slide {
            position: absolute;
            width: 100vw;
            height: 100vh;
            opacity: 0;
            transition: opacity 1.5s ease-in-out, transform 1.5s ease;
        }

        .slide.active {
            opacity: 1;
            transform: scale(1.05);
            box-shadow: 0 0 30px rgba(0, 0, 0, 0.5);
        }

        .slide img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 10px;
            transition: transform 0.5s ease-in-out;
        }

        .slide img:hover {
            transform: scale(1.1);
        }

        .slide-text {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            color: white;
            font-size: 40px;
            font-weight: bold;
            text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.7);
        }

        .arrow {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(0,0,0,0.5);
            color: white;
            border: none;
            padding: 15px;
            cursor: pointer;
            font-size: 30px;
            border-radius: 50%;
            z-index: 10;
        }

        .arrow:hover {
            background: rgba(0, 0, 0, 0.8);
        }

        .arrow.left {
            left: 10px;
        }

        .arrow.right {
            right: 10px;
        }

        @media (max-width: 768px) {
            .arrow {
                font-size: 24px;
                padding: 12px;
            }
        }

        @media (max-width: 480px) {
            .arrow {
                font-size: 20px;
                padding: 10px;
            }
        }

    </style>
</head>
<body>

    <div class="slider-container">
        <div class="slider">
            <div class="slide active">
                <img src="https://i.pinimg.com/736x/9f/38/53/9f385384cf86350110d2d0029a0dcc15.jpg" alt="Image 1">
                <div class="slide-text"><i><b>Majestic Nature</b></i></div>
            </div>
            <div class="slide">
                <img src="https://wallpapers.com/images/hd/kayak-boat-full-screen-hd-desktop-0mr2y1jsnimnbjin.jpg" alt="Image 2">
            </div>
            <div class="slide">
                <img src="https://w0.peakpx.com/wallpaper/816/231/HD-wallpaper-beautiful-full-screen-beautiful-full-screen-use.jpg" alt="Image 3">
            </div>
        </div>

        <button class="arrow left" onclick="prevSlide()">&#10094;</button>
        <button class="arrow right" onclick="nextSlide()">&#10095;</button>
    </div>

    <script>
        let index = 0;
        const slides = document.querySelectorAll('.slide');

        function showSlide() {
            slides.forEach((slide, i) => {
                slide.classList.remove('active');
                if (i === index) {
                    slide.classList.add('active');
                }
            });
        }

        function nextSlide() {
            index = (index < slides.length - 1) ? index + 1 : 0;
            showSlide();
        }

        function prevSlide() {
            index = (index > 0) ? index - 1 : slides.length - 1;
            showSlide();
        }

        setInterval(() => {
            nextSlide();
        }, 5000);

        showSlide();
    </script>

</body>
</html>
