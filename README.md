# GalacticMemories.github.io
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Galactic Memories</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&family=Cinzel:wght@700&display=swap" rel="stylesheet">
    <style>
        body {
            margin: 0;
            font-family: 'Roboto', sans-serif;
            color: white;
            background: url('https://www.wallpaperflare.com/static/87/981/130/space-planet-universe-galaxy-wallpaper.jpg') no-repeat center center fixed;
            background-size: cover;
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }
        header {
            background: rgba(0, 0, 0, 0.7);
            padding: 1rem;
            position: fixed;
            width: 100%;
            top: 0;
            left: 0;
            z-index: 1000;
            transition: top 0.3s;
        }
        .header-hidden {
            top: -80px;
        }
        nav ul {
            list-style: none;
            display: flex;
            justify-content: space-around;
            padding: 0;
            margin: 0;
        }
        nav a {
            color: white;
            text-decoration: none;
            font-size: 1.2rem;
            font-family: 'Cinzel', serif;
            transition: color 0.3s;
        }
        nav a:hover {
            color: #FFD700;
        }
        .hero {
            text-align: center;
            padding: 6rem 1rem;
            background: rgba(0, 0, 0, 0.5);
            margin-top: 4rem;
        }
        .hero h1 {
            font-size: 3rem;
            margin: 0;
            font-family: 'Cinzel', serif;
        }
        footer {
            background: rgba(0, 0, 0, 0.8);
            color: white;
            text-align: center;
            padding: 1rem;
            position: absolute;
            bottom: 0;
            width: 100%;
        }
        footer a {
            color: white;
            text-decoration: none;
        }
        footer a:hover {
            color: #FFD700;
        }
        .toggle-button {
            position: fixed;
            top: 10px;
            left: 10px;
            background: transparent;
            border: none;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <header id="main-header">
        <nav>
            <ul>
                <li><a href="photos.html">Photos</a></li>
                <li><a href="albums.html">Albums</a></li>
                <li><a href="upload.html">Upload</a></li>
                <li><a href="account.html">Account</a></li>
            </ul>
        </nav>
    </header>
    <button class="toggle-button" onclick="toggleHeader()">&#9728;</button>
    <main>
        <section class="hero">
            <h1>Store and organize your intergalactic memories</h1>
        </section>
    </main>
    <footer>
        <a href="#" onclick="promptAdminPassword()">Made by Daddy</a>
    </footer>
    <script>
        let lastScrollY = window.scrollY;
        const header = document.getElementById('main-header');

        window.addEventListener('scroll', () => {
            if (window.scrollY > lastScrollY) {
                header.classList.add('header-hidden');
            } else {
                header.classList.remove('header-hidden');
            }
            lastScrollY = window.scrollY;
        });

        function toggleHeader() {
            header.classList.toggle('header-hidden');
        }

        function promptAdminPassword() {
            const password = prompt('Enter admin password:');
            if (password === 'admin123') {
                alert('Access granted!');
            } else {
                alert('Access denied!');
            }
        }
    </script>
</body>
</html>
