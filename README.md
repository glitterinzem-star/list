<html lang="ru">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>🎄 Fame List - Новогодняя версия</title>
  <style>
    :root{
      --bg:#071017;
      --card:#0f1720;
      --muted:#98a0ab;
      --accent:#ffb86b;
      --glass: rgba(255,255,255,0.03);
      --holly-red: #ff4757;
      --holly-green: #2ecc71;
      --snow: #f1f2f6;
    }

    /* Reset-ish */
    *{box-sizing:border-box}
    html,body{height:100%}
    body{margin:0;font-family:'Segoe UI', Inter, Arial, sans-serif;background:linear-gradient(180deg, #0a1a2a, #03121a);color:#e6eef6;-webkit-font-smoothing:antialiased;position:relative;overflow-x:hidden;}
    .container{max-width:1100px;margin:0 auto;padding:20px;position:relative;z-index:2}

    /* Снежинки */
    .snowflake {
      position: fixed;
      top: -10px;
      color: var(--snow);
      font-size: 1em;
      opacity: 0.8;
      z-index: 1;
      pointer-events: none;
      user-select: none;
    }

    /* Гирлянды */
    .garland {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 40px;
      z-index: 5;
      pointer-events: none;
    }
    
    .light {
      position: absolute;
      width: 12px;
      height: 12px;
      border-radius: 50%;
      animation: twinkle 1.5s infinite alternate;
      top: 10px;
    }
    
    @keyframes twinkle {
      0%, 100% { opacity: 0.3; }
      50% { opacity: 1; }
    }

    /* Новогодние украшения */
    .holly {
      position: fixed;
      width: 40px;
      height: 40px;
      z-index: 1;
      pointer-events: none;
      opacity: 0.7;
    }
    
    .holly::before, .holly::after {
      content: '';
      position: absolute;
      width: 100%;
      height: 100%;
      background-image: radial-gradient(circle at 30% 30%, var(--holly-red), transparent 70%);
      border-radius: 50% 50% 50% 0;
      transform: rotate(45deg);
    }
    
    .holly::after {
      background-image: radial-gradient(circle at 70% 30%, var(--holly-green), transparent 70%);
      border-radius: 50% 50% 0 50%;
      transform: rotate(-45deg);
    }

    /* Новогодний баннер */
    .new-year-banner {
      background: linear-gradient(90deg, var(--holly-red), var(--accent), var(--holly-green));
      padding: 8px;
      text-align: center;
      font-weight: bold;
      color: #071017;
      margin-bottom: 15px;
      border-radius: 8px;
      animation: banner-pulse 3s infinite;
    }
    
    @keyframes banner-pulse {
      0%, 100% { opacity: 0.9; }
      50% { opacity: 1; }
    }

    /* Header */
    .site-header{position:sticky;top:0;background:linear-gradient(180deg, rgba(10, 26, 42, 0.8), rgba(2,6,23,0.5));backdrop-filter:blur(6px);border-bottom:1px solid rgba(255,255,255,0.05);z-index:10}
    .header-inner{display:flex;align-items:center;justify-content:space-between;padding:12px 0}
    .logo{font-weight:700;text-decoration:none;color:var(--accent);font-size:20px;cursor:pointer;display:flex;align-items:center;gap:8px;}
    .main-nav{display:flex;gap:16px}
    .main-nav a{color:var(--muted);text-decoration:none;cursor:pointer;white-space:nowrap;padding:6px 12px;border-radius:8px;transition:all 0.3s}
    .main-nav a:hover{background:rgba(255,255,255,0.05)}
    .main-nav a.active{color:var(--accent);font-weight:600;background:rgba(255,184,107,0.1);border:1px solid rgba(255,184,107,0.2)}

    /* Hero */
    .hero{text-align:center;padding:28px 0;position:relative}
    .hero h1{font-size:40px;margin:6px 0;background:linear-gradient(90deg, var(--holly-red), var(--accent), var(--holly-green));-webkit-background-clip:text;background-clip:text;color:transparent;}
    .subtitle{color:var(--muted);margin-bottom:12px}

    /* Controls */
    .controls{display:flex;gap:10px;justify-content:center;flex-wrap:wrap;margin-bottom:6px}
    .controls input, .controls select{padding:10px 12px;border-radius:10px;border:1px solid rgba(255,255,255,0.08);background:rgba(15, 23, 32, 0.7);color:inherit;min-width:180px}
    .btn{padding:10px 14px;border-radius:10px;border:0;background:linear-gradient(90deg, var(--holly-red), var(--accent));color:#071017;cursor:pointer;font-weight:700;text-decoration:none;display:inline-block;transition:transform 0.2s}
    .btn:hover{transform:translateY(-2px);box-shadow:0 5px 15px rgba(255,71,87,0.3)}

    /* Grid */
    .cards-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:16px;margin-top:18px}
    .card{background:linear-gradient(180deg, rgba(255,255,255,0.03), rgba(0,0,0,0.2));padding:14px;border-radius:12px;display:flex;gap:14px;align-items:flex-start;box-shadow:0 8px 20px rgba(2,6,23,0.6);border:1px solid rgba(255,255,255,0.05);position:relative;transition:transform 0.3s, box-shadow 0.3s}
    .card:hover{transform:translateY(-5px);box-shadow:0 12px 25px rgba(255,71,87,0.1);border-color:rgba(255,184,107,0.3)}
    .card img{width:72px;height:72px;border-radius:50%;object-fit:cover;flex-shrink:0;border:2px solid rgba(255,184,107,0.3)}
    .card-body{flex:1}
    .nick-row{display:flex;align-items:center;gap:8px;justify-content:space-between}
    .nick{margin:0;font-size:18px}
    .badge{padding:6px 8px;border-radius:999px;font-weight:700;font-size:12px;color:#071017}
    .badge.owner{background:linear-gradient(90deg, gold, #ffb86b)}
    .badge.high{background:linear-gradient(90deg, #ff8c00, #ffb86b)}
    .badge.medium{background:linear-gradient(90deg, #1e90ff, #70a1ff)}
    .badge.low{background:linear-gradient(90deg, gray, #a4b0be);color:#fff}
    .badge.banned{background:linear-gradient(90deg, crimson, #ff4757);color:#fff}
    .role{margin:6px 0;color:var(--accent);font-weight:600}
    .desc{margin:0;color:var(--muted);font-size:13px}
    .card a.link-profile{display:inline-block;margin-top:8px;text-decoration:none;color:var(--accent);font-weight:700;cursor:pointer}

    /* Profile page */
    .profile-card{background:var(--card);padding:18px;border-radius:12px;border:1px solid rgba(255,184,107,0.1)}
    .profile-card .bigavatar{width:120px;height:120px;border-radius:50%;object-fit:cover;margin-right:18px;border:3px solid rgba(255,184,107,0.5)}
    .profile-top{display:flex;gap:18px;align-items:center}
    .profile-meta{color:var(--muted);margin-top:6px}

    /* Apply form */
    .apply-form{max-width:700px;margin:0 auto;margin-top:12px;display:grid;gap:10px}
    .apply-form label{display:flex;flex-direction:column;color:var(--muted);font-size:14px}
    .apply-form input, .apply-form select, .apply-form textarea{padding:10px;border-radius:10px;border:1px solid rgba(255,255,255,0.08);background:rgba(15, 23, 32, 0.7);color:inherit}
    .apply-form textarea{min-height:90px;resize:vertical}
    .format-info{background:rgba(255,255,255,0.03);padding:16px;border-radius:12px;margin-bottom:20px;border:1px solid rgba(255,255,255,0.05)}
    .format-info h3{color:var(--accent);margin-top:0}

    /* Footer */
    .site-footer{padding:18px 0;text-align:center;color:var(--muted);border-top:1px solid rgba(255,255,255,0.02);margin-top:36px}

    /* Страницы */
    .page{display:none;}
    .page.active{display:block;}

    /* Mobile */
    @media (max-width:720px){
      .profile-top{flex-direction:column;align-items:flex-start}
      .cards-grid{grid-template-columns:repeat(auto-fill,minmax(200px,1fr))}
      .hero h1{font-size:28px}
      .header-inner{flex-direction:column;gap:12px;text-align:center}
      .main-nav{gap:12px;justify-content:center}
      .controls{flex-direction:column;align-items:center}
      .controls input, .controls select{width:100%;max-width:300px}
      .btn{width:100%;max-width:300px;text-align:center}
    }

    @media (max-width:480px){
      .container{padding:12px}
      .hero{padding:20px 0}
      .hero h1{font-size:24px}
      .cards-grid{grid-template-columns:1fr;gap:12px}
      .card{flex-direction:column;text-align:center;align-items:center}
      .card img{margin-bottom:8px}
      .profile-top{flex-direction:column;text-align:center;align-items:center}
      .profile-card .bigavatar{margin-right:0;margin-bottom:12px}
    }

    .hint {
      color: var(--muted);
      font-style: italic;
      text-align: center;
      padding: 20px;
    }
    
    /* Номер в карточке */
    .number {
      display: inline-block;
      background: rgba(255, 184, 107, 0.1);
      padding: 3px 8px;
      border-radius: 6px;
      font-size: 12px;
      margin-top: 4px;
      color: var(--accent);
      border: 1px solid rgba(255, 184, 107, 0.2);
    }
    
    /* Анимация снега */
    @keyframes fall {
      0% {
        transform: translateY(-10px) rotate(0deg);
        opacity: 0.8;
      }
      100% {
        transform: translateY(100vh) rotate(360deg);
        opacity: 0;
      }
    }
    
    /* Праздничные украшения для карточек */
    .card::before {
      content: '🎄';
      position: absolute;
      top: -10px;
      right: -10px;
      font-size: 20px;
      opacity: 0.6;
      z-index: 1;
    }
  </style>
</head>
<body>
  <!-- Гирлянды -->
  <div class="garland" id="garlandTop"></div>
  
  <header class="site-header">
    <div class="container header-inner">
      <a class="logo" id="homeLink">🎄 Fame List</a>
      <nav class="main-nav">
        <a id="mainLink" class="active">Главная</a>
        <a id="profileLink">Профиль</a>
        <a id="applyLink">Подать заявку</a>
      </nav>
    </div>
  </header>

    
    <!-- Главная страница -->
    <div id="mainPage" class="page active">
      <section class="hero">
        <h1>🎅 Fame List</h1>

        <div class="controls">
          <input id="search" placeholder="Поиск по нику, номеру или описанию..." aria-label="Поиск" />
          <select id="filterMedia" aria-label="Фильтр по медийке">
            <option value="all">Все медийки</option>
            <option value="owner">Разработчик</option>
            <option value="Высокая медийка">Высокая медийка</option>
            <option value="Средняя медийка">Средняя медийка</option>
            <option value="Малая медийка">Малая медийка</option>
            <option value="Бомж/скамер">Бомж/скамер</option>
          </select>

          <select id="filterRank" aria-label="Фильтр по рангу">
            <option value="all">Все ранги</option>
            <option value="owner">разработчик</option>
            <option value="high">Высокая</option>
            <option value="medium">Средняя</option>
            <option value="low">Малая</option>
            <option value="banned">Бомж/скамер</option>
          </select>

          <button id="resetBtn" class="btn"> Сброс</button>
        </div>
      </section>

      <section>
        <div id="cards" class="cards-grid" aria-live="polite"></div>
      </section>
    </div>

    <!-- Страница профиля -->
    <div id="profilePage" class="page">
      <div id="profileCard" class="profile-card" aria-live="polite">
        <p class="hint">Зайдите на профиль через ссылку "Смотреть профиль" на главной или добавьте параметр ?user=Nick</p>
      </div>
    </div>

    <!-- Страница заявки -->
    <div id="applyPage" class="page">
      <section class="hero">
        <h1>🎁 Подать заявку</h1>
        <p class="subtitle">Заполните форму для добавления в Fame List</p>
      </section>

      <div class="format-info">
        <h3>🎄 Формат заявки</h3>
        <p>Для подачи заявки нажмите кнопку ниже - она откроет Telegram-бота, где нужно будет отправить информацию в следующем формате:</p>
        <p><strong>Ник:</strong> Ваш никнейм в телеграмм</p>
        <p><strong>Ссылка на профиль телеграмм:</strong> https://t.me/username</p>
        <p><strong>Медийность:</strong> Высокая/Средняя/Малая</p>
        <p><strong>Как пришёл в KM:</strong> Описание как вы появились в KM</p>
      </div>

      <div style="text-align: center; margin-top: 30px;">
        <a href="https://t.me/PsulistHelp_Bot" class="btn" target="_blank" style="padding: 12px 24px; font-size: 16px;">
          🎅 Подать заявку в бота
        </a>
      </div>
    </div>

  <footer class="site-footer">
    <div class="container">
      <p>© <span id="year"></span> Fame List — @psulist</p>
    </div>
  </footer>

  <script>
    // ======= Demo-данные с номерами =======
    const people = [
      {
        nick: 'Прокурор Алекс',
        rank: 'owner',
        rankName: 'Разработчик',
        media: 'Высокая медийка',
        since: '2024',
        number: '0000',
        profile: 'https://t.me/AlOsint',
        img: 'https://github.com/glitterinzem-star/list/raw/2751079d5f1d012bb6d06226949884906edd11fa/alex.jpg.jpeg',
        desc: 'разработчик сайта'
      },
      {
        nick: 'Ареон',
        rank: 'owner',
        rankName: 'Разработчик',
        media: 'Высокая медийка',
        since: '2021',
        number: '1611',
        profile: 'https://t.me/areonEditor',
        img: 'https://github.com/glitterinzem-star/list/raw/1f126336feb4880f4c731615fc6dba2a4b96db2b/psixo.jpg.jpg',
        desc: 'разработчик сайта'
      },
      {
        nick: 'Koshmarov',
        rank: 'high',
        rankName: 'Высокая',
        media: 'Высокая медийка',
        since: '2022',
        number: '1111',
        profile: 'Https://t.me/koshmarovbog',
        img: 'https://github.com/glitterinzem-star/list/raw/21f4f07d00cb39e3a613b2ee242e7114ac35a78d/kosh.jpg.jpg',
        desc: 'личность которую практически везде узнают (номер был словлен на аукционе)'
      },
      {
        nick: 'Вейзов',
        rank: 'medium',
        rankName: 'Средняя',
        media: 'Средняя мидийка',
        since: '2022',
        profile: 'https://t.me/weizovv',
        img: 'https://github.com/glitterinzem-star/list/raw/c012d6e23ddd60a106ce75fa9a45abf57627536b/weizovv.jpg.jpg',
        desc: 'личность которую почти везде узнают'
      },
      {
        nick: 'Мира Маньяк',
        rank: 'medium',
        rankName: 'Средняя',
        media: 'Средняя медийка',
        since: '2024',
        profile: 'https://t.me/miramaniac',
        img: 'https://github.com/glitterinzem-star/list/raw/baaa63ce37fc6531ac94eccf5337caf113c15a47/mira.jpg.jpg',
        desc: 'средне узнаваемая личность'
      },
      {
        nick: 'Vk Lega',
        rank: 'medium',
        rankName: 'Средняя',
        media: 'Средняя медийка',
        since: '2023',
        number: '6666',
        profile: 'https://t.me/clonlega',
        img: 'https://github.com/glitterinzem-star/list/raw/691d3cb50a06a4e76eebb88488f0bb0bd105f8d8/legf.jpg.jpg',
        desc: 'часто узнаваемая личность ( номер был словлен на аукционе)'
      },
      {
        nick: 'Фартинов',
        rank: 'high',
        rankName: 'Высокая',
        media: 'Высокая медийка',
        since: '2018',
        profile: 'https://t.me/nernuq',
        img: 'https://github.com/glitterinzem-star/list/raw/691d3cb50a06a4e76eebb88488f0bb0bd105f8d8/fart.jpg.jpg',
        desc: 'часто узнаваемая личность'
      },
      {
        nick: 'Георгий',
        rank: 'high',
        rankName: 'Высокая',
        media: 'Высокая медийка',
        since: '2023',
        number: '9999',
        profile: 'https://t.me/userneum',
        img: 'https://github.com/glitterinzem-star/list/raw/691d3cb50a06a4e76eebb88488f0bb0bd105f8d8/georg.jpg.jpg',
        desc: 'часто узнаваемая личность'
      },
      {
        nick: 'ScammerGuy',
        rank: 'banned',
        rankName: 'Бомж/скамер',
        media: 'Бомж/скамер',
        since: '2025',
        profile: 'https://t.me/ScammerGuy',
        img: 'assets/avatars/avatar2.png',
        desc: 'Бан за мошенничество.'
      }
    ];

    // порядок старшинства — меньше = старше
    const rankOrder = { owner: 1, high: 2, medium: 3, low: 4, banned: 5 };

    // ======= Новогодние эффекты =======
    function createSnowflake() {
      const snowflake = document.createElement('div');
      snowflake.classList.add('snowflake');
      snowflake.innerHTML = '❄';
      
      // Случайная позиция и размер
      const size = Math.random() * 20 + 10;
      const startX = Math.random() * window.innerWidth;
      const duration = Math.random() * 10 + 10;
      const delay = Math.random() * 5;
      
      snowflake.style.left = `${startX}px`;
      snowflake.style.fontSize = `${size}px`;
      snowflake.style.animation = `fall ${duration}s linear ${delay}s infinite`;
      snowflake.style.opacity = Math.random() * 0.7 + 0.3;
      
      document.body.appendChild(snowflake);
      
      // Удаление снежинки после завершения анимации
      setTimeout(() => {
        if (snowflake.parentNode) {
          snowflake.parentNode.removeChild(snowflake);
        }
      }, (duration + delay) * 1000);
    }
    
    function createGarland() {
      const garland = document.getElementById('garlandTop');
      if (!garland) return;
      
      garland.innerHTML = '';
      const lightCount = Math.floor(window.innerWidth / 20);
      
      for (let i = 0; i < lightCount; i++) {
        const light = document.createElement('div');
        light.classList.add('light');
        
        // Позиционирование
        const leftPos = (i / lightCount) * 100;
        light.style.left = `${leftPos}%`;
        
        // Цвета гирлянды
        const colors = ['#ff4757', '#2ecc71', '#ffb86b', '#3498db', '#9b59b6'];
        const color = colors[i % colors.length];
        light.style.backgroundColor = color;
        light.style.boxShadow = `0 0 10px ${color}`;
        
        // Анимация мигания
        const delay = Math.random() * 1.5;
        light.style.animationDelay = `${delay}s`;
        
        garland.appendChild(light);
      }
    }
    
    function createHolly() {
      const holly = document.createElement('div');
      holly.classList.add('holly');
      
      // Случайная позиция
      const left = Math.random() * window.innerWidth;
      const top = Math.random() * window.innerHeight;
      
      holly.style.left = `${left}px`;
      holly.style.top = `${top}px`;
      
      // Случайный размер
      const size = Math.random() * 30 + 20;
      holly.style.width = `${size}px`;
      holly.style.height = `${size}px`;
      
      document.body.appendChild(holly);
      
      // Удаление через некоторое время
      setTimeout(() => {
        if (holly.parentNode) {
          holly.parentNode.removeChild(holly);
        }
      }, 15000);
    }
    
    // Запуск новогодних эффектов
    function startNewYearEffects() {
      // Создаем гирлянду
      createGarland();
      
      // Снежинки каждые 3-5 секунд
      setInterval(createSnowflake, Math.random() * 2000 + 3000);
      
      // Гирлянда пересоздается при изменении размера окна
      window.addEventListener('resize', createGarland);
      
      // Падуб (новогоднее украшение) каждые 5-8 секунд
      setInterval(createHolly, Math.random() * 3000 + 5000);
      
      // Сразу создаем несколько снежинок
      for (let i = 0; i < 15; i++) {
        setTimeout(() => createSnowflake(), i * 300);
      }
    }

    // ======= Общие функции =======
    function sortPeople(arr) {
      return arr.slice().sort((a,b)=> {
        // Сначала проверяем номер 0000 - он должен быть всегда первым
        const aIsZero = a.number === '0000';
        const bIsZero = b.number === '0000';
        
        // Если один из них имеет номер 0000, он должен быть выше
        if (aIsZero && !bIsZero) return -1;
        if (!aIsZero && bIsZero) return 1;
        if (aIsZero && bIsZero) return 0;
        
        // Если оба owner, сортируем по номеру (меньший номер выше)
        if (a.rank === 'owner' && b.rank === 'owner') {
          // Преобразуем номера в числа для сравнения
          const numA = parseInt(a.number || '9999') || 9999;
          const numB = parseInt(b.number || '9999') || 9999;
          return numA - numB; // Чем меньше номер, тем выше
        }
        
        // Если только один owner - он всегда выше
        if (a.rank === 'owner' && b.rank !== 'owner') return -1;
        if (b.rank === 'owner' && a.rank !== 'owner') return 1;
        
        // Для всех остальных - обычная сортировка по рангу
        const r = (rankOrder[a.rank] || 99) - (rankOrder[b.rank] || 99);
        if (r !== 0) return r;
        
        // Вторичный порядок — по году появления (раньше выше)
        return (a.since || '9999').localeCompare(b.since || '9999');
      });
    }
  
    // создать DOM-карту-карточку
    function createCard(person) {
      const art = document.createElement('article');
      art.className = 'card';
      art.dataset.rank = person.rank;
      art.dataset.media = person.media || '';
      art.dataset.number = person.number || '';
      art.innerHTML = `
        <img src="${person.img}" alt="${person.nick} avatar" onerror="this.src='assets/avatars/avatar1.png'">
        <div class="card-body">
          <div class="nick-row">
            <h3 class="nick">${person.nick}</h3>
            <span class="badge ${person.rank}">${person.rankName || person.rank}</span>
          </div>
          <p class="role">Медийка: <b>${person.media || person.rankName || '-'}</b></p>
          <p class="desc">${person.desc || ''}</p>
          <div class="profile-meta">
            <p>Номер: <span class="number">${person.number || 'не указан'}</span></p>
            <p>В КМ с: <b>${person.since || '-'}</b></p>
          </div>
          <a class="link-profile view-profile" data-user="${person.nick}">🎄 Смотреть профиль</a>
          &nbsp;·&nbsp;
          <a class="link-profile" href="${person.profile}" target="_blank" rel="noopener noreferrer">🎁 Профиль (внешний)</a>
        </div>
      `;
      return art;
    }

    // рендер главной сетки
    function renderMainGrid(containerId = 'cards', source = people) {
      const cont = document.getElementById(containerId);
      if (!cont) return;
      cont.innerHTML = '';
      const sorted = sortPeople(source);
      sorted.forEach(p => cont.appendChild(createCard(p)));
      
      // Добавляем обработчики для ссылок "Смотреть профиль"
      document.querySelectorAll('.view-profile').forEach(link => {
        link.addEventListener('click', function() {
          const user = this.getAttribute('data-user');
          showProfilePage(user);
        });
      });
    }

    // ======= Поиск и фильтры на главной =======
    function initFilters() {
      const search = document.getElementById('search');
      const filterMedia = document.getElementById('filterMedia');
      const filterRank = document.getElementById('filterRank');
      const resetBtn = document.getElementById('resetBtn');

      function apply() {
        const q = search ? search.value.trim().toLowerCase() : '';
        const fMedia = filterMedia ? filterMedia.value : 'all';
        const fRank = filterRank ? filterRank.value : 'all';

        const nodes = document.querySelectorAll('#cards .card');
        nodes.forEach(node => {
          const nick = node.querySelector('.nick').textContent.toLowerCase();
          const desc = node.querySelector('.desc').textContent.toLowerCase();
          const number = node.querySelector('.number') ? node.querySelector('.number').textContent.toLowerCase() : '';
          const media = node.dataset.media || '';
          const rank = node.dataset.rank || '';

          const matchesQ = q === '' || 
                          nick.includes(q) || 
                          desc.includes(q) || 
                          number.includes(q);
          const matchesMedia = (fMedia === 'all') || media === fMedia;
          const matchesRank = (fRank === 'all') || rank === fRank;

          node.style.display = (matchesQ && matchesMedia && matchesRank) ? '' : 'none';
        });
      }

      if (search) search.addEventListener('input', apply);
      if (filterMedia) filterMedia.addEventListener('change', apply);
      if (filterRank) filterRank.addEventListener('change', apply);
      if (resetBtn) resetBtn.addEventListener('click', () => {
        if (search) search.value = '';
        if (filterMedia) filterMedia.value = 'all';
        if (filterRank) filterRank.value = 'all';
        renderMainGrid('cards');
      });
    }

    // ======= Профиль =======
    function showProfilePage(userNick = null) {
      // Переключаемся на страницу профиля
      switchPage('profilePage');
      
      const profileContainer = document.getElementById('profileCard');
      if (!profileContainer) return;
      
      let nick = userNick;
      
      // Если ник не передан, проверяем URL параметры
      if (!nick) {
        const params = new URLSearchParams(window.location.search);
        nick = params.get('user');
      }
      
      if (!nick) {
        profileContainer.innerHTML = `<p class="hint">🎄 Параметр user не указан. Откройте профиль через ссылку 'Смотреть профиль' на главной.</p>`;
        return;
      }
      
      const person = people.find(p => p.nick.toLowerCase() === nick.toLowerCase());
      if (!person) {
        profileContainer.innerHTML = `<p class="hint">🎅 Пользователь <strong>${escapeHtml(nick)}</strong> не найден.</p>`;
        return;
      }

      profileContainer.innerHTML = `
        <div class="profile-card">
          <div class="profile-top">
            <img class="bigavatar" src="${person.img}" alt="${person.nick}" onerror="this.src='assets/avatars/avatar1.png'">
            <div>
              <h2>${person.nick} <span class="badge ${person.rank}">${person.rankName || person.rank}</span></h2>
              <div class="profile-meta">
                <p>Медийка: <b>${person.media || '-'}</b></p>
                <p>Номер: <span class="number">${person.number || 'не указан'}</span></p>
                <p>В КМ с: <b>${person.since || '-'}</b></p>
                <p>Ссылка: <a href="${person.profile}" target="_blank" rel="noopener noreferrer">${person.profile}</a></p>
              </div>
            </div>
          </div>
          <hr style="margin:12px 0;border:0;border-top:1px solid rgba(255,255,255,0.03)">
          <p>${person.desc || '-'}</p>
        </div>
      `;
    }

    // ======= Навигация между страницами =======
    function switchPage(pageId) {
      // Скрываем все страницы
      document.querySelectorAll('.page').forEach(page => {
        page.classList.remove('active');
      });
      
      // Показываем нужную страницу
      document.getElementById(pageId).classList.add('active');
      
      // Обновляем активную ссылку в навигации
      document.querySelectorAll('.main-nav a').forEach(link => {
        link.classList.remove('active');
      });
      
      if (pageId === 'mainPage') {
        document.getElementById('mainLink').classList.add('active');
      } else if (pageId === 'profilePage') {
        document.getElementById('profileLink').classList.add('active');
      } else if (pageId === 'applyPage') {
        document.getElementById('applyLink').classList.add('active');
      }
    }

    // ======= Утилиты =======
    function escapeHtml(str){
      if (!str) return '';
      return String(str).replace(/[&<>"']/g, function(m){
        return ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[m]);
      });
    }

    // ======= Инициализация при загрузке =======
    document.addEventListener('DOMContentLoaded', () => {
      // футер года
      const y = new Date().getFullYear();
      document.getElementById('year').textContent = y;

      // Запуск новогодних эффектов
      startNewYearEffects();

      // Инициализация главной страницы
      if (document.getElementById('cards')) {
        renderMainGrid('cards');
        initFilters();
      }
      // Навигация
      document.getElementById('homeLink').addEventListener('click', () => switchPage('mainPage'));
      document.getElementById('mainLink').addEventListener('click', () => switchPage('mainPage'));
      document.getElementById('profileLink').addEventListener('click', () => showProfilePage());
      document.getElementById('applyLink').addEventListener('click', () => switchPage('applyPage'));

      // Проверяем URL при загрузке для открытия профиля
      const urlParams = new URLSearchParams(window.location.search);
      if (urlParams.has('user')) {
        showProfilePage(urlParams.get('user'));
      }
    });
  </script>
</body>
</html>
