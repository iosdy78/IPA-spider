<!DOCTYPE html>  
<html lang="ar" dir="rtl">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">  
    <title>IPA spider | KSign</title>  
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">  
    <style>  
        * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }  
          
        body {  
            background-color: #000;  
            margin: 0;  
            padding: 20px;  
            color: white;  
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;  
            display: flex;  
            flex-direction: column;  
            align-items: center;  
            min-height: 100vh;  
        }  
  
        /* توهج الخلفية */  
        body::before {  
            content: "";  
            position: fixed;  
            top: 0; left: 0; width: 100%; height: 100%;  
            background:   
                radial-gradient(circle at 15% 15%, rgba(0, 212, 255, 0.15) 0%, transparent 40%),  
                radial-gradient(circle at 85% 85%, rgba(255, 68, 68, 0.15) 0%, transparent 40%);  
            z-index: -1;  
        }  
  
        .header {  
            text-align: center;  
            margin: 40px 0;  
        }  
  
        .header h1 {  
            font-size: 3.2rem;  
            margin: 0;  
            font-weight: 900;  
            background: linear-gradient(180deg, #ffffff 0%, #aaaaaa 100%);  
            -webkit-background-clip: text;  
            -webkit-text-fill-color: transparent;  
        }  
  
        .header p {  
            color: #00d4ff;  
            font-size: 0.75rem;  
            letter-spacing: 4px;  
            margin-top: 5px;  
            font-weight: bold;  
        }  
  
        .glass-panel {  
            background: rgba(20, 20, 25, 0.6);  
            backdrop-filter: blur(25px);  
            -webkit-backdrop-filter: blur(25px);  
            border: 1px solid rgba(255, 255, 255, 0.1);  
            border-radius: 35px;  
            padding: 25px;  
            width: 100%;  
            max-width: 420px;  
            box-shadow: 0 40px 100px rgba(0,0,0,0.8);  
        }  
  
        .grid {  
            display: flex;  
            flex-direction: column;  
            gap: 16px;  
        }  
  
        .app-item {  
            background: rgba(255, 255, 255, 0.04);  
            border: 1px solid rgba(255, 255, 255, 0.06);  
            border-radius: 22px;  
            padding: 16px;  
            display: flex;  
            align-items: center;  
            text-decoration: none;  
            transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);  
        }  
  
        .app-item:active {  
            transform: scale(0.96);  
            background: rgba(255, 255, 255, 0.1);  
        }  
  
        .icon-wrapper {  
            width: 54px; height: 54px;  
            border-radius: 50%;  
            display: flex; align-items: center; justify-content: center;  
            margin-left: 15px;  
            position: relative;  
            background: rgba(0,0,0,0.2);  
            border: 1.5px solid rgba(255,255,255,0.1);  
        }  
  
        .icon-wrapper::before {  
            content: "";  
            position: absolute;  
            inset: -3px;  
            border-radius: 50%;  
            border: 2px solid transparent;  
            mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);  
            -webkit-mask-composite: xor;  
            mask-composite: exclude;  
        }  
  
        .content { flex-grow: 1; text-align: right; }  
        .content b { display: block; font-size: 1.1rem; color: #fff; margin-bottom: 2px; }  
        .content span { font-size: 0.75rem; color: #888; display: block; }  
  
        .chevron { color: #555; font-size: 0.9rem; margin-right: 10px; }  
  
        /* تلوين الأيقونات بالتناوب */  
        .type-0 .icon-wrapper::before { border-color: #00d4ff; }  
        .type-0 .icon-wrapper { color: #00d4ff; box-shadow: 0 0 15px rgba(0, 212, 255, 0.2); }  
          
        .type-1 .icon-wrapper::before { border-color: #ff4444; }  
        .type-1 .icon-wrapper { color: #ff4444; box-shadow: 0 0 15px rgba(255, 68, 68, 0.2); }  
  
        .type-2 .icon-wrapper::before { border-color: #ffcc00; }  
        .type-2 .icon-wrapper { color: #ffcc00; box-shadow: 0 0 15px rgba(255, 204, 0, 0.2); }  
  
        .type-3 .icon-wrapper::before { border-color: #a066ff; }  
        .type-3 .icon-wrapper { color: #a066ff; box-shadow: 0 0 15px rgba(160, 102, 255, 0.2); }  
  
        .footer {  
            margin-top: 40px;  
            text-align: center;  
            padding-bottom: 40px;  
        }  
  
        .footer p {  
            font-size: 0.65rem;  
            color: #444;  
            letter-spacing: 2px;  
        }  
    </style>  
</head>  
<body>  
  
    <div class="header">  
        <h1>IPA spider</h1>  
        <p>PROJECT VOID SYSTEM</p>  
    </div>  
  
    <div class="glass-panel">  
        <div class="grid" id="mainGrid"></div>  
    </div>  
  
    <div class="footer">  
        <p>BUILT FOR PERFORMANCE. DESIGNED FOR YOU.</p>  
    </div>  
  
    <script>  
        // الروابط العشرين بالترتيب كما طلبت  
        const appLinks = [  
            "https://api.khoindvn.io.vn/JnAsbd",  
            "https://api.khoindvn.io.vn/enw3mG",  
            "https://api.khoindvn.io.vn/03zH0o",  
            "https://api.khoindvn.io.vn/xuuKqO",  
            "https://api.khoindvn.io.vn/xuuKqO",  
            "https://api.khoindvn.io.vn/QdVVh3",  
            "https://api.khoindvn.io.vn/t1UK1D",  
            "https://api.khoindvn.io.vn/NU8PP6",  
            "https://api.khoindvn.eu.org/XSCvQT",  
            "https://api.khoindvn.io.vn/g65UJy",  
            "https://api.khoindvn.io.vn/ZsgCVX",  
            "https://api.khoindvn.io.vn/VNNlkL",  
            "https://api.khoindvn.io.vn/9VDZ4Y",  
            "https://api.khoindvn.io.vn/h5YrG1",  
            "https://api.khoindvn.io.vn/TsTFIu",  
            "https://api.khoindvn.io.vn/IUurbX",  
            "https://api.khoindvn.io.vn/5PBonm",  
            "https://api.khoindvn.io.vn/1H9iee",  
            "https://api.khoindvn.io.vn/qYiNnB",  
            "https://api.khoindvn.io.vn/qYiNnB"  
        ];  
  
        const icons = ['fa-shield-halved', 'fa-download', 'fa-cube', 'fa-wand-magic-sparkles'];  
        const descriptions = ['Advanced Signing Service', 'Powerful Installation', 'Secure Environment', 'Explore & Expand'];  
          
        const grid = document.getElementById('mainGrid');  
  
        appLinks.forEach((link, i) => {  
            const type = i % 4;  
            const card = document.createElement('a');  
            card.href = link;  
            card.target = "_blank"; // لفتح الرابط في صفحة جديدة  
            card.className = `app-item type-${type}`;  
            card.innerHTML = `  
                <div class="icon-wrapper">  
                    <i class="fas ${icons[type]}"></i>  
                </div>  
                <div class="content">  
                    <b>KSign ${i + 1}</b>  
                    <span>${descriptions[type]}</span>  
                </div>  
                <i class="fas fa-chevron-left chevron"></i>  
            `;  
            grid.appendChild(card);  
        });  
    </script>  
</body>  
</html>  
pages:  
  stage: deploy  
  script:  
    - mkdir .public  
    - cp -r * .public  
    - mv .public public  
  artifacts:  
    paths:  
      - public  
  only:  
    - main  
