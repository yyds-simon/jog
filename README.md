<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>娛樂城後台總結 - 登入頁面</title>
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
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            margin-bottom: 20px;
            color: #000; /* 將標題字體顏色設為黑色 */
        }
        input[type="text"], input[type="password"], select {
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
        <h2>歡迎來到測試版後台總結</h2>
        <form id="loginForm" action="#">
            <label for="username">帳號：</label><br>
            <input type="text" id="username" name="username" placeholder="請輸入帳號" required><br><br>
            
            <label for="password">密碼：</label><br>
            <input type="password" id="password" name="password" placeholder="請輸入密碼" required><br><br>
            
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
    </div>

    <script>
        // 初始設置，第一次登入帳密錯誤
        var firstAttempt = true;

        document.getElementById("loginForm").addEventListener("submit", function(event) {
            event.preventDefault(); // 阻止表單預設提交行為

            // 獲取表單資料
            var username = document.getElementById("username").value;
            var password = document.getElementById("password").value;
            var platform = document.getElementById("platform").value;

            // 驗證帳密
            if (firstAttempt) {
                // 第一次登入一律顯示帳密錯誤
                alert("帳號或密碼錯誤！");
                firstAttempt = false;
                return;
            }

            // 根據選擇的平台進行不同的引導
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
                    window.location.href = "https://agup.hyg889.com/zh-Hant/login";
                    break;
                case "AF":
                    window.location.href = "https://ag.af7688.com/";
                    break;
                case "V7":
                    window.location.href = "https://agent.v7-bet.net/login.php";
                    break;
                default:
                    break;
            }
        });
    </script>
</body>
</html>
