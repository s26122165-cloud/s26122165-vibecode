<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>個人數位名片</title>
    <!-- 連結外部 CSS 樣式檔 -->
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <!-- 名片主要卡片 -->
    <div class="profile-card">
        
        <!-- 1. 圓形大頭貼（可替換 src 裡面的圖片網址） -->
        <img class="avatar" src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=400" alt="大頭貼">
        
        <!-- 2. 名字與簡短自我介紹 -->
        <h1 class="name">氏兒潘</h1>
        <p class="bio">✨ 甜點系 UI 設計師，用溫暖的配色打造美好體驗。</p>
        
        <!-- 3. 兩個按鈕 -->
        <div class="button-group">
            <!-- 請將 href="#" 裡面的 # 替換成你的 Instagram 網址 -->
            <a href="#" class="btn btn-instagram" target="_blank">Instagram</a>
            <!-- 請將 your-email@example.com 替換成你的 Email -->
            <a href="mailto:your-email@example.com" class="btn btn-email">Email</a>
        </div>

    </div>

</body>
</html>
/* --- 1. 全局頁面與置中設定 --- */
body {
    margin: 0;
    padding: 0;
    font-family: "PingFang TC", "Microsoft JhengHei", sans-serif;
    /* 馬卡龍淺奶茶色背景 */
    background-color: #FAF5F0; 
    
    /* 讓名片在螢幕正中央 */
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
}

/* --- 2. 卡片主體與馬卡龍風格 --- */
.profile-card {
    background-color: #FFFFFF;
    width: 300px;
    padding: 35px 25px;
    border-radius: 24px; /* 柔和的大圓角 */
    text-align: center;
    
    /* 現代感的軟柔微陰影 */
    box-shadow: 0 12px 30px rgba(235, 178, 178, 0.25);
    
    /* 動畫過渡 */
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

/* 滑鼠移到卡片上的浮起效果 */
.profile-card:hover {
    transform: translateY(-6px);
    box-shadow: 0 18px 35px rgba(235, 178, 178, 0.35);
}

/* --- 3. 圓形大頭貼 --- */
.avatar {
    width: 110px;
    height: 110px;
    border-radius: 50%; /* 正圓形 */
    object-fit: cover;
    margin-bottom: 18px;
    /* 搭配馬卡龍粉色邊框 */
    border: 4px solid #FFE4E6;
}

/* --- 4. 名字與自我介紹 --- */
.name {
    margin: 0 0 8px 0;
    font-size: 22px;
    color: #4A403A; /* 深暖灰，比純黑更有質感 */
    font-weight: 700;
}

.bio {
    margin: 0 0 25px 0;
    font-size: 14px;
    color: #8C7A6B; /* 柔和的奶茶灰色 */
    line-height: 1.5;
}

/* --- 5. 按鈕區塊 --- */
.button-group {
    display: flex;
    flex-direction: column; /* 按鈕上下排列 */
    gap: 12px;              /* 按鈕之間的間距 */
}

/* 基礎按鈕樣式 */
.btn {
    text-decoration: none;
    padding: 12px 20px;
    border-radius: 30px; /* 膠囊圓角 */
    font-size: 14px;
    font-weight: 600;
    letter-spacing: 0.5px;
    transition: all 0.25s ease;
    /* 按鈕微陰影 */
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.04);
}

/* 按鈕 1：馬卡龍甜粉色 (Instagram) */
.btn-instagram {
    background-color: #FFB7B2;
    color: #FFFFFF;
}

.btn-instagram:hover {
    background-color: #FF9E99;
    box-shadow: 0 6px 15px rgba(255, 183, 178, 0.5);
}

/* 按鈕 2：馬卡龍粉紫色 (Email) */
.btn-email {
    background-color: #E2C0EC;
    color: #FFFFFF;
}

.btn-email:hover {
    background-color: #D6A8E2;
    box-shadow: 0 6px 15px rgba(226, 192, 236, 0.5);
}
