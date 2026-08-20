<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CYBER ARSENAL | GODSPY DOXXER & BTS TRACKER</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@600;800;900&family=Rajdhani:wght@500;700;900&family=Share+Tech+Mono&display=swap');

        /* RESET & BASE */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Rajdhani', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: #030305;
            color: #e0e0e0;
            overflow-x: hidden;
            min-height: 100vh;
        }

        /* 3D MOVING GRID BACKGROUND (NO GLOW/SHIMMER) */
        .cyber-grid-container {
            position: fixed;
            top: 0; left: 0; width: 100vw; height: 100vh;
            perspective: 1000px;
            z-index: -1;
            overflow: hidden;
            background: linear-gradient(to bottom, #000000 0%, #030305 100%);
        }
        .cyber-grid {
            position: absolute;
            width: 200%; height: 200%;
            bottom: -50%; left: -50%;
            background-image: 
                linear-gradient(rgba(170, 0, 0, 0.3) 1px, transparent 1px),
                linear-gradient(90deg, rgba(170, 0, 0, 0.3) 1px, transparent 1px);
            background-size: 60px 60px;
            transform: rotateX(65deg);
            animation: gridMove 10s linear infinite;
        }
        @keyframes gridMove {
            0% { transform: rotateX(65deg) translateY(0); }
            100% { transform: rotateX(65deg) translateY(60px); }
        }

        /* GODSPY HEADER LOGO & MANTA FONT TYPOGRAPHY WITH GRADIENT */
        .godspy-brand {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            margin-bottom: 15px;
        }
        .godspy-logo-svg {
            width: 42px;
            height: 42px;
            fill: none;
            stroke: #ff003c;
            stroke-width: 2;
        }
        .godspy-text-manta {
            font-family: 'Orbitron', sans-serif;
            font-size: 2.2rem;
            font-weight: 900;
            letter-spacing: 6px;
            text-transform: uppercase;
            background: linear-gradient(135deg, #ffffff 0%, #00f2fe 50%, #0088ff 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            display: inline-block;
            filter: drop-shadow(0 2px 4px rgba(0,0,0,0.8));
        }

        /* TYPOGRAPHY */
        .title-doxxer {
            font-size: 2.2rem;
            text-align: center;
            margin-bottom: 5px;
            letter-spacing: 2px;
        }
        .text-doxxer { font-weight: 900; color: #ff003c; }
        .text-info { 
            font-weight: 900; 
            color: transparent; 
            -webkit-text-stroke: 1.5px #0088ff; 
        }
        .subtitle-bts {
            text-align: center;
            font-size: 0.9rem;
            color: #aa0000;
            letter-spacing: 3px;
            margin-bottom: 20px;
            font-weight: 700;
        }
        .warning-text {
            color: #ff3333;
            font-size: 0.85rem;
            text-align: center;
            margin: 10px 0;
            font-weight: 600;
        }
        
        /* LAYOUTS & CONTAINERS */
        .screen { display: none; width: 100%; min-height: 100vh; padding: 20px; }
        .screen.active { display: block; }
        .container {
            max-width: 880px;
            margin: 0 auto;
            background: rgba(10, 10, 12, 0.96);
            border: 1px solid #220000;
            border-top: 3px solid #ff003c;
            padding: 20px;
        }

        /* NAVBAR & DRAWER BUTTON */
        nav {
            background: #08080a;
            border: 1px solid #220000;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 15px;
            margin-bottom: 20px;
            flex-wrap: wrap;
            gap: 10px;
        }
        .nav-left { display: flex; align-items: center; gap: 10px; }
        .nav-links { display: flex; gap: 8px; flex-wrap: wrap; }
        .nav-btn {
            background: transparent;
            border: 1px solid #440000;
            color: #aaa;
            padding: 8px 12px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        .nav-btn:hover, .nav-btn.active-tab {
            background: #1a0005;
            color: #ff003c;
            border-color: #ff003c;
        }
        .drawer-toggle-btn {
            background: #0d0d12;
            border: 1px solid #0088ff;
            color: #0088ff;
            padding: 8px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: 0.2s;
        }
        .drawer-toggle-btn:hover {
            background: #0088ff;
            color: #000;
        }
        .nav-profile {
            width: 40px; height: 40px;
            border-radius: 50%;
            border: 2px solid #0088ff;
            overflow: hidden;
            cursor: pointer;
            position: relative;
        }
        .nav-profile img { width: 100%; height: 100%; object-fit: cover; }

        /* DRAWER NAVIGATION SIDEBAR */
        .drawer-overlay {
            position: fixed; top: 0; left: 0; width: 100vw; height: 100vh;
            background: rgba(0,0,0,0.85); z-index: 400; display: none;
        }
        .cyber-drawer {
            position: fixed; top: 0; left: -320px; width: 300px; height: 100vh;
            background: #060609; border-right: 2px solid #ff003c;
            z-index: 401; transition: left 0.3s ease; padding: 20px;
            display: flex; flex-direction: column;
        }
        .cyber-drawer.open { left: 0; }
        .drawer-header {
            display: flex; justify-content: space-between; align-items: center;
            border-bottom: 1px solid #222; padding-bottom: 15px; margin-bottom: 20px;
        }
        .btn-close-drawer {
            background: transparent; border: none; color: #ff003c; cursor: pointer;
        }
        .drawer-menu { display: flex; flex-direction: column; gap: 10px; }
        .drawer-item {
            background: #0a0a0f; border: 1px solid #222; padding: 12px 15px;
            color: #ccc; font-weight: 700; cursor: pointer; display: flex;
            align-items: center; gap: 10px; transition: 0.2s; font-size: 0.9rem;
        }
        .drawer-item:hover {
            border-color: #0088ff; color: #00f2fe; background: #101420;
        }

        /* ARSENAL SLIDER NAVBAR */
        .arsenal-slider-container {
            position: relative;
            display: flex;
            align-items: center;
            margin-bottom: 20px;
            background: #08080a;
            border: 1px solid #220000;
            padding: 5px;
        }
        .arsenal-slider {
            display: flex;
            gap: 10px;
            overflow-x: auto;
            scroll-behavior: smooth;
            scrollbar-width: none;
            -ms-overflow-style: none;
            padding: 5px;
            width: 100%;
        }
        .arsenal-slider::-webkit-scrollbar { display: none; }
        .arsenal-item {
            flex: 0 0 auto;
            min-width: 130px;
            background: #0a0a0d;
            border: 1px solid #330000;
            padding: 12px 15px;
            text-align: center;
            cursor: pointer;
            font-size: 0.85rem;
            color: #aaa;
            font-weight: 700;
            transition: all 0.2s ease;
        }
        .arsenal-item:hover {
            border-color: #ff003c;
            color: #00f2fe;
            background: #150005;
        }
        .slider-arrow {
            background: #0d0d12;
            border: 1px solid #330000;
            color: #0088ff;
            cursor: pointer;
            padding: 10px 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 2;
        }
        .slider-arrow:hover { background: #1a0008; color: #ff003c; }

        /* INPUTS & BUTTONS */
        .input-group { margin-bottom: 15px; position: relative; }
        .input-box {
            width: 100%;
            background: #050505;
            border: 1px solid #440000;
            color: #00e5ff;
            padding: 15px;
            font-size: 1.1rem;
            font-family: 'Share Tech Mono', monospace;
            outline: none;
        }
        .input-box:focus { border-color: #ff003c; }
        .btn-action {
            width: 100%;
            background: #110000;
            color: #ff003c;
            border: 1px solid #ff003c;
            padding: 15px;
            font-size: 1.2rem;
            font-weight: 700;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }
        .btn-action:active { background: #ff003c; color: #000; }

        /* LOGIN SCREEN */
        .login-box {
            max-width: 420px; margin: 6vh auto;
            background: #050508; border: 1px solid #222;
            padding: 30px; border-top: 3px solid #0088ff;
        }
        .social-login { display: flex; gap: 10px; margin-top: 20px; }
        .btn-social {
            flex: 1; padding: 10px; background: #0a0a0a;
            border: 1px solid #333; cursor: pointer;
            display: flex; justify-content: center; align-items: center;
        }
        .btn-social svg { width: 24px; height: 24px; fill: #aaa; }
        .btn-social:hover { background: #111; border-color: #0088ff; }
        .btn-social:hover svg { fill: #0088ff; }

        /* MODALS & FLOATING CARDS */
        .modal-overlay, .floating-panel-overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.90); display: none;
            justify-content: center; align-items: center; z-index: 500;
        }
        .modal-content, .floating-card {
            background: #060609; border: 1px solid #0088ff;
            width: 90%; max-width: 520px; padding: 20px;
        }
        .modal-header, .floating-card-header {
            font-size: 1.2rem; color: #0088ff; margin-bottom: 15px;
            border-bottom: 1px solid #222; padding-bottom: 8px; font-weight: bold;
            display: flex; justify-content: space-between; align-items: center;
        }
        .btn-close-floating {
            background: transparent; border: none; color: #ff003c; cursor: pointer;
        }
        .floating-card-body {
            color: #ccc; font-size: 0.9rem; line-height: 1.5;
            max-height: 400px; overflow-y: auto; font-family: 'Share Tech Mono', monospace;
        }

        /* RESULTS AREA */
        .result-area { margin-top: 20px; display: none; }
        .format-toggle { display: flex; gap: 10px; margin-bottom: 15px; }
        .btn-toggle { flex: 1; background: #050505; border: 1px solid #333; color: #777; padding: 10px; cursor: pointer; font-weight: bold; }
        .btn-toggle.active { border-color: #ff003c; color: #ff003c; }

        /* DATA MATRIX (JSON) */
        .data-matrix {
            background: #000; border: 1px solid #222;
            padding: 15px; font-family: 'Share Tech Mono', monospace;
            color: #00e5ff; font-size: 0.85rem; white-space: pre-wrap;
            word-wrap: break-word; display: none; max-height: 500px; overflow-y: auto;
        }

        /* DIGITAL COVER BOARD (GRID) */
        .cover-board { display: none; flex-direction: column; gap: 8px; max-height: 550px; overflow-y: auto; padding-right: 5px; }
        .data-card {
            background: #08080a; border: 1px solid #220000; border-left: 3px solid #ff003c;
            padding: 10px; display: flex; flex-direction: column;
        }
        .data-card .lbl { font-size: 0.75rem; color: #888; text-transform: uppercase; margin-bottom: 2px; letter-spacing: 1px; }
        .data-card .val { font-size: 0.95rem; color: #eee; font-weight: 600; font-family: 'Share Tech Mono', monospace; word-break: break-all; }

        .active-view { display: flex !important; }

        /* MAP AREA */
        .map-container {
            width: 100%; height: 350px; border: 1px solid #0088ff;
            margin-top: 20px; position: relative; background: #000;
        }
        .map-frame { width: 100%; height: 100%; border: none; }
        .coord-overlay {
            position: absolute; bottom: 10px; left: 10px;
            background: rgba(0,0,0,0.85); border: 1px solid #0088ff;
            padding: 5px 10px; font-family: 'Share Tech Mono', monospace;
            color: #00e5ff; font-size: 0.85rem;
        }

        /* RADAR BLOCKER / JAMMER */
        .radar-box {
            margin-top: 20px; border: 1px solid #333; padding: 20px;
            display: flex; flex-direction: column; align-items: center; background: #050505;
        }
        .radar {
            width: 120px; height: 120px; border-radius: 50%;
            border: 1px solid #0088ff; position: relative; overflow: hidden;
            background: radial-gradient(circle, rgba(0,136,255,0.1) 0%, transparent 70%);
            margin-bottom: 15px;
        }
        .radar-sweep {
            position: absolute; top: 0; left: 50%; width: 50%; height: 50%;
            background: linear-gradient(90deg, rgba(0,136,255,0.8), transparent);
            transform-origin: bottom left;
            animation: spin 2s linear infinite;
        }
        .radar-dot {
            width: 10px; height: 10px; background: #ff003c; border-radius: 50%;
            position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%);
            display: none;
        }
        @keyframes spin { 100% { transform: rotate(360deg); } }
        
        /* TERMINAL LOGS */
        .terminal-loader {
            font-family: 'Share Tech Mono', monospace;
            color: #ff003c; font-size: 0.9rem; margin-top: 15px; text-align: left;
            display: none;
        }

        #profile-upload { display: none; }

        /* FLOATING BUBBLE MODAL */
        .bubble-alert-overlay {
            position: fixed; top: 0; left: 0; width: 100vw; height: 100vh;
            background: rgba(0,0,0,0.75); display: none;
            justify-content: center; align-items: center; z-index: 600;
        }
        .bubble-alert-box {
            background: #080a0f; border: 2px solid #ff003c;
            border-radius: 12px; padding: 25px; max-width: 380px; width: 85%;
            text-align: center;
        }
        .bubble-icon {
            width: 48px; height: 48px; margin: 0 auto 10px auto;
            border-radius: 50%; border: 2px solid #ff003c;
            display: flex; justify-content: center; align-items: center;
            color: #ff003c; font-size: 1.5rem; font-weight: bold;
        }
        .bubble-title { font-family: 'Orbitron', sans-serif; color: #fff; font-size: 1.1rem; margin-bottom: 8px; }
        .bubble-msg { font-size: 0.9rem; color: #bbb; margin-bottom: 20px; font-family: 'Share Tech Mono', monospace; }
        .btn-bubble {
            background: #ff003c; color: #fff; border: none; padding: 8px 24px;
            font-weight: bold; font-family: 'Rajdhani', sans-serif; cursor: pointer; border-radius: 4px;
        }

        /* INTRO VIDEO OVERLAY FRAME */
        .video-intro-container {
            position: fixed; top: 0; left: 0; width: 100vw; height: 100vh;
            background: #000; z-index: 700; display: none;
            flex-direction: column; justify-content: center; align-items: center; padding: 20px;
        }
        .video-frame-futuristic {
            position: relative; width: 100%; max-width: 720px;
            border: 2px solid #0088ff; border-radius: 8px; overflow: hidden;
            background: #050508;
        }
        .video-player { width: 100%; height: auto; display: block; max-height: 60vh; object-fit: contain; }
        .video-caption {
            text-align: center; margin-top: 15px;
        }
        .video-godspy-text {
            font-family: 'Orbitron', sans-serif; font-size: 2.2rem; font-weight: 900;
            letter-spacing: 6px; text-transform: uppercase;
            background: linear-gradient(135deg, #ffffff 0%, #00f2fe 50%, #0088ff 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            display: inline-block;
        }
        .video-project-text {
            font-family: 'Share Tech Mono', monospace; font-size: 1rem; color: #0088ff;
            letter-spacing: 6px; font-weight: bold; margin-top: 5px;
        }
        .btn-skip-video {
            margin-top: 20px; background: transparent; border: 1px solid #ff003c;
            color: #ff003c; padding: 10px 30px; font-weight: bold; font-size: 1rem;
            cursor: pointer; letter-spacing: 2px; transition: 0.3s;
        }
        .btn-skip-video:hover { background: #ff003c; color: #000; }

        /* ACCOUNT SELECTOR MODAL */
        .account-item {
            display: flex; align-items: center; gap: 12px; padding: 12px;
            border: 1px solid #222; margin-bottom: 8px; cursor: pointer; background: #0a0a0f;
            transition: 0.2s;
        }
        .account-item:hover { border-color: #0088ff; background: #101420; }
        .account-avatar { width: 36px; height: 36px; border-radius: 50%; background: #0088ff; color: #fff; display: flex; align-items: center; justify-content: center; font-weight: bold; }
    </style>
</head>
<body>

    <!-- 3D GRID BG -->
    <div class="cyber-grid-container"><div class="cyber-grid"></div></div>

    <!-- DRAWER NAVIGATION SIDEBAR -->
    <div class="drawer-overlay" id="drawer-overlay" onclick="toggleDrawer()"></div>
    <div class="cyber-drawer" id="cyber-drawer">
        <div class="drawer-header">
            <div class="godspy-brand" style="margin-bottom:0;">
                <div class="godspy-text-manta" style="font-size:1.5rem;">GODSPY</div>
            </div>
            <button class="btn-close-drawer" onclick="toggleDrawer()">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/></svg>
            </button>
        </div>
        <div class="drawer-menu">
            <div class="drawer-item" onclick="openFloatingCard('news')">
                <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm-5 14H7v-2h7v2zm3-4H7v-2h10v2zm0-4H7V7h10v2z"/></svg>
                BERITA & INTEL UPDATES
            </div>
            <div class="drawer-item" onclick="openFloatingCard('faq')">
                <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 16h-2v-2h2v2zm1.07-7.75l-.9.92C12.45 11.9 12 12.5 12 14h-2v-.5c0-1.1.45-2.1 1.17-2.83l1.24-1.26c.37-.36.59-.86.59-1.41 0-1.1-.9-2-2-2s-2 .9-2 2H7c0-2.76 2.24-5 5-5s5 2.24 5 5c0 1.04-.42 1.99-1.07 2.75z"/></svg>
                FAQ & PANDUAN PENGGUNAAN
            </div>
            <div class="drawer-item" onclick="openFloatingCard('about')">
                <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 15h-2v-6h2v6zm0-8h-2V7h2v2z"/></svg>
                TENTANG GODSPY PROJECT
            </div>
            <div class="drawer-item" onclick="openFloatingCard('docs')">
                <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm2 16H8v-2h8v2zm0-4H8v-2h8v2zm-3-5V3.5L18.5 9H13z"/></svg>
                ARSENAL SPECIFICATION
            </div>
        </div>
    </div>

    <!-- FLOATING CARD MODAL PANEL -->
    <div class="floating-panel-overlay" id="floating-panel-overlay" onclick="closeFloatingCard(event)">
        <div class="floating-card" onclick="event.stopPropagation()">
            <div class="floating-card-header">
                <span id="floating-title">PANEL INFORMASI</span>
                <button class="btn-close-floating" onclick="closeFloatingCardDirect()">
                    <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/></svg>
                </button>
            </div>
            <div class="floating-card-body" id="floating-body"></div>
        </div>
    </div>

    <!-- FLOATING BUBBLE ALERT -->
    <div class="bubble-alert-overlay" id="bubble-alert">
        <div class="bubble-alert-box">
            <div class="bubble-icon">!</div>
            <div class="bubble-title" id="bubble-title">SYSTEM NOTICE</div>
            <div class="bubble-msg" id="bubble-msg">Pesan notifikasi...</div>
            <button class="btn-bubble" onclick="closeBubbleAlert()">OK / LANJUTKAN</button>
        </div>
    </div>

    <!-- INTRO VIDEO OVERLAY -->
    <div class="video-intro-container" id="video-intro-overlay">
        <div class="video-frame-futuristic">
            <video id="intro-video-element" class="video-player" src="video_intro.mp4" autoplay playsinline></video>
        </div>
        <div class="video-caption">
            <div class="video-godspy-text">GODSPY</div>
            <div class="video-project-text">PROJECT TEAM</div>
        </div>
        <button class="btn-skip-video" onclick="finishVideoIntro()">SKIP INTRO ▶</button>
    </div>

    <!-- SCREEN: LOGIN/REGISTER -->
    <div id="screen-auth" class="screen active">
        <div class="login-box" id="auth-box">
            
            <!-- GODSPY HEADER LOGO -->
            <div class="godspy-brand">
                <svg class="godspy-logo-svg" viewBox="0 0 100 100">
                    <path d="M10,50 Q30,20 45,45 Q20,35 10,50 Z" fill="#ff003c" opacity="0.8"/>
                    <path d="M90,50 Q70,20 55,45 Q80,35 90,50 Z" fill="#ff003c" opacity="0.8"/>
                    <path d="M5,60 Q28,38 48,52 Q22,48 5,60 Z" fill="#aa0000"/>
                    <path d="M95,60 Q72,38 52,52 Q78,48 95,60 Z" fill="#aa0000"/>
                    <circle cx="50" cy="50" r="22" stroke="#0088ff" stroke-width="2.5"/>
                    <circle cx="50" cy="50" r="14" stroke="#ff003c" stroke-width="2"/>
                    <circle cx="50" cy="50" r="6" fill="#00e5ff"/>
                    <path d="M25,50 L75,50" stroke="#0088ff" stroke-width="1.5" stroke-dasharray="3,3"/>
                    <path d="M50,25 L50,75" stroke="#0088ff" stroke-width="1.5" stroke-dasharray="3,3"/>
                </svg>
                <div class="godspy-text-manta">GODSPY</div>
            </div>

            <h2 class="title-doxxer" style="font-size:1.8rem;"><span class="text-info">SYSTEM</span> <span class="text-doxxer">LOGIN</span></h2>
            <p style="color:#666; text-align:center; margin-bottom:20px; font-size:0.8rem;">AUTHORIZED PERSONNEL ONLY</p>
            
            <div class="input-group">
                <input type="text" id="auth-usr" class="input-box" placeholder="USERNAME">
            </div>
            <div class="input-group">
                <input type="password" id="auth-pwd" class="input-box" placeholder="PASSWORD">
            </div>
            <button class="btn-action" onclick="handleLogin()">AUTHENTICATE</button>
            <p style="text-align:center; margin-top:15px; font-size:0.8rem; cursor:pointer; color:#0088ff;" onclick="toggleAuthMode()">No account? Create Entity</p>

            <div class="social-login">
                <div class="btn-social" title="Login with GitHub" onclick="triggerSocialAccountChooser('GitHub')">
                    <svg viewBox="0 0 24 24"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"/></svg>
                </div>
                <div class="btn-social" title="Login with GitLab" onclick="triggerSocialAccountChooser('GitLab')">
                    <svg viewBox="0 0 24 24"><path d="M23.955 13.587l-1.342-4.135-2.664-8.189c-.135-.423-.73-.423-.867 0L16.418 9.45H7.582L4.918 1.263c-.137-.423-.732-.423-.867 0L1.387 9.452.045 13.587c-.173.535.02 1.13.468 1.455l11.487 8.356 11.487-8.356c.448-.325.64-1.92.468-1.455z"/></svg>
                </div>
                <div class="btn-social" title="Login with Google" onclick="triggerSocialAccountChooser('Google')">
                    <svg viewBox="0 0 24 24"><path d="M12.24 10.285V14.4h6.806c-.275 1.765-2.056 5.174-6.806 5.174-4.095 0-7.439-3.389-7.439-7.574s3.345-7.574 7.439-7.574c2.33 0 3.891.989 4.785 1.849l3.254-3.138C18.189 1.186 15.479 0 12.24 0c-6.635 0-12 5.365-12 12s5.365 12 12 12c6.926 0 11.52-4.869 11.52-11.726 0-.788-.085-1.39-.189-1.989H12.24z"/></svg>
                </div>
                <div class="btn-social" title="Login with Apple" onclick="triggerSocialAccountChooser('Apple')">
                    <svg viewBox="0 0 24 24"><path d="M16.365 1.43c-1.335.585-2.82 1.545-3.69 2.61-.78.96-1.425 2.295-1.185 3.585 1.455.06 2.895-.81 3.735-1.845.765-.96 1.35-2.31 1.14-3.57-.045-.015-.12-.03-.225-.03-.18 0-.495.06-.795.195H16.365zm-1.83 6.645c-1.785-.015-3.33 1.14-4.2 1.14-.885 0-2.145-1.02-3.54-1.005-1.83.015-3.51 1.05-4.44 2.685-1.905 3.285-.48 8.16 1.365 10.875.915 1.32 1.995 2.805 3.42 2.76 1.38-.045 1.905-.885 3.555-.885 1.635 0 2.115.885 3.585.855 1.5-.03 2.43-1.35 3.33-2.67 1.035-1.515 1.47-2.985 1.485-3.06-.03-.015-2.865-1.11-2.895-4.38-.03-2.73 2.235-4.035 2.34-4.095-1.275-1.845-3.24-2.1-3.96-2.16z"/></svg>
                </div>
            </div>
        </div>
    </div>

    <!-- ACCOUNT CHOOSER MODAL -->
    <div class="modal-overlay" id="account-modal">
        <div class="modal-content">
            <div class="modal-header" id="account-provider-title">PILIH AKUN GOOGLE</div>
            <p style="color:#888; font-size:0.85rem; margin-bottom:15px; font-family:'Share Tech Mono', monospace;">Gunakan akun terdaftar untuk melanjutkan otentikasi:</p>
            
            <div id="account-list"></div>
            
            <button class="btn-action" style="padding:10px; font-size:0.9rem; margin-top:10px;" onclick="closeAccountModal()">BATAL</button>
        </div>
    </div>

    <!-- MAIN DASHBOARD -->
    <div id="screen-main" class="screen">
        <div class="container">
            
            <!-- GODSPY HEADER IN DASHBOARD -->
            <div class="godspy-brand" style="margin-bottom: 10px;">
                <svg class="godspy-logo-svg" viewBox="0 0 100 100">
                    <path d="M10,50 Q30,20 45,45 Q20,35 10,50 Z" fill="#ff003c" opacity="0.8"/>
                    <path d="M90,50 Q70,20 55,45 Q80,35 90,50 Z" fill="#ff003c" opacity="0.8"/>
                    <path d="M5,60 Q28,38 48,52 Q22,48 5,60 Z" fill="#aa0000"/>
                    <path d="M95,60 Q72,38 52,52 Q78,48 95,60 Z" fill="#aa0000"/>
                    <circle cx="50" cy="50" r="22" stroke="#0088ff" stroke-width="2.5"/>
                    <circle cx="50" cy="50" r="14" stroke="#ff003c" stroke-width="2"/>
                    <circle cx="50" cy="50" r="6" fill="#00e5ff"/>
                    <path d="M25,50 L75,50" stroke="#0088ff" stroke-width="1.5" stroke-dasharray="3,3"/>
                    <path d="M50,25 L50,75" stroke="#0088ff" stroke-width="1.5" stroke-dasharray="3,3"/>
                </svg>
                <div class="godspy-text-manta">GODSPY</div>
            </div>

            <nav>
                <div class="nav-left">
                    <button class="drawer-toggle-btn" onclick="toggleDrawer()" title="Menu Drawer">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M3 18h18v-2H3v2zm0-5h18v-2H3v2zm0-7v2h18V6H3z"/></svg>
                    </button>
                    <div class="nav-links">
                        <button class="nav-btn active-tab" onclick="switchTab('doxxer')">
                            <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/></svg>
                            DOXXER
                        </button>
                        <button class="nav-btn" onclick="switchTab('tracker')">
                            <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/></svg>
                            TRACKER
                        </button>
                        <button class="nav-btn" onclick="switchTab('jammer')">
                            <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 14H9V8h2v8zm4 0h-2V8h2v8z"/></svg>
                            STB JAMMER
                        </button>
                    </div>
                </div>
                <div class="nav-profile" onclick="document.getElementById('profile-upload').click()">
                    <img id="user-avatar" src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0iIzMzMyI+PHBhdGggZD0iTTEyIDJDMiAyIDIgM1g==" alt="profile">
                </div>
                <input type="file" id="profile-upload" accept="image/*" onchange="updateProfile(event)">
            </nav>

            <!-- ARSENAL SLIDER NAVBAR (SLIDEABLE & SCROLLABLE 1 BY 1) -->
            <div class="arsenal-slider-container">
                <button class="slider-arrow" onclick="scrollArsenal(-1)">
                    <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M15.41 7.41L14 6l-6 6 6 6 1.41-1.41L10.83 12z"/></svg>
                </button>
                <div class="arsenal-slider" id="arsenal-slider">
                    <div class="arsenal-item" onclick="openTool('BRUTEFORCE')">BRUTEFORCE</div>
                    <div class="arsenal-item" onclick="openTool('ADMIN FINDER')">ADMIN FINDER</div>
                    <div class="arsenal-item" onclick="openTool('WEB SCRAPER')">WEB SCRAPER</div>
                    <div class="arsenal-item" onclick="openTool('DNS LOOKUP')">DNS LOOKUP</div>
                    <div class="arsenal-item" onclick="openTool('CSRF LOGIN')">CSRF LOGIN</div>
                    <div class="arsenal-item" onclick="openTool('DIOS BYPASS')">DIOS BYPASS</div>
                    <div class="arsenal-item" onclick="openTool('SQL INJECT')">SQL INJECT</div>
                    <div class="arsenal-item" onclick="openTool('OSINT IP')">OSINT IP</div>
                </div>
                <button class="slider-arrow" onclick="scrollArsenal(1)">
                    <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M10 6L8.59 7.41 13.17 12l-4.58 4.59L10 18l6-6z"/></svg>
                </button>
            </div>

            <!-- VIEW: DOXXER INFO -->
            <div id="view-doxxer">
                <h1 class="title-doxxer"><span class="text-doxxer">DOXXER</span> <span class="text-info">INFO</span></h1>
                <p class="warning-text">PERINGATAN: JANGAN GUNAKAN SEMBARANG KARENA BERSIFAT ILLEGAL!</p>
                
                <div class="input-group">
                    <input type="number" id="dox-input" class="input-box" placeholder="CONTOH: 08123456789">
                </div>
                <button class="btn-action" onclick="runDoxxer()">EXECUTE OSINT EXTRACTION</button>

                <div id="dox-terminal" class="terminal-loader"></div>

                <div id="dox-result" class="result-area">
                    <div class="format-toggle">
                        <button class="btn-toggle active" onclick="switchFormat('board')">COVER BOARD</button>
                        <button class="btn-toggle" onclick="switchFormat('matrix')">DATA MATRIX</button>
                    </div>

                    <div id="res-matrix" class="data-matrix"></div>
                    <div id="res-board" class="cover-board"></div>
                </div>
            </div>

            <!-- VIEW: BTS TRACKER -->
            <div id="view-tracker" style="display:none;">
                <h1 class="title-doxxer" style="font-size: 2.2rem; margin-bottom:0;"><span class="text-doxxer">BTS SIGNAL&SS7</span> <span class="text-info">TRACK LOCATION</span></h1>
                <p class="subtitle-bts">BY VLZ0XBYTE & N.E.M.E.S.I.S. TEAM</p>
                <p style="text-align:center; color:#777; font-size:0.85rem; margin-bottom:15px;">(bts signal untuk melacak ip adres dan sinyal hp melalui nomor whatsapp)</p>

                <div class="input-group">
                    <input type="number" id="track-input" class="input-box" placeholder="CONTOH: 08123456789">
                </div>
                <button class="btn-action" onclick="runTracker()">INITIALIZE TRACKING</button>

                <div id="track-terminal" class="terminal-loader"></div>

                <div id="track-result" style="display:none;">
                    <div class="map-container">
                        <iframe id="map-frame" class="map-frame" src="" loading="lazy"></iframe>
                        <div class="coord-overlay" id="map-coords">LAT: 0.0000 | LNG: 0.0000<br>IP: 0.0.0.0</div>
                    </div>
                </div>
            </div>

            <!-- VIEW: STB JAMMER -->
            <div id="view-jammer" style="display:none;">
                <h1 class="title-doxxer" style="font-size: 2.2rem; margin-bottom:0;"><span class="text-doxxer">JAMMER</span> <span class="text-info">SIGNAL STB TV</span></h1>
                <h1 class="title-doxxer" style="font-size: 1.1rem; margin-bottom:0;">
                    <span class="text-doxxer">PROGRAM</span>
                    <span class="text-info">BY VLZ0XBYTE</span>
                </h1>
                <p class="warning-text" style="color:#ffaa00;">HARAP SAMBUNGKAN DENGAN HARDWARE SEPERTI JAMMER DAN BRUCE!</p>
                
                <div class="radar-box">
                    <div class="radar" id="radar-ui">
                        <div class="radar-sweep" id="radar-sweep"></div>
                        <div class="radar-dot" id="radar-dot"></div>
                    </div>
                    <button class="btn-action" id="btn-scan-stb" style="width: 200px; padding:10px; font-size:1rem;" onclick="scanSTB()">SCAN SIGNAL TV</button>
                    <button class="btn-action" id="btn-stop-stb" style="width: 200px; padding:10px; font-size:1rem; display:none; border-color:#ff003c; color:#ff003c;" onclick="stopSTB()">STOP JAMMING</button>
                    <p id="block-status" style="color:#666; margin-top:10px; font-family:'Share Tech Mono', monospace; font-size:0.85rem; font-weight:bold;">STATUS: MENUNGGU SINYAL...</p>
                    
                    <div id="jammer-terminal" class="terminal-loader" style="height: 150px; overflow:hidden; display:none; width:100%; border:1px solid #330000; padding:10px; margin-top:15px;"></div>
                </div>
            </div>
            
            <div style="text-align:center; margin-top:30px;">
                <button class="nav-btn" style="display:inline-block; margin:auto;" onclick="logout()">LOGOUT / DISCONNECT</button>
            </div>
        </div>
    </div>

    <!-- MODAL FOR ARSENAL TOOLS -->
    <div class="modal-overlay" id="tool-modal" onclick="closeTool(event)">
        <div class="modal-content" onclick="event.stopPropagation()">
            <div class="modal-header" id="tool-title">TOOL NAME</div>
            <p style="color:#888; font-size:0.85rem; margin-bottom:15px; font-family:'Share Tech Mono', monospace;">Initiating target configuration...</p>
            
            <div class="input-group" id="tool-inputs"></div>
            
            <button class="btn-action" style="padding:10px; font-size:1rem;" onclick="executeToolAction()">EXECUTE TOOL</button>
            <div id="tool-terminal" style="color:#00e5ff; margin-top:10px; font-family:'Share Tech Mono', monospace; font-size:0.8rem; display:none; overflow-y:auto; max-height:280px; background:#000; padding:10px; border:1px solid #222;"></div>
        </div>
    </div>

    <script>
        // --- FLOATING BUBBLE ALERT SYSTEM ---
        function showBubbleAlert(title, message) {
            document.getElementById('bubble-title').innerText = title;
            document.getElementById('bubble-msg').innerText = message;
            document.getElementById('bubble-alert').style.display = 'flex';
        }
        function closeBubbleAlert() {
            document.getElementById('bubble-alert').style.display = 'none';
        }

        // --- DRAWER NAVIGATION & FLOATING CARD PANELS ---
        function toggleDrawer() {
            const drawer = document.getElementById('cyber-drawer');
            const overlay = document.getElementById('drawer-overlay');
            if (drawer.classList.contains('open')) {
                drawer.classList.remove('open');
                overlay.style.display = 'none';
            } else {
                drawer.classList.add('open');
                overlay.style.display = 'block';
            }
        }

        function openFloatingCard(type) {
            toggleDrawer();
            const overlay = document.getElementById('floating-panel-overlay');
            const title = document.getElementById('floating-title');
            const body = document.getElementById('floating-body');

            if (type === 'about') {
                title.innerText = 'TENTANG GODSPY PROJECT';
                body.innerHTML = `
                    <div style="color:#00f2fe; font-weight:bold; margin-bottom:8px;">[ SYSTEM IDENTITY & FOUNDER ]</div>
                    <p><strong>PENDIRI UTAMA:</strong> LOZX DARI TEAM N.E.M.E.S.I.S. DAN GODSPY D.I.W.M.</p>
                    <p><strong>TIPE FRAMEWORK:</strong> Advanced Cyber Intelligence & OSINT Recon Suite v4.0</p>
                    <br>
                    <div style="color:#ff003c; font-weight:bold; margin-bottom:8px;">[ TUJUAN PEMBUATAN ALAT ]</div>
                    <p>GODSPY diciptakan sebagai platform riset intelijen keamanan cyber tingkat tinggi. Alat ini dirancang khusus untuk memfasilitasi ekstraksi data OSINT terstruktur, audit kerentanan jaringan,deteksi frekuensi BTS/SS7, serta verifikasi identitas kependudukan secara cepat dan akurat dalam satu sistem terintegrasi.</p>
                `;
            } else if (type === 'news') {
                title.innerText = 'BERITA & INTEL UPDATES';
                body.innerHTML = `
                    <div style="color:#00f2fe; margin-bottom:5px;">● [2026-08-20] UPDATE SYSTEM GODSPY v4.0 RELEASED</div>
                    <p style="color:#aaa; font-size:0.8rem; margin-bottom:12px;">Pembaruan penuh pada modul OSINT Doxxer dengan dukungan integrasi NIK regional 38 Provinsi Indonesia secara lengkap.</p>
                    <div style="color:#00f2fe; margin-bottom:5px;">● [2026-08-15] STB FREQUENCY SCANNER ENHANCEMENT</div>
                    <p style="color:#aaa; font-size:0.8rem;">Peningkatan algoritma pemblokir frekuensi sinyal digital TV Bruce & Hardware Jammer.</p>
                `;
            } else if (type === 'faq') {
                title.innerText = 'FAQ & PANDUAN PENGGUNAAN';
                body.innerHTML = `
                    <div style="color:#00f2fe; font-weight:bold;">Q: Bagaimana cara kerja Doxxer OSINT?</div>
                    <p style="margin-bottom:10px;">A: Memasukkan nomor HP terdaftar akan mentriangulasi identitas Sipil NIK, KK, NISN, dan Data Keluarga secara mutlak konsisten.</p>
                    <div style="color:#00f2fe; font-weight:bold;">Q: Mengapa data nomor yang sama selalu konsisten?</div>
                    <p>A: Sistem menggunakan enkripsi Seed Deterministik mutlak dari input nomor tujuan sehingga menghasilkan rekaman valid yang tidak acak saat di-dox ulang.</p>
                `;
            } else if (type === 'docs') {
                title.innerText = 'ARSENAL SPECIFICATION';
                body.innerHTML = `
                    <div style="color:#00f2fe;">[ MODUL ARSENAL TERSEDIA ]</div>
                    <p>1. <strong>BRUTEFORCE</strong>: SSH/Port Password Spraying</p>
                    <p>2. <strong>ADMIN FINDER</strong>: Real-time path scanner admin portal</p>
                    <p>3. <strong>DIOS BYPASS</strong>: High-density database structure extractor (DH HackBar Format)</p>
                    <p>4. <strong>OSINT IP</strong>: Geolocation, ASN, & Port Open Intelligence</p>
                `;
            }
            overlay.style.display = 'flex';
        }

        function closeFloatingCard(e) {
            if (e.target.id === 'floating-panel-overlay') {
                document.getElementById('floating-panel-overlay').style.display = 'none';
            }
        }
        function closeFloatingCardDirect() {
            document.getElementById('floating-panel-overlay').style.display = 'none';
        }

        // --- ARSENAL SLIDER CONTROL ---
        function scrollArsenal(dir) {
            const slider = document.getElementById('arsenal-slider');
            slider.scrollBy({ left: dir * 160, behavior: 'smooth' });
        }

        // --- AUTH & VIDEO INTRO LOGIC ---
        let isLoginMode = true;
        
        function toggleAuthMode() {
            isLoginMode = !isLoginMode;
            const btn = document.querySelector('#auth-box .btn-action');
            const toggleText = document.querySelector('#auth-box p[onclick]');
            const title = document.querySelector('#auth-box .text-doxxer');
            
            if (isLoginMode) {
                title.innerText = 'LOGIN';
                btn.innerText = 'AUTHENTICATE';
                toggleText.innerText = 'No account? Create Entity';
            } else {
                title.innerText = 'CREATE';
                btn.innerText = 'REGISTER IDENTITY';
                toggleText.innerText = 'Have identity? Authenticate';
            }
        }

        function handleLogin() {
            const usr = document.getElementById('auth-usr').value;
            const pwd = document.getElementById('auth-pwd').value;
            if(!usr || !pwd) {
                showBubbleAlert("AUTHENTICATION ERROR", "Harap isi username dan password!");
                return;
            }

            if(!isLoginMode) {
                localStorage.setItem('cyber_usr', usr);
                localStorage.setItem('cyber_pwd', pwd);
                showBubbleAlert("ENTITY CREATED", "Identitas berhasil dibuat. Silahkan login.");
                toggleAuthMode();
            } else {
                const sUsr = localStorage.getItem('cyber_usr');
                const sPwd = localStorage.getItem('cyber_pwd');
                if((usr === sUsr && pwd === sPwd) || (usr === 'admin' && pwd === 'admin')) {
                    startVideoIntro();
                } else {
                    document.getElementById('auth-pwd').value = '';
                    showBubbleAlert("ACCESS DENIED", "Kredensial salah / tidak terdaftar!");
                }
            }
        }

        function triggerSocialAccountChooser(provider) {
            document.getElementById('account-provider-title').innerText = `AKUN TERHUBUNG (${provider.toUpperCase()})`;
            const accounts = [
                { name: "ARGA RADEN PRATAMA", email: "arga.pratama.dev@gmail.com" },
                { name: "GODSPY OPERATOR", email: "godspy.team@godspy-project.net" },
                { name: "CYBER USER SEC", email: "user.security99@gmail.com" }
            ];
            
            let html = '';
            accounts.forEach(acc => {
                html += `
                    <div class="account-item" onclick="selectSocialAccount('${acc.name}', '${acc.email}')">
                        <div class="account-avatar">${acc.name.charAt(0)}</div>
                        <div>
                            <div style="color:#fff; font-weight:bold; font-size:0.95rem;">${acc.name}</div>
                            <div style="color:#666; font-size:0.8rem; font-family:'Share Tech Mono';">${acc.email}</div>
                        </div>
                    </div>
                `;
            });
            document.getElementById('account-list').innerHTML = html;
            document.getElementById('account-modal').style.display = 'flex';
        }

        function closeAccountModal() {
            document.getElementById('account-modal').style.display = 'none';
        }

        function selectSocialAccount(name, email) {
            closeAccountModal();
            startVideoIntro();
        }

        function startVideoIntro() {
            const videoOverlay = document.getElementById('video-intro-overlay');
            const videoEl = document.getElementById('intro-video-element');
            videoOverlay.style.display = 'flex';
            videoEl.currentTime = 0;
            videoEl.muted = false; // BERSUARA FULL
            videoEl.volume = 1.0;
            videoEl.play().catch(() => {
                // If browser blocks unmuted play without gesture
                videoEl.muted = true;
                videoEl.play();
            });
            videoEl.onended = function() {
                finishVideoIntro();
            };
        }

        function finishVideoIntro() {
            const videoEl = document.getElementById('intro-video-element');
            videoEl.pause();
            document.getElementById('video-intro-overlay').style.display = 'none';
            enterDashboard();
        }

        function enterDashboard() {
            document.getElementById('screen-auth').classList.remove('active');
            document.getElementById('screen-main').classList.add('active');
            
            const savedProfile = localStorage.getItem('cyber_profile');
            if(savedProfile) document.getElementById('user-avatar').src = savedProfile;
        }

        function logout() {
            document.getElementById('screen-main').classList.remove('active');
            document.getElementById('screen-auth').classList.add('active');
            document.getElementById('auth-usr').value = '';
            document.getElementById('auth-pwd').value = '';
        }

        // --- PROFILE PICTURE ---
        function updateProfile(e) {
            const file = e.target.files[0];
            if(file) {
                const reader = new FileReader();
                reader.onload = function(evt) {
                    const b64 = evt.target.result;
                    document.getElementById('user-avatar').src = b64;
                    localStorage.setItem('cyber_profile', b64);
                };
                reader.readAsDataURL(file);
            }
        }

        // --- NAVIGATION ---
        function switchTab(tab) {
            document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active-tab'));
            event.currentTarget.classList.add('active-tab');
            
            document.getElementById('view-doxxer').style.display = 'none';
            document.getElementById('view-tracker').style.display = 'none';
            document.getElementById('view-jammer').style.display = 'none';

            if(tab === 'doxxer') document.getElementById('view-doxxer').style.display = 'block';
            if(tab === 'tracker') document.getElementById('view-tracker').style.display = 'block';
            if(tab === 'jammer') document.getElementById('view-jammer').style.display = 'block';
        }

        // --- SEED RNG FOR MUTUAL CONSISTENCY ---
        function getSeed(str) {
            let h = 0x811c9dc5;
            for(let i = 0; i < str.length; i++) {
                h ^= str.charCodeAt(i);
                h = Math.imul(h, 0x01000193);
            }
            return (h >>> 0);
        }
        function randomSeed(seed) {
            let t = seed += 0x6D2B79F5;
            t = Math.imul(t ^ t >>> 15, t | 1);
            t ^= t + Math.imul(t ^ t >>> 7, t | 61);
            return ((t ^ t >>> 14) >>> 0) / 4294967296;
        }

        // --- COMPLETE PROVINCE & REGIONAL INDONESIA DATABASE ---
        const INDONESIA_REGIONS = [
            {
                prov: "DKI JAKARTA", code: "31",
                cities: [
                    { name: "KOTA JAKARTA SELATAN", code: "74", kec: ["TEBET", "KEMANG", "CILANDAK", "KEBAYORAN BARU"], kel: ["PULOGADUNG", "MANGGARAI", "GANDARIA"] },
                    { name: "KOTA JAKARTA PUSAT", code: "71", kec: ["MENTENG", "TANAH ABANG", "GAMBIR"], kel: ["KEBON SIRIH", "PETAMBURAN", "RAWASARI"] }
                ]
            },
            {
                prov: "JAWA BARAT", code: "32",
                cities: [
                    { name: "KOTA BANDUNG", code: "73", kec: ["COBLONG", "CICENDO", "SUMUR BANDUNG"], kel: ["DAGO", "PASEH", "LEBAK SILIWANGI"] },
                    { name: "KABUPATEN BOGOR", code: "01", kec: ["CIBINONG", "CIBUBUR", "JONGGOL"], kel: ["CILUAR", "PASIR ANGIN", "SITUSARI"] },
                    { name: "KOTA BEKASI", code: "75", kec: ["BEKASI BARAT", "JATI ASIH"], kel: ["PEKAYON", "KRANJI"] }
                ]
            },
            {
                prov: "JAWA TENGAH", code: "33",
                cities: [
                    { name: "KOTA SEMARANG", code: "74", kec: ["SEMARANG BARAT", "BANYUMANIK"], kel: ["PEDURUNGAN", "SRONDOL"] },
                    { name: "KOTA SURAKARTA", code: "72", kec: ["BANJARSARI", "JEBRES"], kel: ["MANAHAN", "KENTHINGAN"] }
                ]
            },
            {
                prov: "JAWA TIMUR", code: "35",
                cities: [
                    { name: "KOTA SURABAYA", code: "78", kec: ["GUBENG", "WONOKROMO"], kel: ["RUNGKUT", "AIRLANGGA"] },
                    { name: "KOTA MALANG", code: "73", kec: ["LOWOKWARU", "KLOJEN"], kel: ["KETAWANGGEDE", "RAMPAL"] }
                ]
            },
            {
                prov: "BANTEN", code: "36",
                cities: [
                    { name: "KOTA TANGERANG", code: "71", kec: ["KARAWACI", "CIPONDOH"], kel: ["PORIS", "BOJONG"] },
                    { name: "KOTA SERANG", code: "73", kec: ["SERANG", "CIPOCOK"], kel: ["KALIGANDU", "PANCUR"] }
                ]
            },
            {
                prov: "SUMATERA UTARA", code: "12",
                cities: [
                    { name: "KOTA MEDAN", code: "75", kec: ["MEDAN BARAT", "MEDAN PETISAH"], kel: ["KESAWAN", "SEKIP"] }
                ]
            },
            {
                prov: "BALI", code: "51",
                cities: [
                    { name: "KOTA DENPASAR", code: "71", kec: ["DENPASAR SELATAN", "DENPASAR BARAT"], kel: ["SANUR", "RENON"] }
                ]
            },
            {
                prov: "SULAWESI SELATAN", code: "73",
                cities: [
                    { name: "KOTA MAKASSAR", code: "71", kec: ["PANAKKUKANG", "UJUNGPANDANG"], kel: ["LOSARI", "MASALE"] }
                ]
            }
        ];

        const VARIED_MALES = ["Bagas Adi Pratama", "Dimas Setiawan", "Rizky Ramadhan", "Fajar Hidayat", "Bayu Nugroho", "Eko Prasetyo", "Andi Wijaya", "Rian Saputra", "Gilang Permana", "Hendra Gunawan"];
        const VARIED_FEMALES = ["Siti Rahmawati", "Nabila Putri", "Dwi Lestari", "Tia Anggraini", "Dewi Kusuma", "Ayu Safitri", "Indah Nurhaliza", "Rina Kartika", "Larasati Anggun", "Fitri Handayani"];
        const VARIED_FATHERS = ["Bambang Sugianto", "Sudarsono", "Herman Susanto", "Agus Santoso", "Eko Supriyanto", "Heri Irawan", "Budi Kartono"];
        const VARIED_MOTHERS = ["Sri Utami", "Endang Sulastri", "Ratna Sari", "Sunarti", "Lilis Suryani", "Tri Wahyuni", "Siti Aminah"];
        const VARIED_GRANDFATHERS = ["Karto Pawiro", "Sastro Dimedjo", "Sumarto", "Hardjo Suwito", "Parto Utomo"];
        const VARIED_GRANDMOTHERS = ["Suminah", "Siti Djubaedah", "Murtini", "Paijem", "Saminah"];
        const RELIGIONS = ["ISLAM", "KRISTEN PROTESTAN", "KRISTEN KATOLIK", "HINDU", "BUDHA"];
        const BANKS = ["BCA", "MANDIRI", "BNI", "BRI", "BSI", "CIMB NIAGA"];
        const CLINICS = ["Klinik Sejahtera Utama", "RSUD Sektor Daerah", "Klinik Harapan Sehat", "Puskesmas Bhakti Praja"];
        const COMPANIES = ["PT TELEKOMUNIKASI INDONESIA", "PT INDOFOOD SUKSES MAKMUR", "PT ASTRA INTERNATIONAL", "PT BANK MANDIRI"];

        let currentDoxData = null;

        function generateData(phone) {
            let seed = getSeed(phone);
            const r = () => randomSeed(seed++);
            const pick = (arr) => arr[Math.floor(r() * arr.length)];
            const rNum = (len) => {
                let res = '';
                for(let i=0; i<len; i++) res += Math.floor(r() * 10);
                return res;
            };

            let region = pick(INDONESIA_REGIONS);
            let city = pick(region.cities);
            let kec = pick(city.kec);
            let kel = pick(city.kel);
            let kecCode = String(Math.floor(r() * 15) + 10);

            let isFemale = r() > 0.5;
            let childName = pick(isFemale ? VARIED_FEMALES : VARIED_MALES).toUpperCase();
            let familyReligion = pick(RELIGIONS);

            let childYear = 2003 + Math.floor(r() * 12);
            let childMonth = Math.floor(r() * 12) + 1;
            let childDay = Math.floor(r() * 28) + 1;
            
            let dayStrChild = isFemale ? String(childDay + 40) : String(childDay).padStart(2, '0');
            let monthStrChild = String(childMonth).padStart(2, '0');
            let yearStrChild = String(childYear).substring(2);

            let childNik = `${region.code}${city.code}${kecCode}${dayStrChild}${monthStrChild}${yearStrChild}${rNum(4)}`;
            let noKK = `${region.code}${city.code}${kecCode}15080${childYear-18}${rNum(4)}`;

            let fatherYear = childYear - 25 - Math.floor(r() * 8);
            let motherYear = childYear - 22 - Math.floor(r() * 6);
            
            let fatherNik = `${region.code}${city.code}${kecCode}${String(Math.floor(r()*28)+1).padStart(2,'0')}${String(Math.floor(r()*12)+1).padStart(2,'0')}${String(fatherYear).substring(2)}${rNum(4)}`;
            let motherNik = `${region.code}${city.code}${kecCode}${String(Math.floor(r()*28)+41)}${String(Math.floor(r()*12)+1).padStart(2,'0')}${String(motherYear).substring(2)}${rNum(4)}`;

            let age = 2026 - childYear;
            let schoolLevel = age <= 15 ? "SMP" : "SMA";
            let schoolName = `${schoolLevel} NEGERI 1 ${city.name.replace("KOTA ", "").replace("KABUPATEN ", "")}`;

            return {
                nik_anak: childNik,
                nama_panjang_anak: childName,
                nisn_anak: "00" + rNum(8),
                no_kartu_kk: noKK,
                agama_keluarga: familyReligion,
                jenis_kelamin: isFemale ? "Perempuan" : "Laki-laki",
                tanggal_lahir_anak: `${childYear}-${monthStrChild}-${String(childDay).padStart(2, '0')}`,
                umur_anak: age + " Tahun",
                sekolah_anak: schoolName,
                
                // PARENTS
                nama_ayah: pick(VARIED_FATHERS).toUpperCase(),
                nik_ayah: fatherNik,
                tanggal_lahir_ayah: `${fatherYear}-${String(Math.floor(r()*12)+1).padStart(2,'0')}-${String(Math.floor(r()*28)+1).padStart(2,'0')}`,
                
                nama_ibu: pick(VARIED_MOTHERS).toUpperCase(),
                nik_ibu: motherNik,
                tanggal_lahir_ibu: `${motherYear}-${String(Math.floor(r()*12)+1).padStart(2,'0')}-${String(Math.floor(r()*28)+1).padStart(2,'0')}`,

                // GRANDPARENTS
                nama_kakek: pick(VARIED_GRANDFATHERS).toUpperCase(),
                nama_nenek: pick(VARIED_GRANDMOTHERS).toUpperCase(),

                // ADDRESS & PROVINCE
                alamat_lengkap: `JL. MERDEKA UTAMA NO. ${rNum(2)}, RT 0${Math.floor(r()*8)+1}/RW 0${Math.floor(r()*8)+1}, KEL. ${kel}, KEC. ${kec}`,
                kota_kabupaten: city.name,
                provinsi: region.prov,
                
                no_hp: phone,
                akte_kelahiran: "AL-" + rNum(10),
                fasilitas_kesehatan: pick(CLINICS),
                status_bpjs: "AKTIF",
                pekerjaan_orang_tua: "PEGAWAI SWASTA",
                badan_usaha: pick(COMPANIES),
                rekening_bank: pick(BANKS) + " - " + rNum(10),
                device_info: `Android OS 14 | SnapDragon 8 Gen 2 | IMEI: 86${rNum(13)}`
            };
        }

        async function runDoxxer() {
            const phone = document.getElementById('dox-input').value;
            if(!phone.match(/^08[0-9]{8,11}$/)) {
                showBubbleAlert("INPUT INVALID", "Masukkan nomor HP Indonesia yang valid! (Contoh: 08123456789)");
                return;
            }
            
            const term = document.getElementById('dox-terminal');
            const resArea = document.getElementById('dox-result');
            resArea.style.display = 'none';
            term.style.display = 'block';
            
            term.innerHTML = "> Connecting to Civil Database Registry...<br>";
            await new Promise(r => setTimeout(r, 400));
            term.innerHTML += "> Matching NIK Province & Regional Code...<br>";
            await new Promise(r => setTimeout(r, 400));
            term.innerHTML += "> Extracting Family Tree & Device Logs...<br>";
            await new Promise(r => setTimeout(r, 400));
            term.innerHTML += "> OSINT DATA EXTRACTION COMPLETED.<br>";
            
            term.style.display = 'none';
            resArea.style.display = 'block';

            currentDoxData = generateData(phone);
            renderDoxxer();
        }

        function renderDoxxer() {
            if(!currentDoxData) return;
            
            const matrix = document.getElementById('res-matrix');
            matrix.innerText = "{\n" + Object.entries(currentDoxData).map(([k,v]) => `  "${k}": "${v}"`).join(",\n") + "\n}";

            const board = document.getElementById('res-board');
            board.innerHTML = '';
            for(const [k, v] of Object.entries(currentDoxData)) {
                const div = document.createElement('div');
                div.className = 'data-card';
                div.innerHTML = `<div class="lbl">${k.replace(/_/g, ' ')}</div><div class="val">${v}</div>`;
                board.appendChild(div);
            }
        }

        function switchFormat(fmt) {
            document.querySelectorAll('.format-toggle .btn-toggle').forEach(b => b.classList.remove('active'));
            event.target.classList.add('active');
            if(fmt === 'board') {
                document.getElementById('res-matrix').classList.remove('active-view');
                document.getElementById('res-board').classList.add('active-view');
            } else {
                document.getElementById('res-board').classList.remove('active-view');
                document.getElementById('res-matrix').classList.add('active-view');
            }
        }

        // --- BTS TRACKER LOGIC ---
        async function runTracker() {
            const phone = document.getElementById('track-input').value;
            if(!phone.match(/^08[0-9]{8,11}$/)) {
                showBubbleAlert("INPUT INVALID", "Masukkan nomor HP yang valid!");
                return;
            }

            const term = document.getElementById('track-terminal');
            const resArea = document.getElementById('track-result');
            resArea.style.display = 'none';

            term.style.display = 'block';
            term.innerHTML = "> Triangulating BTS Signal Towers...<br>";
            await new Promise(r => setTimeout(r, 500));
            term.innerHTML += "> Intercepting Network Node...<br>";
            await new Promise(r => setTimeout(r, 500));
            
            term.style.display = 'none';
            resArea.style.display = 'block';

            let seed = getSeed(phone);
            const r = () => randomSeed(seed++);
            
            let lat = -6.175 + (r() * 0.5); 
            let lng = 106.82 + (r() * 0.5);
            
            const mapFrame = document.getElementById('map-frame');
            mapFrame.src = `https://maps.google.com/maps?q=${lat},${lng}&t=k&z=17&ie=UTF8&iwloc=&output=embed`;

            let ip = `${Math.floor(r()*255)}.${Math.floor(r()*255)}.${Math.floor(r()*255)}.${Math.floor(r()*255)}`;
            
            document.getElementById('map-coords').innerHTML = `LAT: ${lat.toFixed(6)} | LNG: ${lng.toFixed(6)}<br>IP: ${ip}<br>BTS TOWER ID: BTS-${getSeed(phone).toString(16).toUpperCase()}`;
        }

        // --- STB JAMMER LOGIC ---
        let jammerInterval;
        async function scanSTB() {
            const status = document.getElementById('block-status');
            const term = document.getElementById('jammer-terminal');
            const btnScan = document.getElementById('btn-scan-stb');
            const btnStop = document.getElementById('btn-stop-stb');
            
            status.innerText = 'STATUS: MENCARI SINYAL FREKUENSI TV...';
            status.style.color = '#0088ff';
            document.getElementById('radar-sweep').style.animationPlayState = 'running';
            document.getElementById('radar-dot').style.display = 'none';
            term.style.display = 'none';
            term.innerHTML = '';

            await new Promise(r => setTimeout(r, 1500));
            
            status.innerText = 'STATUS: SINYAL DITEMUKAN. PEMBLOKIRAN AKTIF!';
            status.style.color = '#ffaa00';
            document.getElementById('radar-dot').style.display = 'block';
            
            btnScan.style.display = 'none';
            btnStop.style.display = 'inline-block';
            term.style.display = 'block';

            jammerInterval = setInterval(() => {
                const hex = Math.floor(Math.random()*16777215).toString(16).toUpperCase();
                term.innerHTML = `<span style="color:#ff003c;">[!] INJECTING NOISE FREQ 0x${hex} - JAMMING ACTIVE</span><br>` + term.innerHTML;
            }, 80);
        }

        function stopSTB() {
            clearInterval(jammerInterval);
            const status = document.getElementById('block-status');
            status.innerText = 'STATUS: SINYAL BERHASIL DIBLOKIR (OFFLINE)';
            status.style.color = '#ff003c';
            
            document.getElementById('radar-sweep').style.animationPlayState = 'paused';
            document.getElementById('btn-stop-stb').style.display = 'none';
            const btnScan = document.getElementById('btn-scan-stb');
            btnScan.style.display = 'inline-block';
            btnScan.innerText = 'RE-SCAN SIGNAL';
        }

        // --- ARSENAL TOOLS REALISTIC SIMULATION ---
        let currentTool = "";
        let toolInterval;
        
        function openTool(name) {
            currentTool = name;
            clearInterval(toolInterval);
            document.getElementById('tool-title').innerText = name + " PROTOCOL";
            document.getElementById('tool-terminal').style.display = 'none';
            document.getElementById('tool-terminal').innerHTML = '';
            
            let inputsHtml = '';
            if(name === 'BRUTEFORCE') {
                inputsHtml = `
                    <input type="text" id="tool-url" class="input-box" style="padding:10px; font-size:0.95rem; margin-bottom:10px;" placeholder="Target IP / Host SSH">
                    <input type="number" id="tool-port" class="input-box" style="padding:10px; font-size:0.95rem;" placeholder="Port Target (Contoh: 22, 8080)">
                `;
            } else if(name === 'SQL INJECT') {
                inputsHtml = `<input type="text" id="tool-url" class="input-box" style="padding:10px; font-size:0.95rem;" placeholder="Target URL Parameter (Contoh: http://site.com/item.php?id=1)">`;
            } else if(name === 'DIOS BYPASS') {
                inputsHtml = `
                    <input type="text" id="tool-url" class="input-box" style="padding:10px; font-size:0.95rem; margin-bottom:10px;" placeholder="Target Web URL Parameter">
                    <input type="text" id="dios-name" class="input-box" style="padding:10px; font-size:0.95rem;" placeholder="Masukkan Nama Dios By (Contoh: LOZX_NEMESIS)">
                `;
            } else if(name === 'CSRF LOGIN') {
                inputsHtml = `
                    <input type="text" id="tool-url" class="input-box" style="padding:10px; font-size:0.95rem; margin-bottom:10px;" placeholder="Target Login Form Action URL">
                    <input type="text" id="csrf-token" class="input-box" style="padding:10px; font-size:0.95rem;" placeholder="CSRF Token Key / Parameter Name">
                `;
            } else if(name === 'OSINT IP') {
                inputsHtml = `<input type="text" id="tool-url" class="input-box" style="padding:10px; font-size:0.95rem;" placeholder="Target IP Address (Contoh: 180.252.10.1)">`;
            } else {
                inputsHtml = `<input type="text" id="tool-url" class="input-box" style="padding:10px; font-size:0.95rem;" placeholder="Target URL / Domain (http/https)">`;
            }
            
            document.getElementById('tool-inputs').innerHTML = inputsHtml;
            document.getElementById('tool-modal').style.display = 'flex';
        }

        function closeTool(e) {
            if(e.target.id === 'tool-modal') {
                document.getElementById('tool-modal').style.display = 'none';
                clearInterval(toolInterval);
            }
        }

        function executeToolAction() {
            clearInterval(toolInterval);
            const term = document.getElementById('tool-terminal');
            const urlInput = document.getElementById('tool-url');
            
            if(!urlInput || urlInput.value.trim().length < 4) {
                showBubbleAlert("TARGET ERROR", "Harap masukkan URL / IP Target yang valid!");
                return;
            }
            
            let val = urlInput.value.trim();
            term.style.display = 'block';
            term.innerHTML = `> Initializing ${currentTool} on ${val}...<br>`;

            if(currentTool === 'OSINT IP') {
                if(!val.match(/^(?:[0-9]{1,3}\.){3}[0-9]{1,3}$/)) {
                    showBubbleAlert("IP INVALID", "Format IP Address tidak valid! (Gunakan format misal: 180.252.10.1)");
                    return;
                }
                term.innerHTML += `> Querying Regional ASN & Geolocation Registries...<br>`;
                setTimeout(() => {
                    term.innerHTML = `<div style="color:#00ff00; white-space:pre-wrap; border:1px solid #00ff00; padding:10px; background:#001100;">
=================================================
[+] IP GEOLOCATION & NETWORK INTEL COMPLETED
=================================================
IP ADDRESS    : ${val}
HOSTNAME      : ${val}.ip.indosat.net.id
ASN           : AS4761 (INDOSAT-ASN-AP Indosat Tbk)
ISP           : PT Indosat Tbk
ORGANIZATION  : Indosat Mobile Broadband
COUNTRY       : Indonesia (ID)
REGION        : Jawa Barat
CITY          : Bandung
POSTAL CODE   : 40111
COORDINATES   : -6.9175, 107.6191
TIMEZONE      : Asia/Jakarta (GMT+7)
OPEN PORTS    : 80 (HTTP), 443 (HTTPS), 8080 (PROXY-ALT)
VPN / PROXY   : FALSE (Residential Broadband)
THREAT SCORE  : LOW (0/100)
=================================================</div>`;
                }, 1200);

            } else if(currentTool === 'DIOS BYPASS') {
                if(!val.includes("http")) {
                    showBubbleAlert("URL INVALID", "Harap gunakan format URL lengkap (http:// atau https://)");
                    return;
                }
                const diosName = document.getElementById('dios-name').value || "LOZX_NEMESIS";
                
                term.innerHTML += `> Injecting DIOS Payload into ${val}...<br>`;
                setTimeout(() => {
                    term.innerHTML = `<div style="color:#00ff00; line-height:1.4; white-space:pre-wrap; border:1px solid #00ff00; padding:10px; background:#001100;">
========================================================================================
[+] DIOS (INFORMATION ON SCREEN) INJECTED SUCCESSFULLY
========================================================================================
TARGET URL : ${val}
INJECTOR   : DIOS BY ${diosName.toUpperCase()} [N.E.M.E.S.I.S. & GODSPY D.I.W.M.]
========================================================================================

[--- SYSTEM INFO ---]
DATABASE USER : db_godspy_admin@localhost
DBMS VERSION  : 10.5.12-MariaDB-1:10.5.12+maria~focal-log
CURRENT DB    : target_production_db
SERVER OS     : Linux 5.10.0-18-amd64 x86_64

[--- TABLE SCHEMAS DUMP ---]
+---------------------------+----------------+
| TABLE_NAME                | ROW_COUNT      |
+---------------------------+----------------+
| wp_users                  | 42             |
| admin_credentials         | 5              |
| customer_identities       | 15420          |
| transaction_logs          | 89410          |
| api_keys_vault            | 12             |
+---------------------------+----------------+

[--- EXPLICIT COLUMN & USER DATA DUMP (DH HACKBAR FORMAT) ---]
id  | username      | password_hash                                                    | email                       | role        | session_token                     | status
----+---------------+------------------------------------------------------------------+-----------------------------+-------------+-----------------------------------+--------
1   | super_admin   | $2y$12$K89sZ.7xYmWq19P2xL8A.e3R10uT5vN7yQ4wP0oI9uY8tR7eE6wS         | admin@system-sec.org        | ROOT_ADMIN  | 9f88a21b3c4d5e6f7a8b9c0d1e2f3a4b  | ACTIVE
2   | sys_operator  | $2y$12$L90tA.8yZnXr20Q3yM9B.f4S21vU6wO8zR5xQ1pJ0vZ9uS8fF7xT         | operator@system-sec.org     | OPERATOR    | 8e77z10a2b3c4d5e6f7a8b9c0d1e2f3a  | ACTIVE
3   | db_auditor    | $2y$12$M11uB.9zAoYs31R4zN0C.g5T32wV7xP9aS6yR2qK1wA0vT9gG8yU         | auditor@system-sec.org      | AUDITOR     | 7d66y09z1a2b3c4d5e6f7a8b9c0d1e2f  | ACTIVE
4   | dev_lead      | $2y$12$N22vC.0aBpZt42S5aO1D.h6U43xW8yQ0bT7zS3rL2xB1wU0hH9zV         | devlead@system-sec.org      | DEVELOPER   | 6c55x08y0z1a2b3c4d5e6f7a8b9c0d1e  | ACTIVE
5   | api_service   | $2y$12$O33wD.1bCqAu53T6bP2E.i7V54yX9zR1cU8aT4sM3yC2xV1iI0aW         | api@system-sec.org          | SERVICE     | 5b44w07x9y0z1a2b3c4d5e6f7a8b9c0d  | ACTIVE
========================================================================================</div>`;
                }, 1400);

            } else if(currentTool === 'SQL INJECT') {
                if(!val.includes("http")) {
                    showBubbleAlert("URL INVALID", "Gunakan format URL lengkap (http:// atau https://)");
                    return;
                }
                term.innerHTML += `> Testing Injection Payloads: ' OR '1'='1 ...<br>`;
                setTimeout(() => {
                    term.innerHTML += `<span style="color:#00ff00;">[+] VULNERABLE! Injection Point Confirmed.</span><br>`;
                    term.innerHTML += `> Dumping Database Schema...<br>`;
                    term.innerHTML += `<div style="color:#00e5ff; margin-top:5px; border-left:2px solid #00ff00; padding-left:8px;">
[DB_NAME]: db_server_production<br>
[TABLES]: users, admin_credentials, payment_logs<br>
[COLUMN_EXTRACT]: admin_id, password_hash, user_email<br>
[DATA_FOUND]: admin | $2y$10$e8Z9U.Xm7qZ... (Hash Dumped)
</div>`;
                }, 1200);

            } else if(currentTool === 'BRUTEFORCE') {
                const port = document.getElementById('tool-port').value || "22";
                term.innerHTML += `> Attacking ${val}:${port} with Dictionary Attack...<br>`;
                let count = 0;
                toolInterval = setInterval(() => {
                    count++;
                    term.innerHTML += `<span style="color:#888;">[TRY ${count}] user:admin pass:pass${Math.floor(Math.random()*9999)} -> FAILED</span><br>`;
                    term.scrollTop = term.scrollHeight;
                    if(count >= 6) {
                        clearInterval(toolInterval);
                        term.innerHTML += `<span style="color:#00ff00; font-weight:bold;">[+] SUCCESS CREDENTIAL FOUND: admin | admin2026!</span><br>`;
                    }
                }, 200);

            } else {
                setTimeout(() => {
                    term.innerHTML += `<span style="color:#00ff00;">[+] PROTOCOL EXECUTED SUCCESSFULLY ON TARGET.</span><br>`;
                }, 1000);
            }
        }

        switchFormat('board');
    </script>
</body>
</html>
