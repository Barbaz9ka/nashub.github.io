# nashub.github.io

<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Гайд: как работать с тревогой</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,340;9..144,480;9..144,600&family=Work+Sans:wght@400;500;600;700&family=Caveat:wght@500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --cream:#F7F1E7;
    --sand:#EFE2CE;
    --sand-2:#E8D9C2;
    --blush:#E7BCAE;
    --terracotta:#BE6B48;
    --clay-deep:#8C4630;
    --umber:#40332A;
    --taupe:#8B7A6A;
    --line:#DED0B9;
    --paper:#FBF7F0;
    --ok-green:#7C9070;
  }
  *{box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    margin:0;
    background:var(--cream);
    color:var(--umber);
    font-family:'Work Sans', sans-serif;
    -webkit-font-smoothing:antialiased;
  }
  h1,h2,h3{
    font-family:'Fraunces', serif;
    font-weight:480;
    margin:0;
    letter-spacing:-0.01em;
  }
  .hand{
    font-family:'Caveat', cursive;
    font-weight:600;
  }
  .slide{
    min-height:100vh;
    width:100%;
    padding:96px 8vw 64px;
    display:flex;
    align-items:center;
    justify-content:center;
    position:relative;
    scroll-margin-top:0;
    border-bottom:1px solid var(--line);
  }
  .slide:last-of-type{border-bottom:none;}
  .wrap{
    max-width:1080px;
    width:100%;
    display:grid;
    grid-template-columns:1.35fr 1fr;
    gap:56px;
    align-items:center;
  }
  .wrap.narrow{grid-template-columns:1fr;}
  .label{
    font-size:13px;
    color:var(--terracotta);
    font-weight:600;
    margin-bottom:14px;
    display:flex;
    align-items:center;
    gap:8px;
  }
  .label .dot{width:6px;height:6px;border-radius:50%;background:var(--terracotta);}
  .title{
    font-size:44px;
    line-height:1.08;
    color:var(--umber);
    margin-bottom:18px;
  }
  .thesis{
    font-size:19px;
    line-height:1.55;
    color:var(--umber);
    max-width:52ch;
    margin-bottom:14px;
  }
  .text{
    font-size:16px;
    line-height:1.65;
    color:#5B4E42;
    max-width:56ch;
  }
  .text p{margin:0 0 12px;}
  .visual-col{
    position:relative;
    display:flex;
    align-items:center;
    justify-content:center;
  }
  .blob{
    position:relative;
    width:340px;
    height:340px;
    border-radius:44% 56% 62% 38% / 48% 42% 58% 52%;
    background:linear-gradient(150deg, var(--blush) 0%, var(--sand-2) 100%);
    display:flex;
    align-items:center;
    justify-content:center;
    box-shadow:0 30px 60px -30px rgba(140,70,48,0.35);
  }
  .blob .num{
    font-family:'Fraunces', serif;
    font-size:120px;
    color:rgba(140,70,48,0.28);
    font-weight:480;
  }
  .card{
    background:var(--paper);
    border:1px solid var(--line);
    border-radius:20px;
    padding:26px 28px;
    box-shadow:0 20px 40px -28px rgba(64,51,42,0.25);
  }
  .worksheet{margin-top:22px;}
  .field{margin-bottom:16px;}
  .field label{
    display:block;
    font-size:13.5px;
    font-weight:600;
    color:var(--clay-deep);
    margin-bottom:6px;
  }
  .field .hint{
    font-size:12.5px;
    color:var(--taupe);
    font-weight:400;
    margin-left:6px;
  }
  input[type="text"], textarea{
    width:100%;
    border:none;
    border-bottom:2px solid var(--line);
    background:transparent;
    font-family:'Work Sans', sans-serif;
    font-size:15.5px;
    color:var(--umber);
    padding:6px 2px;
    resize:none;
    transition:border-color .2s ease;
  }
  input[type="text"]:focus, textarea:focus{
    outline:none;
    border-bottom-color:var(--terracotta);
  }
  textarea{min-height:38px;}
  .row2{display:grid;grid-template-columns:1fr 1fr;gap:18px;}
  .row3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:14px;}
  .pct-row{display:flex;align-items:center;gap:14px;}
  input[type="range"]{
    -webkit-appearance:none;
    flex:1;
    height:4px;
    border-radius:4px;
    background:linear-gradient(90deg, var(--terracotta) 0%, var(--terracotta) var(--val,50%), var(--line) var(--val,50%), var(--line) 100%);
  }
  input[type="range"]::-webkit-slider-thumb{
    -webkit-appearance:none;
    width:18px;height:18px;border-radius:50%;
    background:var(--paper);
    border:3px solid var(--terracotta);
    cursor:pointer;
  }
  .pct-val{
    font-family:'Fraunces', serif;
    font-size:20px;
    color:var(--clay-deep);
    min-width:48px;
    text-align:right;
  }
  .checks{display:flex;flex-direction:column;gap:10px;margin-top:6px;}
  .check{display:flex;align-items:center;gap:10px;font-size:15px;cursor:pointer;}
  .check input{
    appearance:none;-webkit-appearance:none;
    width:20px;height:20px;
    border:2px solid var(--terracotta);
    border-radius:6px;
    position:relative;
    cursor:pointer;
    flex:none;
  }
  .check input:checked{background:var(--terracotta);}
  .check input:checked::after{
    content:'';
    position:absolute;left:5px;top:1px;
    width:5px;height:10px;
    border:solid var(--paper);
    border-width:0 2px 2px 0;
    transform:rotate(45deg);
  }
  .footline{
    margin-top:20px;
    font-family:'Fraunces', serif;
    font-style:normal;
    font-size:18px;
    color:var(--clay-deep);
    border-left:3px solid var(--terracotta);
    padding-left:14px;
    line-height:1.4;
  }
  .chain{
    display:flex;
    flex-wrap:wrap;
    align-items:center;
    gap:10px;
    margin:22px 0 6px;
  }
  .chain .chip{
    background:var(--sand);
    border-radius:999px;
    padding:8px 16px;
    font-size:14px;
    font-weight:600;
    color:var(--clay-deep);
  }
  .chain .arrow{color:var(--terracotta); font-size:16px;}
  .example{
    margin-top:10px;
    background:var(--sand);
    border-radius:14px;
    padding:16px 18px;
    font-size:14.5px;
    color:#5B4E42;
    line-height:1.7;
  }
  .example .step{display:block;}
  .example .arrow-d{color:var(--terracotta); margin:2px 0;}
  .mini-grid{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:16px;
    margin-top:22px;
  }
  .mini-card{
    background:var(--paper);
    border:1px solid var(--line);
    border-radius:16px;
    padding:18px;
  }
  .mini-card h3{font-size:16px; color:var(--clay-deep); margin-bottom:8px;}
  .mini-card .ex{font-size:13.5px; color:#5B4E42; margin-bottom:10px; line-height:1.5;}
  .mini-card .q{font-size:13px; color:var(--terracotta); font-weight:600;}
  .scale{
    margin-top:24px;
    position:relative;
  }
  .scale-track{
    height:10px;
    border-radius:10px;
    background:linear-gradient(90deg, var(--ok-green) 0%, var(--sand-2) 45%, var(--terracotta) 100%);
  }
  .scale-labels{display:flex; justify-content:space-between; margin-top:8px; font-size:12.5px; color:var(--taupe);}
  .scale-labels span:last-child{color:var(--terracotta); font-weight:600;}
  .scale-labels span:first-child{color:var(--ok-green); font-weight:600;}
  .breathe-wrap{display:flex; flex-direction:column; align-items:center; gap:18px;}
  .breathe-circle{
    width:180px;height:180px;border-radius:50%;
    background:radial-gradient(circle at 35% 30%, var(--blush), var(--terracotta));
    animation:breathe 8s ease-in-out infinite;
    box-shadow:0 20px 50px -20px rgba(140,70,48,0.45);
  }
  @keyframes breathe{
    0%{transform:scale(0.72);}
    45%{transform:scale(1);}
    50%{transform:scale(1);}
    95%{transform:scale(0.72);}
    100%{transform:scale(0.72);}
  }
  .breathe-caption{font-size:13.5px; color:var(--taupe); text-align:center;}
  .fivefour{display:flex; flex-direction:column; gap:10px; margin-top:18px;}
  .ff-row{display:flex; align-items:center; gap:12px;}
  .ff-num{
    font-family:'Fraunces', serif;
    font-size:22px;
    color:var(--terracotta);
    width:26px;
  }
  .ff-row input{flex:1;}
  table.map{
    width:100%;
    border-collapse:collapse;
    margin-top:20px;
    font-size:14.5px;
  }
  table.map td{
    padding:14px 10px;
    border-bottom:1px solid var(--line);
    vertical-align:top;
  }
  table.map td:first-child{color:#5B4E42; width:52%;}
  table.map td:last-child{color:var(--clay-deep); font-weight:600;}
  table.map tr:last-child td{border-bottom:none;}
  .split-note{
    margin-top:20px;
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:16px;
  }
  .split-note .box{
    background:var(--sand);
    border-radius:14px;
    padding:16px;
    font-size:13.5px;
    color:#5B4E42;
    line-height:1.55;
  }
  .split-note .box b{color:var(--clay-deep); display:block; margin-bottom:6px; font-size:14px;}
  .care-note{
    margin-top:26px;
    font-size:13px;
    color:var(--taupe);
    border-top:1px solid var(--line);
    padding-top:14px;
    line-height:1.5;
  }
  /* nav dots */
  .dotnav{
    position:fixed;
    right:26px;
    top:50%;
    transform:translateY(-50%);
    display:flex;
    flex-direction:column;
    gap:12px;
    z-index:50;
  }
  .dotnav a{
    width:9px;height:9px;
    border-radius:50%;
    background:var(--line);
    display:block;
    transition:background .2s, transform .2s;
  }
  .dotnav a.active{background:var(--terracotta); transform:scale(1.3);}
  .topbar{
    position:fixed; top:0; left:0; right:0;
    padding:16px 8vw;
    display:flex; align-items:center; justify-content:space-between;
    z-index:50;
    background:linear-gradient(var(--cream) 60%, transparent);
  }
  .brand{
    font-family:'Fraunces', serif;
    font-size:15px;
    color:var(--clay-deep);
    letter-spacing:0.02em;
  }
  .progress-text{font-size:12.5px; color:var(--taupe);}
  .cover .wrap{grid-template-columns:1fr;}
  .cover{
    background:radial-gradient(circle at 75% 20%, var(--blush) 0%, transparent 45%), var(--cream);
  }
  .cover-inner{text-align:left; max-width:640px;}
  .cover .kicker{font-size:14px; color:var(--terracotta); font-weight:600; margin-bottom:20px;}
  .cover h1{font-size:58px; line-height:1.05; margin-bottom:20px;}
  .cover .sub{font-size:18px; color:#5B4E42; line-height:1.6; max-width:46ch; margin-bottom:28px;}
  .cover .startline{font-family:'Caveat', cursive; font-size:24px; color:var(--clay-deep);}
  .scroll-hint{
    margin-top:40px; font-size:13px; color:var(--taupe);
    display:flex; align-items:center; gap:8px;
  }
  .scroll-hint .arrow-down{
    display:inline-block; animation:bob 1.6s ease-in-out infinite;
  }
  @keyframes bob{0%,100%{transform:translateY(0);}50%{transform:translateY(6px);}}
  @media (max-width:820px){
    .wrap{grid-template-columns:1fr;}
    .visual-col{order:-1; margin-bottom:12px;}
    .blob{width:190px;height:190px;}
    .blob .num{font-size:64px;}
    .title{font-size:32px;}
    .cover h1{font-size:38px;}
    .mini-grid{grid-template-columns:1fr;}
    .row2, .row3{grid-template-columns:1fr;}
    .split-note{grid-template-columns:1fr;}
    .dotnav{display:none;}
    .slide{padding:80px 6vw 48px;}
  }
</style>
</head>
<body>

<div class="topbar">
  <div class="brand">спокойный ум · антитревожный гайд</div>
  <div class="progress-text" id="progressText">01 / 09</div>
</div>

<nav class="dotnav" id="dotnav"></nav>

<!-- COVER -->
<section class="slide cover" id="s0">
  <div class="wrap">
    <div class="cover-inner">
      <div class="kicker">рабочая тетрадь · 9 шагов</div>
      <h1>Что делать,<br>когда тревожно</h1>
      <p class="sub">Не теория, а инструменты. Открой заметки или возьми лист бумаги — и заполняй по ходу чтения.</p>
      <p class="startline">Начнём с того, что такое тревога на самом деле →</p>
      <div class="scroll-hint"><span class="arrow-down">↓</span> листай вниз</div>
    </div>
  </div>
</section>

<!-- SLIDE 1 -->
<section class="slide" id="s1">
  <div class="wrap">
    <div>
      <div class="label"><span class="dot"></span>01 · НАЧАЛО</div>
      <h2 class="title">Тревога — это не поломка</h2>
      <p class="thesis">Тревога — это система раннего предупреждения тела. Она пытается заметить возможную опасность заранее, ещё до того, как та случится.</p>
      <div class="text">
        <p>Сама по себе тревога — нормальна. Она помогает подготовиться, быть внимательнее, заранее продумать действия и вовремя заметить риск.</p>
        <p>Проблема начинается не тогда, когда тревога появляется, а когда она перестаёт помогать и начинает мешать: заставляет избегать, без конца перепроверять, прокручивать одни и те же сценарии, искать гарантий там, где их не бывает.</p>
      </div>
      <div class="scale">
        <div class="scale-track"></div>
        <div class="scale-labels"><span>помогает действовать</span><span>мешает жить</span></div>
      </div>
      <div class="footline">Цель не в том, чтобы никогда не тревожиться.<br>Цель — научиться управлять тревогой, когда она начинает управлять тобой.</div>
    </div>
    <div class="visual-col"><div class="blob"><span class="num">01</span></div></div>
  </div>
</section>

<!-- SLIDE 2 -->
<section class="slide" id="s2">
  <div class="wrap">
    <div>
      <div class="label"><span class="dot"></span>02 · МЕХАНИЗМ</div>
      <h2 class="title">Как одна мысль раскручивает тревогу</h2>
      <div class="chain">
        <span class="chip">Ситуация</span><span class="arrow">→</span>
        <span class="chip">Мысль</span><span class="arrow">→</span>
        <span class="chip">Эмоция</span><span class="arrow">→</span>
        <span class="chip">Тело</span><span class="arrow">→</span>
        <span class="chip">Поведение</span>
      </div>
      <div class="example">
        <span class="step">Человек не ответил на сообщение</span>
        <span class="arrow-d">↓</span>
        <span class="step">«Наверное, он на меня злится»</span>
        <span class="arrow-d">↓</span>
        <span class="step">тревога → сердцебиение, напряжение</span>
        <span class="arrow-d">↓</span>
        <span class="step">желание написать ещё 5 сообщений, проверить телефон</span>
      </div>
      <div class="text" style="margin-top:18px;">
        <p>Часто нас тревожит не сама ситуация, а то, как мозг её интерпретирует. Тревожная мысль не обязательно неправильная — задача не заменить её на позитивную, а заменить <b>автоматическую</b> мысль на <b>более реалистичную</b>.</p>
        <p>Такие привычные ошибки мышления называют когнитивными искажениями — это не диагноз, просто способ, которым мозг иногда смотрит на ситуацию тревожнее, чем она есть на самом деле.</p>
      </div>
      <div class="field" style="margin-top:20px; max-width:420px;">
        <label>Вспомни последний момент, когда тревожился(-лась). Какая мысль пришла первой? <span class="hint">коротко, одной фразой</span></label>
        <input type="text" placeholder="Например: «я точно всё испортил(а)»">
      </div>
    </div>
    <div class="visual-col"><div class="blob"><span class="num">02</span></div></div>
  </div>
</section>

<!-- SLIDE 3: DECATASTROPHIZATION -->
<section class="slide" id="s3">
  <div class="wrap narrow">
    <div>
      <div class="label"><span class="dot"></span>03 · ГЛАВНЫЙ ИНСТРУМЕНТ</div>
      <h2 class="title">Декатастрофизация</h2>
      <p class="thesis">Тревога часто рисует самый страшный сценарий так, будто он уже почти произошёл. Задача — не убедить себя, что «всё точно будет хорошо», а посмотреть на ситуацию трезво и вернуть ей масштаб.</p>

      <div class="card worksheet">
        <div class="field">
          <label>1. Чего я сейчас боюсь?</label>
          <textarea rows="1" placeholder="Опиши ситуацию в одном предложении"></textarea>
        </div>
        <div class="row2">
          <div class="field">
            <label>2. Самый страшный вариант</label>
            <textarea rows="1" placeholder="Что самое худшее может произойти?"></textarea>
          </div>
          <div class="field">
            <label>Насколько это вероятно?</label>
            <div class="pct-row">
              <input type="range" min="0" max="100" value="50" oninput="this.style.setProperty('--val', this.value+'%'); this.nextElementSibling.textContent=this.value+'%'">
              <span class="pct-val">50%</span>
            </div>
          </div>
        </div>
        <div class="row2">
          <div class="field">
            <label>3. Факты «за» <span class="hint">коротко</span></label>
            <textarea rows="1" placeholder="Что говорит, что это может случиться"></textarea>
          </div>
          <div class="field">
            <label>Факты «против»</label>
            <textarea rows="1" placeholder="Что говорит, что вряд ли"></textarea>
          </div>
        </div>
        <div class="field">
          <label>4. Наиболее реалистичный сценарий</label>
          <textarea rows="1" placeholder="Что на самом деле вероятнее всего произойдёт?"></textarea>
        </div>
        <div class="row2">
          <div class="field">
            <label>5. Если худшее всё же случится — мой первый шаг</label>
            <textarea rows="1" placeholder="Что я сделаю в этом случае?"></textarea>
          </div>
          <div class="field">
            <label>6. Что я могу сделать прямо сейчас</label>
            <textarea rows="1" placeholder="Один конкретный шаг"></textarea>
          </div>
        </div>
      </div>
      <div class="footline">Тревожный мозг часто воспринимает «возможность» как «вероятность», а вероятность — почти как факт. Это упражнение возвращает ситуации реальный масштаб.</div>
    </div>
  </div>
</section>

<!-- SLIDE 4: mind reading -->
<section class="slide" id="s4">
  <div class="wrap">
    <div>
      <div class="label"><span class="dot"></span>04 · ИСКАЖЕНИЕ</div>
      <h2 class="title">«Он точно думает обо мне плохо»</h2>
      <p class="thesis">Это искажение называют «чтение мыслей» — когда мы уверены, что знаем, о чём думает другой человек, хотя на самом деле только предполагаем.</p>
      <div class="example"><span class="step">«Он посмотрел на меня странно» → «он точно плохо обо мне думает»</span></div>
      <p style="margin-top:16px; font-family:'Fraunces',serif; font-size:17px; color:var(--clay-deep);">Факт ≠ моя интерпретация</p>

      <div class="card worksheet">
        <div class="field">
          <label>Факт — что я действительно знаю?</label>
          <textarea rows="1" placeholder="Только то, что можно увидеть или услышать"></textarea>
        </div>
        <div class="field">
          <label>Моя мысль — что я предполагаю?</label>
          <textarea rows="1" placeholder="Моя интерпретация факта"></textarea>
        </div>
        <div class="field">
          <label>Что ещё это может означать? <span class="hint">хотя бы 2 варианта</span></label>
          <div class="row2">
            <input type="text" placeholder="Вариант 1">
            <input type="text" placeholder="Вариант 2">
          </div>
        </div>
        <div class="field">
          <label>Более нейтральная мысль, которую я могу выбрать</label>
          <textarea rows="1" placeholder="Спокойнее и ближе к фактам"></textarea>
        </div>
      </div>
    </div>
    <div class="visual-col"><div class="blob"><span class="num">04</span></div></div>
  </div>
</section>

<!-- SLIDE 5: fortune telling -->
<section class="slide" id="s5">
  <div class="wrap">
    <div>
      <div class="label"><span class="dot"></span>05 · ИСКАЖЕНИЕ</div>
      <h2 class="title">«Я точно знаю, что будет»</h2>
      <p class="thesis">«Я точно провалю собеседование», «после этого всё станет ужасно» — мозг говорит о будущем так, будто оно уже известно.</p>

      <div class="card worksheet">
        <div class="field">
          <label>Моё предсказание</label>
          <textarea rows="1" placeholder="Что, по-моему, точно произойдёт"></textarea>
        </div>
        <div class="field">
          <label>Насколько я уверен(-а)?</label>
          <div class="pct-row">
            <input type="range" min="0" max="100" value="60" oninput="this.style.setProperty('--val', this.value+'%'); this.nextElementSibling.textContent=this.value+'%'">
            <span class="pct-val">60%</span>
          </div>
        </div>
        <div class="row2">
          <div class="field">
            <label>Что я знаю наверняка</label>
            <textarea rows="1" placeholder="Только факты"></textarea>
          </div>
          <div class="field">
            <label>Что я только предполагаю</label>
            <textarea rows="1" placeholder="Догадки, не факты"></textarea>
          </div>
        </div>
        <div class="field">
          <label>Какой сценарий наиболее реалистичен?</label>
          <textarea rows="1" placeholder="С учётом фактов выше"></textarea>
        </div>
      </div>
      <div class="footline">Мне не нужно знать будущее. Мне достаточно знать, что я смогу справиться с тем, что произойдёт.</div>
    </div>
    <div class="visual-col"><div class="blob"><span class="num">05</span></div></div>
  </div>
</section>

<!-- SLIDE 6: other distortions -->
<section class="slide" id="s6">
  <div class="wrap narrow">
    <div>
      <div class="label"><span class="dot"></span>06 · ЕЩЁ ВАРИАНТЫ</div>
      <h2 class="title">Другие ловушки мышления</h2>
      <p class="thesis" style="max-width:70ch;">Три частых искажения, которые тоже усиливают тревогу. Не нужно запоминать названия — важно научиться замечать их у себя.</p>
      <div class="mini-grid">
        <div class="mini-card">
          <h3>Чёрно-белое мышление</h3>
          <div class="ex">«Если выступлю не идеально — считай, что провалился(-лась)».</div>
          <div class="q">Есть ли между «идеально» и «провал» другие варианты?</div>
        </div>
        <div class="mini-card">
          <h3>Сверхобобщение</h3>
          <div class="ex">«Один раз не получилось — значит, у меня никогда не получится».</div>
          <div class="q">Это правда «всегда» и «никогда» — или один раз?</div>
        </div>
        <div class="mini-card">
          <h3>Долженствование</h3>
          <div class="ex">«Я должен(-жна) справляться со всем без ошибок».</div>
          <div class="q">Что бы я сказал(а) другу с таким же «долгом»?</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- SLIDE 7: acute techniques -->
<section class="slide" id="s7">
  <div class="wrap">
    <div>
      <div class="label"><span class="dot"></span>07 · ЗДЕСЬ И СЕЙЧАС</div>
      <h2 class="title">Когда тревога зашкаливает прямо сейчас</h2>
      <p class="thesis">Сильная тревога связана с активацией части нервной системы, которая переводит тело в режим «опасность / действуй». Медленное дыхание с более длинным выдохом у многих людей способствует снижению этого физиологического возбуждения — хотя и не «выключает» тревогу полностью.</p>

      <div class="text" style="margin-top:6px;"><p><b style="color:var(--clay-deep);">Техника 5–4–3–2–1</b> — способ переключить внимание с тревожных мыслей на то, что происходит здесь и сейчас.</p></div>
      <div class="fivefour">
        <div class="ff-row"><span class="ff-num">5</span><input type="text" placeholder="вещей, которые я вижу"></div>
        <div class="ff-row"><span class="ff-num">4</span><input type="text" placeholder="вещи, которых могу коснуться"></div>
        <div class="ff-row"><span class="ff-num">3</span><input type="text" placeholder="звука, которые слышу"></div>
        <div class="ff-row"><span class="ff-num">2</span><input type="text" placeholder="запаха"></div>
        <div class="ff-row"><span class="ff-num">1</span><input type="text" placeholder="вкус или ощущение во рту"></div>
      </div>
    </div>
    <div class="visual-col">
      <div class="breathe-wrap">
        <div class="breathe-circle"></div>
        <div class="breathe-caption">Дыши в такт кругу: вдох, пока он растёт, выдох чуть длиннее — пока сжимается.</div>
      </div>
    </div>
  </div>
</section>

<!-- SLIDE 8: navigator -->
<section class="slide" id="s8">
  <div class="wrap narrow">
    <div>
      <div class="label"><span class="dot"></span>08 · НАВИГАТОР</div>
      <h2 class="title">Если… → используй</h2>
      <table class="map">
        <tr><td>Тело сильно напряжено, сердце быстро бьётся</td><td>дыхание / 5–4–3–2–1</td></tr>
        <tr><td>Застрял(а) в самом страшном сценарии</td><td>декатастрофизация</td></tr>
        <tr><td>Уверен(а), что знаю, что думает другой человек</td><td>проверка «чтения мыслей»</td></tr>
        <tr><td>Уверен(а), что знаю, что произойдёт</td><td>проверка предсказания будущего</td></tr>
        <tr><td>Мысли постоянно возвращаются к одному и тому же</td><td>выписать мысль + проверить факты</td></tr>
        <tr><td>Не получается оторваться от тревожных мыслей</td><td>переключение внимания</td></tr>
      </table>
      <div class="split-note">
        <div class="box"><b>Техники для тела и внимания</b>помогают снизить интенсивность тревоги здесь и сейчас.</div>
        <div class="box"><b>Когнитивные техники</b>помогают разобраться с мыслями, которые эту тревогу поддерживают. Их можно сочетать.</div>
      </div>
    </div>
  </div>
</section>

<!-- SLIDE 9: final plan -->
<section class="slide" id="s9">
  <div class="wrap narrow">
    <div>
      <div class="label"><span class="dot"></span>09 · МОЙ ПЛАН</div>
      <h2 class="title">Мой антитревожный план</h2>
      <div class="card worksheet">
        <div class="row2">
          <div class="field">
            <label>Сейчас я тревожусь из-за</label>
            <textarea rows="1"></textarea>
          </div>
          <div class="field">
            <label>Моя главная тревожная мысль</label>
            <textarea rows="1"></textarea>
          </div>
        </div>
        <div class="row2">
          <div class="field">
            <label>Какое искажение здесь может быть? <span class="hint">необязательно</span></label>
            <textarea rows="1"></textarea>
          </div>
          <div class="field">
            <label>Более реалистичный взгляд на ситуацию</label>
            <textarea rows="1"></textarea>
          </div>
        </div>
        <div class="field">
          <label>Что я сделаю прямо сейчас</label>
          <div class="checks">
            <label class="check"><input type="checkbox"> Дыхание</label>
            <label class="check"><input type="checkbox"> 5–4–3–2–1</label>
            <label class="check"><input type="checkbox"> Декатастрофизация</label>
            <label class="check"><input type="checkbox"> Переключение внимания</label>
          </div>
        </div>
        <div class="row2" style="margin-top:6px;">
          <div class="field">
            <label>Уровень тревоги до</label>
            <div class="pct-row">
              <input type="range" min="0" max="10" value="6" oninput="this.style.setProperty('--val', (this.value*10)+'%'); this.nextElementSibling.textContent=this.value+'/10'">
              <span class="pct-val">6/10</span>
            </div>
          </div>
          <div class="field">
            <label>Уровень тревоги после</label>
            <div class="pct-row">
              <input type="range" min="0" max="10" value="3" oninput="this.style.setProperty('--val', (this.value*10)+'%'); this.nextElementSibling.textContent=this.value+'/10'">
              <span class="pct-val">3/10</span>
            </div>
          </div>
        </div>
      </div>
      <div class="footline">Мне не нужно полностью избавиться от тревоги. Мне нужно понять, что она пытается сказать, проверить свои мысли и выбрать следующий шаг.</div>
      <div class="care-note">Если тревога регулярно мешает спать, работать, учиться, общаться — или вызывает сильное избегание и панические симптомы, стоит обратиться к специалисту по психическому здоровью.</div>
    </div>
  </div>
</section>

<script>
  const ids = ['s0','s1','s2','s3','s4','s5','s6','s7','s8','s9'];
  const nav = document.getElementById('dotnav');
  ids.forEach((id,i)=>{
    const a = document.createElement('a');
    a.href = '#'+id;
    if(i===0) a.classList.add('active');
    nav.appendChild(a);
  });
  const dots = nav.querySelectorAll('a');
  const progressText = document.getElementById('progressText');
  const sections = ids.map(id=>document.getElementById(id));
  const io = new IntersectionObserver((entries)=>{
    entries.forEach(entry=>{
      if(entry.isIntersecting){
        const idx = sections.indexOf(entry.target);
        dots.forEach(d=>d.classList.remove('active'));
        dots[idx].classList.add('active');
        progressText.textContent = String(idx).padStart(2,'0')+' / 09';
      }
    });
  }, {threshold:0.5});
  sections.forEach(s=>io.observe(s));

  // auto-grow textareas
  document.querySelectorAll('textarea').forEach(t=>{
    t.addEventListener('input', function(){
      this.style.height = 'auto';
      this.style.height = this.scrollHeight+'px';
    });
  });
</script>
</body>
</html>
