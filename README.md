# GalacticMemories.github.io
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Digital HunterZ</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <header>
            <nav>
                <ul>
                    <li><a href="#explore">Explore</a></li>
                    <li><a href="#albums">Albums</a></li>
                    <li><a href="#search">Search</a></li>
                    <li><a href="#share">Share</a></li>
                </ul>
            </nav>
        </header>
        <main>
            <section id="hero">
                <h1>Store and organize your intergalactic memories</h1>
                <button id="signUpBtn">Sign Up</button>
            </section>
            <section id="features">
                <div class="feature">
                    <img src="spaceship.jpg" alt="Automatic Categorization">
                    <h2>Automatic Categorization</h2>
                    <p>Let our AI-powered categorization system organize your photos into albums, people, places, and things.</p>
                </div>
                <div class="feature">
                    <img src="astronaut.jpg" alt="AI-Powered Search">
                    <h2>AI-Powered Search</h2>
                    <p>Find your photos quickly with our AI-powered search engine, which recognizes objects, scenes, and actions.</p>
                </div>
                <div class="feature">
                    <img src="spaceships.jpg" alt="Sharing and Collaboration">
                    <h2>Sharing and Collaboration</h2>
                    <p>Share your photos and albums with friends and family, and collaborate on shared libraries.</p>
                </div>
            </section>
        </main>
        <footer>
            <p>Made by Daddy</p>
        </footer>
    </div>
    <script src="scripts.js"></script>
</body>
</html>
body {
    background-image: url('galaxy.jpg');
    color: white;
    font-family: 'Arial', sans-serif;
    margin: 0;
    padding: 0;
}

.container {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
}

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

nav ul {
    list-style: none;
    display: flex;
    gap: 20px;
}

nav a {
    color: white;
    text-decoration: none;
}

#hero {
    text-align: center;
    margin-top: 50px;
}

#features {
    display: flex;
    justify-content: space-around;
    margin-top: 50px;
}

.feature {
    text-align: center;
}

.feature img {
    width: 100px;
    height: 100px;
}

footer {
    text-align: center;
    margin-top: 50px;
}
const express = require('express');
const admin = require('firebase-admin');
const bodyParser = require('body-parser');
const app = express();
const port = 3000;

const serviceAccount = require('./path/to/serviceAccountKey.json');

admin.initializeApp({
    credential: admin.credential.cert(serviceAccount),
    storageBucket: 'your-firebase-storage-bucket'
});

const db = admin.firestore();
const bucket = admin.storage().bucket();

app.use(bodyParser.json());
app.use(express.static('public'));

app.post('/upload', (req, res) => {
    const { file, userId } = req.body;
    const fileName = `${userId}/${file.name}`;
    const fileBuffer = Buffer.from(file.data, 'base64');

    const fileUpload = bucket.file(fileName);
    const stream = fileUpload.createWriteStream({
        metadata: {
            contentType: file.type
        }
    });

    stream.on('error', (err) => {
        res.status(500).send(err);
    });

    stream.on('finish', () => {
        fileUpload.getSignedUrl({
            action: 'read',
            expires: '03-01-2500'
        }).then((url) => {
            db.collection('users').doc(userId).collection('files').add({
                name: file.name,
                url: url[0]
            }).then(() => {
                res.status(200).send('File uploaded successfully');
            }).catch((err) => {
                res.status(500).send(err);
            });
        });
    });

    stream.end(fileBuffer);
});

app.listen(port, () => {
    console.log(`Server running at http://localhost:${port}`);
});
