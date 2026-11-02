<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>個人數位名片</title>
    <style>
        /* --- 1. 全局頁面與動態馬卡龍柔光背景 --- */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: "PingFang TC", "Microsoft JhengHei", -apple-system, BlinkMacSystemFont, "SF Pro Display", sans-serif;
            background: #FAF4F0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
            overflow-x: hidden;
            position: relative;
        }

        /* 柔和環境氣氛燈光飾球 */
        body::before, body::after {
            content: "";
            position: absolute;
            width: 300px;
            height: 300px;
            border-radius: 50%;
            filter: blur(80px);
            z-index: 0;
            opacity: 0.6;
            animation: pulseGlow 8s ease-in-out infinite alternate;
        }

        body::before {
            background: #FFD1DC; /* 馬卡龍草莓粉 */
            top: 10%;
            left: 15%;
        }

        body::after {
            background: #E8DFF5; /* 馬卡龍柔粉紫 */
            bottom: 10%;
            right: 15%;
            animation-delay: -4s;
        }

        @keyframes pulseGlow {
            0% { transform: scale(1) translate(0, 0); }
            100% { transform: scale(1.15) translate(20px, -20px); }
        }

        /* --- 2. 玻璃擬態質感名片卡片 --- */
        .profile-card {
            position: relative;
            z-index: 1;
            background: rgba(255, 255, 255, 0.75);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            width: 100%;
            max-width: 340px;
            padding: 40px 28px 35px;
            border-radius: 30px;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.9);
            box-shadow: 
                0 20px 40px rgba(230, 180, 190, 0.2),
                0 2px 6px rgba(255, 255, 255, 0.8) inset;
            animation: fadeInUp 0.8s cubic-bezier(0.16, 1, 0.3, 1);
            transition: transform 0.4s ease, box-shadow 0.4s ease;
        }

        .profile-card:hover {
            transform: translateY(-8px);
            box-shadow: 
                0 28px 50px rgba(220, 160, 175, 0.3),
                0 2px 8px rgba(255, 255, 255, 0.9) inset;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(25px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* --- 3. 光芒圓形大頭貼 --- */
        .avatar-container {
            position: relative;
            width: 116px;
            height: 116px;
            margin: 0 auto 20px;
        }

        /* 頭像後方馬卡龍漸層光暈 */
        .avatar-container::before {
            content: "";
            position: absolute;
            inset: -4px;
            border-radius: 50%;
            background: linear-gradient(135deg, #FFB7B2, #E2C0EC, #FFDAC1);
            z-index: 0;
            animation: spin 10s linear infinite;
        }

        @keyframes spin {
            100% { transform: rotate(360deg); }
        }

        .avatar {
            position: relative;
            z-index: 1;
            width: 100%;
            height: 100%;
            border-radius: 50%;
            object-fit: cover;
            border: 3.5px solid #FFFFFF;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.06);
            transition: transform 0.4s ease;
        }

        .avatar-container:hover .avatar {
            transform: scale(1.04);
        }

        /* --- 4. 名字與簡介區域 --- */
        .badge {
            display: inline-block;
            background: linear-gradient(135deg, #FFF0F3, #F6E6FF);
            color: #B565A7;
            font-size: 11px;
            font-weight: 700;
            letter-spacing: 1px;
            padding: 4px 12px;
            border-radius: 20px;
            margin-bottom: 10px;
            border: 1px solid rgba(226, 192, 236, 0.4);
        }

        .name {
            margin: 0 0 10px 0;
            font-size: 25px;
            color: #3D3430;
            font-weight: 800;
            letter-spacing: 0.5px;
        }

        .bio {
            margin: 0 0 28px 0;
            font-size: 13.5px;
            color: #7A6B63;
            line-height: 1.65;
            font-weight: 400;
            padding: 0 4px;
        }

        /* --- 5. 按鈕區塊與漸層光澤 --- */
        .button-group {
            display: flex;
            flex-direction: column;
            gap: 14px;
        }

        .btn {
            position: relative;
            text-decoration: none;
            padding: 14px 22px;
            border-radius: 25px;
            font-size: 14px;
            font-weight: 700;
            letter-spacing: 0.6px;
            transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            overflow: hidden;
            box-shadow: 0 6px 18px rgba(0, 0, 0, 0.05);
        }

        /* 按鈕反光閃亮效果 */
        .btn::after {
            content: "";
            position: absolute;
            top: -50%;
            left: -60%;
            width: 50%;
            height: 200%;
            background: linear-gradient(90deg, rgba(255,255,255,0) 0%, rgba(255,255,255,0.4) 50%, rgba(255,255,255,0) 100%);
            transform: rotate(25deg);
            transition: all 0.6s ease;
        }

        .btn:hover::after {
            left: 120%;
        }

        /* 按鈕 1：草莓糖霜粉橘漸層 (Instagram) */
        .btn-instagram {
            background: linear-gradient(135deg, #FFB7B2 0%, #FFDAC1 100%);
            color: #7F2F2B;
        }

        .btn-instagram:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 22px rgba(255, 183, 178, 0.45);
        }

        /* 按鈕 2：芋泥冰淇淋紫漸層 (Email) */
        .btn-email {
            background: linear-gradient(135deg, #E2C0EC 0%, #C7CEEA 100%);
            color: #4A3059;
        }

        .btn-email:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 22px rgba(226, 192, 236, 0.45);
        }
    </style>
</head>
<body>

    <!-- 名片主要卡片 -->
    <div class="profile-card">
        
        <!-- 1. 圓形大頭貼與漸層環 -->
        <div class="avatar-container">
            <img class="avatar" 
                 src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=400" 
                 alt="潘氏兒的大頭貼"
                 onerror="this.src='https://placehold.co/110x110/FFE4E6/4A403A?text=Avatar'">
        </div>
        
        <!-- 2. 小標籤、名字與簡短自我介紹 -->
        <div class="badge">DESIGNER</div>
        <h1 class="name">潘氏兒</h1>
        <p class="bio">✨ 甜點系 UI 設計師，用溫暖的配色打造美好體驗。</p>
        
        <!-- 3. 按鈕區塊 -->
        <div class="button-group">
            <a href="#" class="btn btn-instagram" target="_blank" rel="noopener noreferrer">
                <span>Instagram</span>
            </a>
            <a href="mailto:your-email@example.com" class="btn btn-email">
                <span>Email 聯絡我</span>
            </a>
        </div>

    </div>

</body>
</html>
