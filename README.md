<測試版！登入只有三次機會！否則封鎖ＩＰ>
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>測試版 - 登入頁面</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            text-align: center;
            margin-top: 50px;
        }
        .container {
            max-width: 400px;
            margin: auto;
            padding: 20px;
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            margin-bottom: 20px;
        }
        input[type="text"], input[type="password"] {
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
            background-color: #4CAF50;
            color: white;
            padding: 10px 20px;
            margin: 8px 0;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
        }
        input[type="submit"]:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>歡迎來到測試版</h2>
        <form id="loginForm">
            <label for="username">帳號：</label><br>
            <input type="text" id="username" name="username" required><br><br>
            
            <label for="password">密碼：</label><br>
            <input type="password" id="password" name="password" required><br><br>
            
            <label for="platform">選擇平台：</label><br>
            <select id="platform" name="platform">
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

        document.getElementById("loginForm").addEventListener("submit", function(event) {
            event.preventDefault(); // 阻止表單預設提交行為

            var username = document.getElementById("username").value;
            var password = document.getElementById("password").value;

            // 假設這裡是你的帳號密碼驗證邏輯，這裡只是示例
            if (username === "admin" && password === "password") {
                // 登入成功
                window.location.href = getRedirectUrl(); // 取得跳轉連結
            } else {
                // 登入失敗
                loginAttempts++;
                displayErrorMessage();
            }
        });

        function displayErrorMessage() {
            var errorElement = document.getElementById("error");
            if (loginAttempts === 1) {
                errorElement.textContent = "錯誤帳號密碼第一次！";
            } else if (loginAttempts === 2) {
                errorElement.textContent = "錯誤帳號密碼第二次！";
            } else if (loginAttempts >= maxAttempts) {
                errorElement.textContent = "錯誤帳號密碼第三次！";
                setTimeout(function() {
                    window.location.href = getRedirectUrl(); // 第三次錯誤後跳轉
                }, 1000); // 延遲一秒再跳轉，可根據需求調整
            }
        }

        function getRedirectUrl() {
            var platform = document.getElementById("platform").value;
            switch (platform) {
                case "BU":
                    return "https://ag.bu5168.com/";
                case "SZ":
                    return "https://agup.sz17888.com/zh-Hant/login";
                case "財神":
                    return "https://ag.as5588.com/index.php?s=/AgentIndex/index";
                case "鉅城":
                    return "https://ag.ofa77.net/login.php";
                case "雄厚":
                    return "https://agent.918ofa.net/login.php";
                case "好玩":
                    return "https://ag.hw16555.net/";
                case "昊陽":
                    return "https://agup.hyg889.com/zh-Hant/login";
                case "AF":
                    return "https://ag.af7688.com/";
                case "V7":
                    return "https://agent.v7-bet.net/login.php";
                default:
                    return ""; // 如果沒有選擇平台，返回空字串或其他預設值
            }
        }
    </script>
</body>
</html>
