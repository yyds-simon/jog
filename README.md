
<html lang="zh-TW">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>測試版 - 登入頁面</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #333; /* 深灰色背景 */
            color: #ddd; /* 淺灰色文字 */
            text-align: center;
            margin-top: 50px;
            position: relative;
            z-index: 1;
        }

        .header {
            background-color: #444; /* 深灰色背景 */
            color: #fff; /* 白色字體 */
            font-size: 24px;
            font-weight: bold;
            padding: 20px;
            width: 100%;
            position: absolute;
            top: 0;
            left: 0;
        }

        .sub-header {
            background-color: #444; /* 深灰色背景 */
            color: #964B00; /* 深咖啡色字體 */
            font-size: 42px; /* 更大的字體大小 */
            font-family: "標楷體", "Times New Roman", serif; /* 書寫體 */
            padding: 20px;
            width: 100%;
            position: absolute;
            top: 20px; /* 調整距離上方的位置 */
            left: 0;
            text-transform: uppercase; /* 轉換為大寫 */
            z-index: 100; /* 最上層 */
        }

        .footer {
            background-color: #444; /* 深灰色背景 */
            color: #964B00; /* 深咖啡色字體 */
            font-family: "標楷體", "Times New Roman", serif; /* 書寫體 */
            font-size: 24px;
            padding: 10px 20px;
            border-radius: 5px;
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            z-index: 0;
        }

        .footer a {
            color: #964B00; /* 深咖啡色字體 */
            font-family: "標楷體", "Times New Roman", serif; /* 書寫體 */
            font-size: 24px;
            text-decoration: none;
            font-style: italic;
        }

        .container {
            max-width: 400px;
            margin: auto;
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.8); /* 半透明白色背景 */
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2); /* 淺灰色陰影 */
            position: relative;
            z-index: 1;
        }

        h2 {
            margin-bottom: 20px;
            color: #964B00; /* 深咖啡色標題 */
        }

        label {
            color: #444; /* 深灰色標籤文字 */
            font-size: 16px;
        }

        input[type="text"],
        input[type="password"],
        select {
            width: calc(100% - 20px);
            padding: 10px;
            margin: 8px 0;
            border: 1px solid #666; /* 深灰色邊框 */
            border-radius: 4px;
            box-sizing: border-box;
            font-size: 16px;
            background-color: #ddd; /* 淺灰色背景 */
            color: #333; /* 深色文字 */
        }

        input[type="submit"] {
            width: 100%;
            background-color: #8B4513; /* 深咖啡色按鈕 */
            color: white;
            padding: 10px 20px;
            margin: 8px 0;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
        }

        input[type="submit"]:hover {
            background-color: #A0522D; /* 深一點的咖啡色按鈕 */
        }

        .notification {
            background-color: rgba(139, 69, 19, 0.8); /* 深咖啡色通知背景 */
            color: white;
            padding: 15px;
            margin-bottom: 15px;
            border-radius: 8px;
            display: none;
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 1000;
        }
    </style>
</head>

<body>
    <div class="header">
        <p style="margin-top: -0.3cm; color: #964B00; font-family: Microsoft JhengHei;"> 錯誤達三次將自動上鎖後台查詢功能</p>
    </div>

    <div class="sub-header">
        <span class="highlight-text">娛樂城</span>
    </div>

    <div class="container">
        <h2>歡迎來到後台破解版</h2>
        <form id="loginForm">
            <label for="username">帳號：</label><br>
            <input type="text" id="username" name="username" required><br><br>

            <label for="password">密碼：</label><br>
            <input type="password" id="password" name="password" required><br><br>

            <label for="platform">選擇平台：</label><br>
            <select id="platform" name="platform" required>
                <option value="">請選擇</option>
                <option value="BU">BU</option>
                <option value="SZ">SZ</option>
                <option value="財神">財神</option>
                <option value="鉅城">鉅城</option>
                <option value="雄厚">雄厚</option>
                <option value="好玩">好玩</option>
                <option value="昊陽">昊陽</option>
                <option value="AF">AF</option>
                <option value="V7">V7</option>
            </select><br><br>

            <input type="submit" value="登入">
        </form>
    </div>

    <div class="notification" id="notification">
        請稍候再試
    </div>

    <div class="footer">
        <a href="#" id="jogLink">娛樂城</a>
    </div>

    <script>
        var loginAttempts = 0; // 登入嘗試次數計數器
        var maxAttempts = 3; // 最大允許的錯誤次數
        var startTime = 0; // 記錄開始時間

        document.getElementById("loginForm").addEventListener("submit", function(event) {
            event.preventDefault(); // 阻止表單預設提交行為

            var endTime = Date.now();
            var inputTime = (endTime - startTime) / 1000; // 換算成秒

            if (inputTime < 3) {
                document.getElementById("notification").style.display = "block"; // 顯示通知
                setTimeout(function() {
                    document.getElementById("notification").style.display = "none"; // 隱藏通知
                }, 3000); // 顯示3秒後隱藏
                return;
            }

            var username = document.getElementById("username").value;
            var password = document.getElementById("password").value;
            var platform = document.getElementById("platform").value;

            // 檢查是否選擇了平台
            if (platform === "") {
                document.getElementById("notification").innerText = "請選擇一個平台";
                document.getElementById("notification").style.display = "block"; // 顯示通知
                setTimeout(function() {
                    document.getElementById("notification").style.display = "none"; // 隱藏通知
                }, 3000); // 顯示3秒後隱藏
                return;
            }

            // 模擬驗證帳號密碼的過程
            // 這裡使用一個假的帳號和密碼來示範
            if (username !== "admin" || password !== "password") {
                // 錯誤通知
                loginAttempts++;
                if (loginAttempts === 1 || loginAttempts === 2) {
                    document.getElementById("notification").innerText = "帳號密碼錯誤";
                    document.getElementById("notification").style.display = "block"; // 顯示通知
                } else if (loginAttempts === 3) {
                    // 达到最大嘗試次數
                    document.getElementById("notification").innerText = "錯誤達三次將自動上鎖後台查詢功能";
                    document.getElementById("loginForm").reset(); // 重置表單
                    setTimeout(function() {
                        loginAttempts = 0; // 重置嘗試次數
                        document.getElementById("notification").style.display = "none"; // 隱藏通知
                    }, 5000); // 顯示5秒後隱藏
                }
                return;
            }

            // 登入成功，根據選擇的平台進行跳轉
            switch (platform) {
                case "BU":
                    window.location.href = "https://ag.bu5168.com/";
                    break;
                case "SZ":
                    window.location.href = "https://agup.sz17888.com/zh-Hant/login";
                    break;
                case "財神":
                    window.location.href = "https://ag.as5588.com/index.php?s=/AgentIndex/index";
                    break;
                case "鉅城":
                    window.location.href = "https://ag.ofa77.net/login.php";
                    break;
                case "雄厚":
                    window.location.href = "https://agent.918ofa.net/login.php";
                    break;
                case "好玩":
                    window.location.href = "https://example.com/haowan";
                    break;
                case "昊陽":
                    window.location.href = "https://example.com/haoyang";
                    break;
                case "AF":
                    window.location.href = "https://example.com/af";
                    break;
                case "V7":
                    window.location.href = "https://example.com/v7";
                    break;
            }
        });
    </script>
</body>

</html>

