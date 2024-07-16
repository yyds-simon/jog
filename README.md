
<html lang="zh-TW">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>測試版 - 登入頁面</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #222;
            color: #ddd;
            text-align: center;
            margin-top: 50px;
            position: relative; /* 讓內容可以使用絕對定位 */
            z-index: 1; /* 將內容放在最上層 */
        }

        .header {
            background-color: #111;
            color: #888;
            font-size: 24px;
            font-weight: bold;
            padding: 20px;
            width: 100%;
            position: absolute;
            top: 0;
            left: 0;
        }

        .footer {
            background-color: #111;
            color: #aaa; /* 紅色字體 */
            font-family: "Segoe Script", cursive;
            font-size: 24px;
            padding: 10px 20px;
            border-radius: 5px;
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            z-index: 0; /* 將底部長方形放在最底層 */
            background-image: linear-gradient(45deg, #ff0000, #990000); /* 火焰黑底 */
            text-shadow: 0 0 10px #ff0000, 0 0 20px #ff0000, 0 0 40px #ff0000; /* 火焰效果 */
            padding: 15px 30px; /* 增加內邊距 */
        }

        .container {
            max-width: 400px;
            margin: auto;
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.1);
            position: relative;
            z-index: 1;
        }

        h2 {
            margin-bottom: 20px;
            color: #aaa;
            font-size: 28px;
        }

        label {
            color: #ccc;
            font-size: 18px;
        }

        input[type="text"],
        input[type="password"],
        select {
            width: calc(100% - 20px);
            padding: 10px;
            margin: 8px 0;
            border: 1px solid #444;
            border-radius: 4px;
            box-sizing: border-box;
            font-size: 16px;
            background-color: #333;
            color: #ccc;
        }

        input[type="submit"] {
            width: 100%;
            background-color: #555;
            color: #eee;
            padding: 10px 20px;
            margin: 8px 0;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
        }

        input[type="submit"]:hover {
            background-color: #666;
        }

        #error {
            color: #ff6666;
            font-size: 14px;
            margin-top: 10px;
            display: none; /* 預設隱藏 */
        }
    </style>
</head>

<body>
    <div class="header">
        <p style="margin-top: -0.3cm; color: #ffcc00; font-family: Microsoft JhengHei;">錯誤達三次將自動上鎖後台查詢功能</p>
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
        <p id="error"></p>
    </div>

    <div class="footer">
        <a href="#" id="jogLink" style="color: #ff0000;">娛樂城</a>
    </div>

    <script>
        var loginAttempts = 0; // 登入嘗試次數計數器
        var maxAttempts = 3; // 最大允許的錯誤次數
        var startTime = 0; // 記錄開始時間

        document.getElementById("loginForm").addEventListener("submit", function(event) {
            event.preventDefault(); // 阻止表單預設提交行為

            var endTime = Date.now();
            var inputTime = (endTime - startTime) / 1000; // 換算成秒

            if (inputTime < 3) { // 改為三秒
                document.getElementById("error").textContent = "請稍候再試";
                document.getElementById("error").style.display = "block"; // 顯示錯誤訊息
                return;
            }

            var username = document.getElementById("username").value;
            var password = document.getElementById("password").value;
            var platform = document.getElementById("platform").value;

            // 檢查是否選擇了平台
            if (platform === "") {
                document.getElementById("error").textContent = "請選擇一個平台";
                document.getElementById("error").style.display = "block"; // 顯示錯誤訊息
                return;
            }

            // 模擬驗證帳號密碼的過程
            // 這裡使用一個假的帳號和密碼來示範
            if (username !== "admin" || password !== "password") {
                // 錯誤通知
                loginAttempts++;
                if (loginAttempts === 1 || loginAttempts === 2) {
                    document.getElementById("error").textContent = "帳號密碼錯誤";
                    document.getElementById("error").style.display = "block"; // 顯示錯誤訊息
                } else if (loginAttempts === 3) {
                    // 达到最大嘗試次數
                    document.getElementById("error").textContent = "錯誤達三次將自動上鎖後台查詢功能";
                    document.getElementById("loginForm").reset(); // 重置表單
                    setTimeout(function() {
                        loginAttempts = 0; // 重置嘗試次數
                        document.getElementById("error").textContent = "";
                    }, 5000); // 5秒後清除錯誤訊息
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

