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
            display: flex;
            flex-direction: column;
            min-height: 100vh;
            background: url('https://www.wallpaperflare.com/static/87/981/130/space-planet-universe-galaxy-wallpaper.jpg') no-repeat center center fixed;
            background-size: cover;
        }
        header {
            background: rgba(0, 0, 0, 0.7);
            padding: 1rem;
            position: fixed;
            width: 100%;
            top: 0;
            left: 0;
            z-index: 1000;
        }
        nav ul {
            list-style: none;
            display: flex;
            justify-content: space-around;
            padding: 0;
            margin: 0;
            width: 100%;
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
        .menu-toggle {
            display: none;
            cursor: pointer;
            font-size: 1.5rem;
            background: none;
            border: none;
            color: white;
            padding: 0.5rem 1rem;
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
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        footer a {
            color: white;
            text-decoration: none;
            font-size: 1.5rem;
        }
        footer a:hover {
            color: #FFD700;
        }
        @media only screen and (max-width: 768px) {
            nav ul {
                flex-direction: column;
                display: none;
            }
            nav ul.active {
                display: flex;
            }
            .menu-toggle {
                display: block;
            }
            .hero h1 {
                font-size: 2rem;
            }
        }
        #admin-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            justify-content: center;
            align-items: center;
            z-index: 1001;
        }
        #admin-modal.active {
            display: flex;
        }
        #admin-modal-content {
            background: url('https://www.wallpaperflare.com/static/482/355/749/galaxy-stars-astronomy-space-wallpaper.jpg') no-repeat center center;
            background-size: cover;
            padding: 2rem;
            text-align: center;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.5);
            color: white;
        }
        #admin-modal-content input {
            padding: 0.5rem;
            margin: 0.5rem 0;
            width: 100%;
            border: none;
            border-radius: 4px;
        }
        #admin-modal-content button {
            padding: 0.5rem 1rem;
            background: #FFD700;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        #admin-modal-content button:hover {
            background: #FFC107;
        }
    </style>
</head>
<body>
    <header>
        <nav>
            <button class="menu-toggle" onclick="toggleMenu()">☰</button>
            <ul id="menu">
                <li><a href="#explore">Explore</a></li>
                <li><a href="#albums">Albums</a></li>
                <li><a href="#search">Search</a></li>
                <li><a href="#share">Share</a></li>
                <li><a href="#account">Account</a></li>
                <li><a href="#face-recognition">Face Recognition</a></li>
                <li><a href="#photo-editing">Photo Editing</a></li>
                <li><a href="#slideshow">Slideshow</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section class="hero">
            <h1>Store and organize your intergalactic memories</h1>
        </section>
        <!-- Add content sections here -->
    </main>

    <footer>
        <a href="#" id="admin-link" onclick="showAdminModal()">Made by Daddy</a>
    </footer>

    <div id="admin-modal">
        <div id="admin-modal-content">
            <h2>Enter Admin Password</h2>
            <input type="password" id="admin-password" placeholder="Password">
            <button onclick="checkAdminPassword()">Submit</button>
            <button onclick="closeAdminModal()">Cancel</button>
        </div>
    </div>

    <script>
        function toggleMenu() {
            const menu = document.getElementById('menu');
            menu.classList.toggle('active');
        }

        function showAdminModal() {
            const modal = document.getElementById('admin-modal');
            modal.classList.add('active');
        }

        function closeAdminModal() {
            const modal = document.getElementById('admin-modal');
            modal.classList.remove('active');
        }

        function checkAdminPassword() {
            const password = document.getElementById('admin-password').value;
            if (password === 'admin123') {
                window.location.href = 'admin-login.html';
            } else {
                alert('Incorrect password!');
            }
        }
    </script>
</body>
</html>
