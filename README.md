<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Welcome to Panku World</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'JetBrains Mono', 'Courier New', monospace;
            background: linear-gradient(135deg, #0f0f23 0%, #1a1a2e 50%, #16213e 100%);
            color: #00f7ff;
            overflow: hidden;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .intro-container {
            width: 100%;
            height: 100%;
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Animated Background */
        .bg-animation {
            position: absolute;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: 1;
        }

        .bg-animation::before {
            content: '';
            position: absolute;
            width: 200%;
            height: 200%;
            background: 
                radial-gradient(circle at 20% 20%, rgba(0, 247, 255, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 80% 80%, rgba(255, 0, 128, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 40% 60%, rgba(0, 255, 128, 0.1) 0%, transparent 50%);
            animation: bgRotate 20s linear infinite;
        }

        @keyframes bgRotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Floating Elements */
        .floating-elements {
            position: absolute;
            width: 100%;
            height: 100%;
            z-index: 2;
        }

        .floating-icon {
            position: absolute;
            font-size: 2rem;
            opacity: 0.3;
            animation: float 6s ease-in-out infinite;
        }

        .floating-icon:nth-child(1) { top: 10%; left: 10%; animation-delay: 0s; }
        .floating-icon:nth-child(2) { top: 20%; right: 15%; animation-delay: 1s; }
        .floating-icon:nth-child(3) { bottom: 20%; left: 20%; animation-delay: 2s; }
        .floating-icon:nth-child(4) { bottom: 10%; right: 10%; animation-delay: 3s; }
        .floating-icon:nth-child(5) { top: 50%; left: 5%; animation-delay: 4s; }
        .floating-icon:nth-child(6) { top: 40%; right: 5%; animation-delay: 5s; }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(180deg); }
        }

        /* Main Content */
        .content {
            position: relative;
            z-index: 10;
            text-align: center;
            max-width: 800px;
            width: 90%;
        }

        /* Scene Transitions */
        .scene {
            position: absolute;
            width: 100%;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            opacity: 0;
            transform: scale(0.8);
            transition: all 1s ease;
        }

        .scene.active {
            opacity: 1;
            transform: scale(1);
        }

        /* Scene 1: Welcome */
        .welcome-title {
            font-size: 4rem;
            font-weight: bold;
            background: linear-gradient(45deg, #00f7ff, #ff0080, #00ff80, #ff8000);
            background-size: 400% 400%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradientShift 3s ease-in-out infinite;
            margin-bottom: 2rem;
        }

        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        .welcome-subtitle {
            font-size: 1.5rem;
            margin-bottom: 3rem;
            opacity: 0.8;
        }

        /* Scene 2: Student Avatar */
        .student-avatar {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
        }

        .avatar-circle {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            background: linear-gradient(135deg, #00f7ff, #ff0080);
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 2rem;
            animation: pulse 2s ease-in-out infinite;
            position: relative;
        }

        .avatar-circle::before {
            content: '👨‍💻';
            font-size: 5rem;
            animation: bounce 2s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); box-shadow: 0 0 0 0 rgba(0, 247, 255, 0.7); }
            50% { transform: scale(1.05); box-shadow: 0 0 0 20px rgba(0, 247, 255, 0); }
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        .student-title {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            color: #00f7ff;
        }

        .student-subtitle {
            font-size: 1.2rem;
            color: #ff0080;
        }

        /* Scene 3: AI Activities */
        .ai-activities {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 2rem;
            width: 100%;
            max-width: 600px;
        }

        .activity-card {
            background: rgba(0, 247, 255, 0.1);
            border: 2px solid #00f7ff;
            border-radius: 15px;
            padding: 2rem;
            text-align: center;
            transition: all 0.3s ease;
            animation: slideInUp 0.5s ease forwards;
            opacity: 0;
            transform: translateY(50px);
        }

        .activity-card:nth-child(1) { animation-delay: 0.2s; }
        .activity-card:nth-child(2) { animation-delay: 0.4s; }
        .activity-card:nth-child(3) { animation-delay: 0.6s; }

        @keyframes slideInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .activity-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
            display: block;
        }

        .activity-title {
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
            color: #00f7ff;
        }

        .activity-desc {
            font-size: 0.9rem;
            opacity: 0.8;
        }

        /* Scene 4: Final Logo */
        .final-logo {
            text-align: center;
        }

        .logo-main {
            font-size: 3.5rem;
            font-weight: bold;
            background: linear-gradient(45deg, #00f7ff, #ff0080);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 1rem;
            animation: glow 2s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from { text-shadow: 0 0 10px #00f7ff; }
            to { text-shadow: 0 0 20px #ff0080, 0 0 30px #00f7ff; }
        }

        .logo-subtitle {
            font-size: 1.5rem;
            color: #ff0080;
            margin-bottom: 2rem;
        }

        .tech-background {
            position: absolute;
            width: 100%;
            height: 100%;
            background: 
                linear-gradient(45deg, transparent 49%, rgba(0, 247, 255, 0.1) 50%, transparent 51%),
                linear-gradient(-45deg, transparent 49%, rgba(255, 0, 128, 0.1) 50%, transparent 51%);
            background-size: 20px 20px;
            animation: techMove 4s linear infinite;
        }

        @keyframes techMove {
            0% { background-position: 0 0; }
            100% { background-position: 20px 20px; }
        }

        /* Control Buttons */
        .controls {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 100;
            display: flex;
            gap: 10px;
        }

        .control-btn {
            background: rgba(0, 247, 255, 0.2);
            border: 2px solid #00f7ff;
            color: #00f7ff;
            padding: 10px 20px;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-family: inherit;
        }

        .control-btn:hover {
            background: rgba(0, 247, 255, 0.3);
            transform: translateY(-2px);
        }

        /* Progress Bar */
        .progress-bar {
            position: fixed;
            bottom: 0;
            left: 0;
            height: 4px;
            background: linear-gradient(90deg, #00f7ff, #ff0080);
            transition: width 1s ease;
            z-index: 100;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .welcome-title {
                font-size: 2.5rem;
            }
            
            .ai-activities {
                grid-template-columns: 1fr;
                gap: 1rem;
            }
            
            .activity-card {
                padding: 1.5rem;
            }
            
            .avatar-circle {
                width: 150px;
                height: 150px;
            }
            
            .avatar-circle::before {
                font-size: 3rem;
            }
        }
    </style>
</head>
<body>
    <!-- Animated Background -->
    <div class="bg-animation"></div>
    
    <!-- Floating Elements -->
    <div class="floating-elements">
        <div class="floating-icon">💻</div>
        <div class="floating-icon">🤖</div>
        <div class="floating-icon">📊</div>
        <div class="floating-icon">🛡️</div>
        <div class="floating-icon">⚡</div>
        <div class="floating-icon">🔬</div>
    </div>

    <div class="intro-container">
        <!-- Scene 1: Welcome -->
        <div class="scene active" id="scene1">
            <div class="content">
                <h1 class="welcome-title">Welcome to</h1>
                <h2 class="welcome-title">Panku World</h2>
                <p class="welcome-subtitle">Where AI meets Innovation</p>
            </div>
        </div>

        <!-- Scene 2: Student Avatar -->
        <div class="scene" id="scene2">
            <div class="content">
                <div class="student-avatar">
                    <div class="avatar-circle"></div>
                    <h2 class="student-title">Data Science Learner</h2>
                    <p class="student-subtitle">Young • Passionate • AI-Powered</p>
                </div>
            </div>
        </div>

        <!-- Scene 3: AI Activities -->
        <div class="scene" id="scene3">
            <div class="content">
                <div class="ai-activities">
                    <div class="activity-card">
                        <span class="activity-icon">📝</span>
                        <h3 class="activity-title">AI Blog Writing</h3>
                        <p class="activity-desc">Creating engaging content with AI assistance</p>
                    </div>
                    <div class="activity-card">
                        <span class="activity-icon">💻</span>
                        <h3 class="activity-title">Smart Coding</h3>
                        <p class="activity-desc">Writing efficient code with AI co-pilot</p>
                    </div>
                    <div class="activity-card">
                        <span class="activity-icon">📄</span>
                        <h3 class="activity-title">PDF Summarization</h3>
                        <p class="activity-desc">Extracting key insights from documents</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Scene 4: Final Logo -->
        <div class="scene" id="scene4">
            <div class="tech-background"></div>
            <div class="content">
                <div class="final-logo">
                    <h1 class="logo-main">AI Expert</h1>
                    <h2 class="logo-subtitle">Powered by Panku</h2>
                    <div style="display: flex; justify-content: center; gap: 2rem; margin-top: 2rem;">
                        <div style="background: rgba(0,247,255,0.1); padding: 1rem; border-radius: 10px; border: 2px solid #00f7ff;">
                            <span style="font-size: 2rem;">🚀</span>
                            <p>Innovation</p>
                        </div>
                        <div style="background: rgba(255,0,128,0.1); padding: 1rem; border-radius: 10px; border: 2px solid #ff0080;">
                            <span style="font-size: 2rem;">🤖</span>
                            <p>AI Powered</p>
                        </div>
                        <div style="background: rgba(0,255,128,0.1); padding: 1rem; border-radius: 10px; border: 2px solid #00ff80;">
                            <span style="font-size: 2rem;">⚡</span>
                            <p>Future Ready</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Controls -->
    <div class="controls">
        <button class="control-btn" onclick="previousScene()">Previous</button>
        <button class="control-btn" onclick="toggleAutoplay()" id="autoplayBtn">Pause</button>
        <button class="control-btn" onclick="nextScene()">Next</button>
        <button class="control-btn" onclick="restartIntro()">Restart</button>
    </div>

    <!-- Progress Bar -->
    <div class="progress-bar" id="progressBar"></div>

    <script>
        let currentScene = 1;
        const totalScenes = 4;
        let autoplayInterval;
        let isAutoplay = true;

        function showScene(sceneNumber) {
            // Hide all scenes
            document.querySelectorAll('.scene').forEach(scene => {
                scene.classList.remove('active');
            });
            
            // Show current scene
            document.getElementById(`scene${sceneNumber}`).classList.add('active');
            
            // Update progress bar
            const progress = (sceneNumber / totalScenes) * 100;
            document.getElementById('progressBar').style.width = progress + '%';
            
            // Add special effects for scene 3
            if (sceneNumber === 3) {
                setTimeout(() => {
                    document.querySelectorAll('.activity-card').forEach((card, index) => {
                        setTimeout(() => {
                            card.style.animation = 'slideInUp 0.5s ease forwards';
                        }, index * 200);
                    });
                }, 100);
            }
        }

        function nextScene() {
            currentScene++;
            if (currentScene > totalScenes) {
                currentScene = 1;
            }
            showScene(currentScene);
        }

        function previousScene() {
            currentScene--;
            if (currentScene < 1) {
                currentScene = totalScenes;
            }
            showScene(currentScene);
        }

        function toggleAutoplay() {
            const btn = document.getElementById('autoplayBtn');
            if (isAutoplay) {
                clearInterval(autoplayInterval);
                btn.textContent = 'Play';
                isAutoplay = false;
            } else {
                startAutoplay();
                btn.textContent = 'Pause';
                isAutoplay = true;
            }
        }

        function startAutoplay() {
            autoplayInterval = setInterval(() => {
                nextScene();
            }, 4000);
        }

        function restartIntro() {
            currentScene = 1;
            showScene(currentScene);
            if (isAutoplay) {
                clearInterval(autoplayInterval);
                startAutoplay();
            }
        }

        // Initialize
        showScene(1);
        startAutoplay();

        // Keyboard controls
        document.addEventListener('keydown', function(e) {
            switch(e.key) {
                case 'ArrowLeft':
                    previousScene();
                    break;
                case 'ArrowRight':
                    nextScene();
                    break;
                case ' ':
                    e.preventDefault();
                    toggleAutoplay();
                    break;
                case 'r':
                    restartIntro();
                    break;
            }
        });

        // Add sound effects (optional - you can add audio elements)
        function playTransitionSound() {
            // You can add audio elements here for sound effects
            // const audio = new Audio('path-to-your-sound.mp3');
            // audio.play();
        }

        // Add click sound to buttons
        document.querySelectorAll('.control-btn').forEach(btn => {
            btn.addEventListener('click', playTransitionSound);
        });
    </script>
</body>
</html>
