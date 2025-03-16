<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>All Rounder - YouTube + Instagram Experience</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <link rel="icon" type="image/svg+xml" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><rect width='100' height='100' rx='15' fill='linear-gradient(45deg, #FF0101, #C13584, #FD1D1D)' /><path d='M50 10L65 40L50 70L35 40L50 10' fill='white' /><circle cx='20' cy='20' r='5' fill='white' /><path d='M15 15L25 25M25 15L15 25' stroke='white' stroke-width='2' /></svg>">
    <style>
        :root {
            --youtube-red: #FF0101;
            --instagram-gradient: linear-gradient(45deg, #FF0101, #C13584, #FD1D1D);
            --light-bg: #f8f9fa;
            --light-text: #333;
            --dark-bg: #121212;
            --dark-text: #ffffff;
            --card-bg: rgba(255, 255, 255, 0.1);
        }

        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            transition: background-color 0.3s, color 0.3s;
            background-color: var(--dark-bg);
            color: var(--dark-text);
        }

        .theme-toggle {
            position: fixed;
            top: 20px;
            right: 20px;
            z-index: 100;
            background: var(--card-bg);
            border: none;
            color: white;
            padding: 8px 16px;
            border-radius: 20px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .theme-toggle:hover {
            background-color: rgba(255, 255, 255, 0.2);
        }

        .hero {
            background: var(--instagram-gradient);
            padding: 4rem 2rem;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            animation: shine 3s infinite;
        }

        @keyframes shine {
            100% {
                left: 100%;
            }
        }

        .logo-container {
            max-width: 300px;
            margin: 0 auto 2rem;
        }

        .logo {
            width: 100%;
            height: auto;
        }

        .app-showcase {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            padding: 2rem;
        }

        .feature-card {
            background: var(--card-bg);
            border-radius: 15px;
            padding: 1.5rem;
            backdrop-filter: blur(10px);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
        }

        .download-section {
            text-align: center;
            padding: 3rem;
            background: rgba(0,0,0,0.3);
        }

        .download-btn {
            display: inline-block;
            padding: 12px 24px;
            margin: 1rem;
            border-radius: 30px;
            text-decoration: none;
            font-weight: bold;
            transition: transform 0.3s ease, opacity 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .download-btn::after {
            content: '';
            position: absolute;
            width: 0;
            height: 100%;
            background: var(--instagram-gradient);
            right: 0;
            top: 0;
            transition: width 0.5s ease;
        }

        .download-btn:hover::after {
            width: 100%;
            left: 0;
            right: auto;
        }

        .youtube-style {
            color: var(--youtube-red);
            border: 2px solid var(--youtube-red);
        }

        .youtube-style:hover {
            background: var(--youtube-red);
            color: white;
        }

        .instagram-style {
            background: var(--instagram-gradient);
        }

        .demo-section {
            padding: 4rem 2rem;
            text-align: center;
            background: rgba(255,255,255,0.05);
        }

        .video-container {
            max-width: 800px;
            margin: 0 auto;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
        }

        .video-placeholder {
            width: 100%;
            height: 450px;
            background: linear-gradient(45deg, #333, #666, #333);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 2rem;
        }

        .play-button {
            width: 80px;
            height: 80px;
            background: var(--youtube-red);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto;
            cursor: pointer;
            transition: transform 0.3s ease;
        }

        .play-button:hover {
            transform: scale(1.1);
        }

        .testimonials {
            padding: 4rem 2rem;
            background: var(--dark-bg);
        }

        .testimonial-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .testimonial-card {
            background: var(--card-bg);
            border-radius: 15px;
            padding: 2rem;
            transition: transform 0.3s ease;
        }

        .testimonial-card:hover {
            transform: translateY(-10px);
        }

        .testimonial-avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            margin-bottom: 1rem;
            background: var(--youtube-red);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
        }

        .social-proof {
            padding: 4rem 2rem;
            text-align: center;
            background: rgba(255,255,255,0.05);
        }

        .counters {
            display: flex;
            justify-content: center;
            gap: 4rem;
            margin-top: 2rem;
        }

        .counter {
            text-align: center;
        }

        .counter-number {
            font-size: 3rem;
            font-weight: bold;
            color: var(--youtube-red);
        }

        .counter-label {
            color: #aaa;
        }

        @media (max-width: 768px) {
            .counters {
                flex-direction: column;
                gap: 2rem;
            }
        }

        .footer {
            text-align: center;
            padding: 2rem;
            background: rgba(0,0,0,0.3);
        }

        .animated-text {
            display: inline-block;
            position: relative;
            overflow: hidden;
        }

        .animated-text span {
            animation: typing 3s steps(40, end), blink-caret 0.5s step-end infinite;
            white-space: nowrap;
            margin-right: 5px;
            opacity: 0;
        }

        @keyframes typing {
            from { width: 0 }
            to { width: 100% }
        }

        @keyframes blink-caret {
            from, to { border-color: transparent }
            50% { border-color: white }
        }
    </style>
</head>
<body>
    <button class="theme-toggle" id="theme-toggle">
        <i class="fas fa-moon"></i> Light Mode
    </button>

    <section class="hero">
        <div class="logo-container">
            <svg class="logo" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 300 300">
                <rect width="300" height="300" rx="30" fill="linear-gradient(45deg, #FF0101, #C13584, #FD1D1D)" />
                <rect x="50" y="50" width="200" height="200" rx="25" fill="white" />
                <path d="M150 60L185 100L150 140L115 100L150 60" fill="#FF0101" />
                <circle cx="70" cy="70" r="15" fill="white" />
                <path d="M60 60L80 80M80 60L60 80" stroke="white" stroke-width="3" />
            </svg>
        </div>
        <h1>All Rounder</h1>
        <p class="animated-text"><span>The Ultimate Social Video Experience</span></p>
        <p>Combining the best of YouTube and Instagram</p>
    </section>

    <section class="app-showcase">
        <div class="feature-card">
            <h2>YouTube Features</h2>
            <ul>
                <li>Long-form video uploads</li>
                <li>Comment sections</li>
                <li>Subscriptions</li>
                <li>Playlists</li>
                <li>Video recommendations</li>
            </ul>
        </div>

        <div class="feature-card">
            <h2>Instagram Features</h2>
            <ul>
                <li>Stories & Reels</li>
                <li>Photo grid profile</li>
                <li>Direct messaging</li>
                <li>Explore page</li>
                <li>Filters & AR effects</li>
            </ul>
        </div>

        <div class="feature-card">
            <h2>Unique Combination</h2>
            <ul>
                <li>Vertical video support</li>
                <li>24-hour story highlights</li>
                <li>Channel subscriptions with story integration</li>
                <li>Unified notification system</li>
                <li>Cross-platform sharing</li>
            </ul>
        </div>
    </section>

    <section class="demo-section">
        <h2>See All Rounder in Action</h2>
        <p>Watch this quick demo to experience the power of combined social video platforms</p>
        <div class="video-container">
            <div class="video-placeholder">
                <div class="play-button">
                    <i class="fas fa-play"></i>
                </div>
            </div>
        </div>
    </section>

    <section class="testimonials">
        <h2>What Our Users Say</h2>
        <div class="testimonial-grid">
            <div class="testimonial-card">
                <div class="testimonial-avatar">J</div>
                <p>"All Rounder changed my content creation game. I love having both YouTube and Instagram features in one place!"</p>
                <p><strong>- Jane D., Content Creator</strong></p>
            </div>

            <div class="testimonial-card">
                <div class="testimonial-avatar">M</div>
                <p>"This app is amazing! The combination of long-form content and short reels makes my social media management so much easier."</p>
                <p><strong>- Mark R., Influencer</strong></p>
            </div>

            <div class="testimonial-card">
                <div class="testimonial-avatar">S</div>
                <p>"I've been waiting for an app like this for years. The integration between YouTube and Instagram features is seamless and intuitive."</p>
                <p><strong>- Sarah K., Digital Marketer</strong></p>
            </div>
        </div>
    </section>

    <section class="social-proof">
        <h2>Join Millions of Creators Worldwide</h2>
        <div class="counters">
            <div class="counter">
                <div class="counter-number" id="users-counter">12,5M+</div>
                <div class="counter-label">Happy Users</div>
            </div>
            <div class="counter">
                <div class="counter-number" id="videos-counter">350M+</div>
                <div class="counter-label">Videos Uploaded</div>
            </div>
        </div>
    </section>

    <section class="download-section">
        <h2>Experience the Future of Social Video</h2>
        <a href="#" class="download-btn youtube-style">Download for iOS</a>
        <a href="#" class="download-btn instagram-style">Download for Android</a>
    </section>

    <footer class="footer">
        <p>&copy; 2023 All Rounder. All rights reserved.</p>
    </footer>

    <script>
        // Theme toggle functionality
        const themeToggle = document.getElementById('theme-toggle');
        themeToggle.addEventListener('click', () => {
            if (document.body.style.backgroundColor === 'var(--light-bg)') {
                document.body.style.backgroundColor = 'var(--dark-bg)';
                document.body.style.color = 'var(--dark-text)';
                document.documentElement.style.setProperty('--card-bg', 'rgba(255, 255, 255, 0.1)');
                themeToggle.innerHTML = '<i class="fas fa-moon"></i> Light Mode';
            } else {
                document.body.style.backgroundColor = 'var(--light-bg)';
                document.body.style.color = 'var(--light-text)';
                document.documentElement.style.setProperty('--card-bg', 'rgba(0, 0, 0, 0.05)');
                themeToggle.innerHTML = '<i class="fas fa-sun"></i> Dark Mode';
            }
        });

        // Animation for text
        document.addEventListener('DOMContentLoaded', () => {
            const animatedText = document.querySelector('.animated-text span');
            setTimeout(() => {
                animatedText.style.opacity = '1';
            }, 500);
        });

        // Counter animation
        const usersCounter = document.getElementById('users-counter');
        const videosCounter = document.getElementById('videos-counter');

        function animateCounters() {
            let usersCount = 0;
            let videosCount = 0;
            const usersTarget = parseInt(usersCounter.textContent.replace(/,/g, '').replace('M+', ''));
            const videosTarget = parseInt(videosCounter.textContent.replace(/,/g, '').replace('M+', ''));

            const usersInterval = setInterval(() => {
                usersCount += Math.ceil(usersTarget / 100);
                if (usersCount >= usersTarget) {
                    usersCount = usersTarget;
                    clearInterval(usersInterval);
                }
                usersCounter.textContent = usersCount.toLocaleString() + '+';
            }, 20);

            const videosInterval = setInterval(() => {
                videosCount += Math.ceil(videosTarget / 100);
                if (videosCount >= videosTarget) {
                    videosCount = videosTarget;
                    clearInterval(videosInterval);
                }
                videosCounter.textContent = videosCount.toLocaleString() + '+';
            }, 15);
        }

        // Trigger counter animation when section is visible
        const socialProofSection = document.querySelector('.social-proof');
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    animateCounters();
                    observer.unobserve(socialProofSection);
                }
            });
        });

        observer.observe(socialProofSection);
    </script>
</body>
</html>
