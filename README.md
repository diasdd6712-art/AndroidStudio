<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Жаңа Activity қосу</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: #f5f5f5;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .container {
            background: #ffffff;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            width: 100%;
            max-width: 500px;
            padding: 30px;
        }

        h1 {
            color: #333;
            font-size: 24px;
            margin-bottom: 20px;
            border-bottom: 2px solid #4CAF50;
            padding-bottom: 10px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            color: #555;
            font-size: 14px;
            margin-bottom: 8px;
            font-weight: 500;
        }

        input[type="text"] {
            width: 100%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 14px;
            font-family: 'Courier New', monospace;
        }

        input[type="text"]:focus {
            outline: none;
            border-color: #4CAF50;
        }

        .btn-primary {
            background: #4CAF50;
            color: white;
            border: none;
            padding: 14px 28px;
            font-size: 16px;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
            transition: background 0.3s;
        }

        .btn-primary:hover {
            background: #45a049;
        }

        /* Нәтиже бөлімі */
        .result-section {
            margin-top: 30px;
            padding-top: 20px;
            border-top: 1px solid #e0e0e0;
            display: none;
        }

        .result-section.show {
            display: block;
        }

        .file-block {
            background: #263238;
            border-radius: 4px;
            padding: 16px;
            margin-bottom: 16px;
            overflow-x: auto;
        }

        .file-header {
            color: #81C784;
            font-size: 12px;
            margin-bottom: 8px;
            font-weight: bold;
        }

        .code-content {
            color: #aed581;
            font-family: 'Courier New', monospace;
            font-size: 13px;
            line-height: 1.6;
            white-space: pre-wrap;
        }

        .code-tag { color: #FF8A65; }
        .code-attr { color: #64B5F6; }
        .code-value { color: #FFF176; }
        .code-comment { color: #90A4AE; }

        /* ҚЫЗҒЫЛТ САРЫ МӘТІН */
        .success-message {
            margin-top: 20px;
            padding: 16px;
            background: #FFF8E1;
            border-left: 4px solid #FFB300;
            border-radius: 4px;
        }

        .highlight-text {
            font-size: 18px;
            font-weight: 700;
            color: #FF6F00;
            text-shadow: 1px 1px 2px rgba(255, 111, 0, 0.3);
        }

        .info-text {
            color: #666;
            font-size: 13px;
            margin-top: 8px;
        }

        .check-icon {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 20px;
            height: 20px;
            background: #4CAF50;
            color: white;
            border-radius: 50%;
            font-size: 12px;
            margin-right: 8px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>📝 Жаңа Activity қосу</h1>
        
        <div class="form-group">
            <label for="activityName">Activity атауы:</label>
            <input type="text" id="activityName" placeholder="Мысалы: SecondActivity" value="SecondActivity">
        </div>

        <div class="form-group">
            <label for="packageName">Package атауы:</label>
            <input type="text" id="packageName" placeholder="com.example.myapp" value="com.example.myapp">
        </div>

        <button class="btn-primary" onclick="generateFiles()">
            Жасау
        </button>

        <div id="resultSection" class="result-section">
            <!-- Java файлы -->
            <div class="file-block">
                <div class="file-header">📄 SecondActivity.java</div>
                <div class="code-content" id="javaCode"></div>
            </div>

            <!-- Layout файлы -->
            <div class="file-block">
                <div class="file-header">📄 activity_second.xml</div>
                <div class="code-content" id="layoutCode"></div>
            </div>

            <!-- Manifest жаңартылуы -->
            <div class="file-block">
                <div class="file-header">📄 AndroidManifest.xml (автоматты түрде жаңартылды)</div>
                <div class="code-content" id="manifestCode"></div>
            </div>

            <!-- Қызғылт сары мәтін -->
            <div class="success-message">
                <p class="highlight-text">
                    <span class="check-icon">✓</span>
                    Activity сәтті қосылды! Manifest автоматты түрде жаңартылды.
                </p>
                <p class="info-text">
                    Енді жаңа экранға өту үшін Intent қолданыңыз.
                </p>
            </div>
        </div>
    </div>

    <script>
        function generateFiles() {
            const activityName = document.getElementById('activityName').value || 'SecondActivity';
            const packageName = document.getElementById('packageName').value || 'com.example.myapp';
            
            // Java коды
            const javaCode = `<span class="code-tag">package</span> ${packageName};

<span class="code-tag">import</span> android.os.Bundle;
<span class="code-tag">import</span> androidx.appcompat.app.AppCompatActivity;

<span class="code-tag">public class</span> <span class="code-attr">${activityName}</span> <span class="code-tag">extends</span> AppCompatActivity {
    <span class="code-attr">@Override</span>
    <span class="code-tag">protected void</span> <span class="code-attr">onCreate</span>(Bundle savedInstanceState) {
        <span class="code-tag">super</span>.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);
    }
}`;

            // Layout коды
            const layoutCode = `<span class="code-tag">&lt;?xml version="1.0" encoding="utf-8"?&gt;</span>
<span class="code-tag">&lt;LinearLayout</span> 
    xmlns:android=<span class="code-value">"http://schemas.android.com/apk/res/android"</span>
    android:layout_width=<span class="code-value">"match_parent"</span>
    android:layout_height=<span class="code-value">"match_parent"</span>
    android:orientation=<span class="code-value">"vertical"</span>
    android:gravity=<span class="code-value">"center"</span><span class="code-tag">&gt;</span>

    <span class="code-tag">&lt;TextView</span>
        android:layout_width=<span class="code-value">"wrap_content"</span>
        android:layout_height=<span class="code-value">"wrap_content"</span>
        android:text=<span class="code-value">"Бұл жаңа Activity!"</span>
        android:textSize=<span class="code-value">"24sp"</span> <span class="code-tag">/&gt;</span>

<span class="code-tag">&lt;/LinearLayout&gt;</span>`;

            // Manifest коды
            const manifestCode = `<span class="code-tag">&lt;activity</span>
    android:name=<span class="code-value">".${activityName}"</span>
    android:label=<span class="code-value">"@string/title_${activityName.toLowerCase()}"</span> <span class="code-tag">/&gt;</span>

<span class="code-comment">&lt;!-- Автоматты түрде AndroidManifest.xml-ге қосылды --&gt;</span>`;

            // Кодтарды көрсету
            document.getElementById('javaCode').innerHTML = javaCode;
            document.getElementById('layoutCode').innerHTML = layoutCode;
            document.getElementById('manifestCode').innerHTML = manifestCode;
            
            // Нәтиже бөлімін көрсету
            document.getElementById('resultSection').classList.add('show');
        }
    </script>
</body>
</html>
