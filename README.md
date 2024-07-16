
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
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2); /* 淺灰色陰影 */
            position: relative;
            z-index: 1;
        }

        .sub-header {
            margin-bottom: 20px;
            color: #964B00; /* 深咖啡色字體 */
            font-size: 24px; /* 字體大小 */
            font-family: "標楷體", "Times New Roman", serif; /* 書寫體 */
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
            background-color: rgba(255, 255, 255, 0.8); /* 半透明白色通知背景 */
            color: white; /* 白色文字 */
            padding: 15px;
            margin-bottom: 15px;
            border-radius: 8px;
            display: none;
            font-family: "標楷體", "Times New Roman", serif; /* 書寫體 */
            text-shadow: -1px -1px 0 black, 1px -1px 0 black, -1px 1px 0 black, 1px 1px 0 black; /* 黑色描邊 */
            position: fixed;
            bottom: 20px;
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

    <div class="container">
        <div class="sub-header">
            娛樂城<br>
            歡迎來到後台破解版
        </div>

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

    <script>
        var loginAttempts = 0; // 登入嘗試次數計數器
        var maxAttempts = 3; // 最大允許的錯誤次數
        var startTime = 0; // 記錄開始時間

        document.getElementById("loginForm").addEventListener("submit", function(event) {
            event.preventDefault(); // 阻止表單預設提交行為

            var endTime = Date.now();
            var inputTime = (endTime - startTime) / 1000; // 換算成秒

            if (inputTime < 3) {
                document.getElementById("notification").innerText = "請稍候再試";
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
                }, 3000); // 顯示3秒後
                return;
            }

            // 模擬驗證帳號密碼的過程
            // 這裡使用了一個假定的驗證函數
            var authenticated = validateUser(username, password, platform);

            if (authenticated) {
                // 登入成功，導向目標平台
                window.location.href = "https://example.com/" + platform;
            } else {
                // 登入失敗，增加嘗試次數計數
                loginAttempts++;

                if (loginAttempts >= maxAttempts) {
                    document.getElementById("notification").innerText = "錯誤達三次將自動上鎖後台查詢功能";
                } else {
                    document.getElementById("notification").innerText = "帳號或密碼錯誤，請再試一次";
                }

                document.getElementById("notification").style.display = "block"; // 顯示通知
                setTimeout(function() {
                    document.getElementById("notification").style.display = "none"; // 隱藏通知
                }, 3000); // 顯示3秒後
            }
        });

        function validateUser(username, password, platform) {
            // 此處模擬驗證函數，假設帳號為 admin，密碼為 admin，並且平台不為空
            return username === "admin" && password === "admin" && platform !== "";
        }
    </script>
</body>

</html>

