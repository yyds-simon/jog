
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

        .container {
            max-width: 400px;
            margin: auto;
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.8); /* 半透明白色背景 */
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2); /* 阴影 */
            position: relative;
            z-index: 1;
        }

        h2 {
            margin-bottom: 20px;
        }

        input[type="text"],
        input[type="password"],
        select {
            width: calc(100% - 20px);
            padding: 10px;
            margin: 8px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
            box-sizing: border-box;
            font-size: 16px;
        }

        input[type="submit"] {
            width: 100%;
            background-color: #4CAF50; /* 绿色按钮 */
            color: white;
            padding: 10px 20px;
            margin: 8px 0;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
        }

        input[type="submit"]:hover {
            background-color: #45a049; /* 按钮悬停时的颜色 */
        }

        #error {
            color: #ff0000;
            font-size: 14px;
            margin-top: 10px;
            display: none;
        }
    </style>
</head>

<body>
    <div class="header">
        <p>娛樂城</p>
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

    <script>
        var loginAttempts = 0; // 登入嘗試次數計數器
        var maxAttempts = 3; // 最大允許的錯誤次數
        var startTime = 0; // 記錄開始時間

        document.getElementById("loginForm").addEventListener("submit", function(event) {
            event.preventDefault(); // 阻止表單預設提交行為

            var endTime = Date.now();
            var inputTime = (endTime - startTime) / 1000; // 計算輸入時間（秒）

            if (inputTime < 4) {
                document.getElementById("error").textContent = "請稍候再試";
                document.getElementById("error").style.display = "block";
                return;
            }

            var username = document.getElementById("username").value;
            var password = document.getElementById("password").value;
            var platform = document.getElementById("platform").value;

            // 檢查是否選擇了平台
            if (platform === "") {
                document.getElementById("error").textContent = "請選擇一個平台";
                document.getElementById("error").style.display = "block";
                return;
            }

            // 模擬驗證帳號密碼的過程（這裡使用假的帳號密碼來示範）
            if (username !== "admin" || password !== "password") {
                // 錯誤通知
                loginAttempts++;
                if (loginAttempts === 1) {
                    document.getElementById("error").textContent = "帳號密碼錯誤第一次";
                    document.getElementById("error").style.display = "block";
                } else if (loginAttempts === 2) {
                    document.getElementById("error").textContent = "帳號密碼錯誤第二次";
                    document.getElementById("error").style.display = "block";
                } else if (loginAttempts === 3) {
                    // 第三次直接跳轉
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
                            window.location.href = "https://haoyang.com";
                            break;
                        case "AF":
                            window.location.href = "https://af.com";
                            break;
                        case "V7":
                            window.location.href = "https://v7.com";
                            break;
                        default:
                            break;
                    }
                }
                return;
            }
        });
    </script>
</body>

</html>
