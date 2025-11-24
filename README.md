</head>
<body>

<header>
  <div class="title">L-Crown（西武ライオンズ データサイト）</div>

  <input type="checkbox" id="nav-toggle" class="nav-toggle">
  <label for="nav-toggle" class="nav-toggle-label">
    <span></span>
  </label>

  <div class="overlay"></div>

  <nav class="nav-menu">
    <ul>
      <li><a href="#game">試合速報</a></li>
      <li><a href="#news">ニュース</a></li>
      <li><a href="#rank">TOP3</a></li>
    </ul>
  </nav>
</header>

<div class="container">

  <!-- 試合速報 -->
  <section class="game-card" id="game">
    <h2>試合速報</h2>

    <div class="match-card">
      <div class="teams">
        <div class="team lions">
          <div class="logo"><span class="fallback">L</span></div>
          <div>
            <div class="team-name">Lions</div>
            <div class="team-sub">埼玉西武</div>
          </div>
        </div>

        <div class="score">
          <div class="runs">3 - 2</div>
        </div>

        <div class="team hawks">
          <div class="logo"><span class="fallback">H</span></div>
          <div>
            <div class="team-name">Hawks</div>
            <div class="team-sub">福岡ソフトバンク</div>
          </div>
        </div>
      </div>

      <div class="meta">
        <div class="inning">7回表</div>
        <div class="status">ベルーナドーム</div>
      </div>
    </div>
  </section>

  <!-- ニュース -->
  <section class="news-section" id="news">
    <h2>ニュース</h2>
    <ul>
      <li>2025/03/01 サイトをリニューアルしました。</li>
      <li>2025/02/28 選手データを最新版に更新しました。</li>
      <li>2025/02/27 今季の日程ページを公開しました。</li>
    </ul>
  </section>

  <!-- TOP3 ランキング -->
  <section class="rank-section" id="rank">
    <h2>TOP3 ランキング</h2>

    <!-- メインタブ -->
    <div class="ranking-tabs main-tabs">
      <button class="active" data-target="batting">打撃</button>
      <button data-target="pitching">投球</button>
    </div>

    <!-- 打撃 -->
    <div id="batting" class="ranking-block active">
      <div class="ranking-tabs sub-tabs">
        <button class="active" data-target="avg">打率</button>
        <button data-target="hr">本塁打</button>
        <button data-target="rbi">打点</button>
        <button data-target="sb">盗塁</button>
      </div>

      <div id="avg" class="ranking-content active">
        <div class="ranking-card"><div class="rank-num">1</div><div><div class="player-name">山川 穂高</div><div class="player-detail">.320</div></div></div>
        <div class="ranking-card"><div class="rank-num">2</div><div><div class="player-name">森 友哉</div><div class="player-detail">.310</div></div></div>
        <div class="ranking-card"><div class="rank-num">3</div><div><div class="player-name">源田 壮亮</div><div class="player-detail">.305</div></div></div>
      </div>

      <div id="hr" class="ranking-content">
        <div class="ranking-card"><div class="rank-num">1</div><div><div class="player-name">山川 穂高</div><div class="player-detail">35本</div></div></div>
        <div class="ranking-card"><div class="rank-num">2</div><div><div class="player-name">森 友哉</div><div class="player-detail">28本</div></div></div>
        <div class="ranking-card"><div class="rank-num">3</div><div><div class="player-name">源田 壮亮</div><div class="player-detail">20本</div></div></div>
      </div>

      <div id="rbi" class="ranking-content">
        <div class="ranking-card"><div class="rank-num">1</div><div><div class="player-name">山川 穂高</div><div class="player-detail">98打点</div></div></div>
        <div class="ranking-card"><div class="rank-num">2</div><div><div class="player-name">森 友哉</div><div class="player-detail">85打点</div></div></div>
        <div class="ranking-card"><div class="rank-num">3</div><div><div class="player-name">源田 壮亮</div><div class="player-detail">70打点</div></div></div>
      </div>

      <div id="sb" class="ranking-content">
        <div class="ranking-card"><div class="rank-num">1</div><div><div class="player-name">源田 壮亮</div><div class="player-detail">25盗塁</div></div></div>
        <div class="ranking-card"><div class="rank-num">2</div><div><div class="player-name">森 友哉</div><div class="player-detail">12盗塁</div></div></div>
        <div class="ranking-card"><div class="rank-num">3</div><div><div class="player-name">山川 穂高</div><div class="player-detail">8盗塁</div></div></div>
      </div>
    </div>

    <!-- 投球 -->
    <div id="pitching" class="ranking-block">
      <div class="ranking-tabs sub-tabs">
        <button class="active" data-target="era">防御率</button>
        <button data-target="so">奪三振</button>
        <button data-target="app">登板</button>
        <button data-target="win">勝利</button>
      </div>

      <div id="era" class="ranking-content active">
        <div class="ranking-card"><div class="rank-num">1</div><div><div class="player-name">髙橋 光成</div><div class="player-detail">2.10</div></div></div>
        <div class="ranking-card"><div class="rank-num">2</div><div><div class="player-name">平良 海馬</div><div class="player-detail">2.30</div></div></div>
        <div class="ranking-card"><div class="rank-num">3</div><div><div class="player-name">増田 達至</div><div class="player-detail">2.50</div></div></div>
      </div>

      <div id="so" class="ranking-content">
        <div class="ranking-card"><div class="rank-num">1</div><div><div class="player-name">髙橋 光成</div><div class="player-detail">188奪三振</div></div></div>
        <div class="ranking-card"><div class="rank-num">2</div><div><div class="player-name">平良 海馬</div><div class="player-detail">175奪三振</div></div></div>
        <div class="ranking-card"><div class="rank-num">3</div><div><div class="player-name">増田 達至</div><div class="player-detail">160奪三振</div></div></div>
      </div>

      <div id="app" class="ranking-content">
        <div class="ranking-card"><div class="rank-num">1</div><div><div class="player-name">髙橋 光成</div><div class="player-detail">65試合</div></div></div>
        <div class="ranking-card"><div class="rank-num">2</div><div><div class="player-name">平良 海馬</div><div class="player-detail">61試合</div></div></div>
        <div class="ranking-card"><div class="rank-num">3</div><div><div class="player-name">増田 達至</div><div class="player-detail">58試合</div></div></div>
      </div>

      <div id="win" class="ranking-content">
        <div class="ranking-card"><div class="rank-num">1</div><div><div class="player-name">髙橋 光成</div><div class="player-detail">12勝</div></div></div>
        <div class="ranking-card"><div class="rank-num">2</div><div><div class="player-name">平良 海馬</div><div class="player-detail">10勝</div></div></div>
        <div class="ranking-card"><div class="rank-num">3</div><div><div class="player-name">増田 達至</div><div class="player-detail">9勝</div></div></div>
      </div>
    </div>
  </section>

</div>

<footer style="text-align:center; padding:40px; color:#777;">
  © 2025 L-Crown / Seibu Lions Data
</footer>

<script>
// メインタブ切替
document.querySelectorAll('.main-tabs button').forEach(btn=>{
  btn.addEventListener('click', ()=>{
    document.querySelectorAll('.main-tabs button').forEach(t=>t.classList.remove('active'));
    btn.classList.add('active');
    document.querySelectorAll('.ranking-block').forEach(b=>b.classList.remove('active'));
    document.getElementById(btn.dataset.target).classList.add('active');
    // サブタブ初期化
    const subTabs = document.querySelector(`#${btn.dataset.target} .sub-tabs button`);
    if(subTabs){ subTabs.click(); }
  });
});

// サブタブ切替
document.querySelectorAll('.sub-tabs button').forEach(btn=>{
  btn.addEventListener('click', ()=>{
    const container = btn.closest('.ranking-block');
    container.querySelectorAll('.sub-tabs button').forEach(t=>t.classList.remove('active'));
    btn.classList.add('active');
    container.querySelectorAll('.ranking-content').forEach(c=>c.classList.remove('active'));
    container.querySelector(`#${btn.dataset.target}`).classList.add('active');
  });
});
</script>

</body>
</html>
