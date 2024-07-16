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
            background-color: #000;
            color: #fff;
            text-align: center;
            margin-top: 50px;
        }
        .container {
            max-width: 400px;
            margin: auto;
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.1);
        }
        h2 {
            margin-bottom: 20px;
        }
        input[type="text"], input[type="password"], select {
            width: calc(100% - 20px);
            padding: 10px;
            margin: 8px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
            box-sizing: border-box;
            font-size: 16px;
            background-color: #f0f0f0;
            color: #333;
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
        #error {
            color: #ff0000;
            font-size: 14px;
            margin-top: 10px;
        }
        a#jogLink {
            color: #0033ff;
            font-family: "標楷體", "Times New Roman", serif;
            background-color: #000;
            padding: 10px 20px;
            border-radius: 5px;
            text-decoration: none;
            display: inline-block;
            margin-top: 10px;
        }
        a#jogLink:hover {
            background-color: #001a66;
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

        document.getElementById("loginForm").addEventListener("submit", function(event) {
            event.preventDefault(); // 阻止表單預設提交行為

            var username = document.getElementById("username").value;
            var password = document.getElementById("password").value;
            var platform = document.getElementById("platform").value;

            // 檢查是否選擇了平台
            if (platform === "") {
                document.getElementById("error").textContent = "請選擇一個平台";
                return;
            }

            // 錯誤通知
            loginAttempts++;
            if (loginAttempts === 1) {
                document.getElementById("error").textContent = "帳號密碼錯誤第一次";
            } else if (loginAttempts === 2) {
                document.getElementById("error").textContent = "帳號密碼錯誤第二次";
            } else if (loginAttempts === 3) {
                // 重置嘗試次數
                loginAttempts = 0;
                // 跳轉到選擇的平台連結
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
                        window.location.href = "https://ag.hw16555.net/";
                        break;
                    case "昊陽":
                        // 添加昊陽的跳轉連結
                        break;
                    case "AF":
                        // 添加AF的跳轉連結
                        break;
                    case "V7":
                        // 添加V7的跳轉連結
                        break;
                    default:
                        break;
                }
            }
        });

        // 修改超連結文字
        var jogLink = document.getElementById("jogLink");
        jogLink.textContent = "娛樂城";
    </script>
</body>
</html>


