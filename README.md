<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>L-Crown | 西武ライオンズ データ速報</title>
  <style>
    :root {
      --lions-blue:#092048;
      --hawks-yellow:#ffcc00;
      --bg:#f5f7fa;
      --card:#ffffff;
      --muted:#94a3b8;
      --score-bg: rgba(255,255,255,0.06);
    }
    body {
      margin:0;
      background:var(--bg);
      font-family:'Hiragino Sans','Noto Sans JP',sans-serif;
      color:#1a1a1a;
    }

    /* ヘッダー */
    header {
      position:sticky; top:0; background:var(--lions-blue); color:#fff;
      padding:12px 20px; display:flex; justify-content:space-between; align-items:center; z-index:50;
    }
    header .title { font-size:1.4rem; font-weight:700; }
    .nav-menu { display:flex; gap:20px; }
    .nav-menu a { color:#fff; text-decoration:none; font-weight:600; }

    .container{ max-width:1100px; margin:0 auto; padding:20px; }

    /* 試合速報 */
    .game-card{ background:var(--card); padding:20px; border-radius:14px; box-shadow:0 2px 6px rgba(0,0,0,0.08); margin-bottom:25px; }
    .match-card{ width:100%; padding:14px; border-radius:14px; background:var(--card); color:#000; box-shadow:0 6px 20px rgba(2,6,23,0.15); display:flex; gap:16px; align-items:center; flex-wrap:wrap; }
    .teams{ display:flex; flex:1; align-items:center; gap:16px; flex-wrap:wrap; }
    .team{ flex:1 1 120px; display:flex; align-items:center; gap:14px; }
    .logo{ width:56px; height:56px; border-radius:12px; overflow:hidden; display:flex; align-items:center; justify-content:center; background:linear-gradient(135deg, rgba(255,255,255,0.02), rgba(255,255,255,0.04)); border:2px solid rgba(0,0,0,0.05); flex-shrink:0; }
    .team-name{ font-size:15px; font-weight:600; }
    .team-sub{ font-size:12px; color:var(--muted); }
    .lions .team-name{ color:var(--lions-blue); }
    .hawks .team-name{ color:var(--hawks-yellow); }
    .score{ display:flex; flex-direction:row; align-items:center; justify-content:center; padding:10px 14px; border-radius:14px; background:var(--score-bg); gap:8px; flex-shrink:0; }
    .score .runs{ font-size:36px; font-weight:800; }
    .meta{ display:flex; flex-direction:column; align-items:flex-end; gap:6px; }
    .inning{ padding:6px 10px; border-radius:999px; font-weight:600; font-size:13px; background:#f3f4f6; }

    /* ニュース */
    .news-section{ background:var(--card); padding:20px; border-radius:14px; box-shadow:0 2px 6px rgba(0,0,0,0.08); margin-bottom:25px; }

    /* TOP3ランキング */
    .rank-section{ background:var(--card); padding:20px; border-radius:14px; box-shadow:0 2px 6px rgba(0,0,0,0.08); margin-bottom:25px; }
    .ranking-tabs{ display:flex; gap:10px; margin-bottom:14px; }
    .ranking-tabs button{ padding:8px 14px; border-radius:8px; border:none; background:#e5e7eb; cursor:pointer; font-weight:600; }
    .ranking-tabs button.active{ background:var(--lions-blue); color:#fff; }
    .ranking-content{ display:none; }
    .ranking-content.active{ display:block; }
    .ranking-card{ display:flex; gap:12px; padding:12px; background:#fff; border-radius:12px; margin-bottom:10px; border-left:5px solid var(--lions-blue); box-shadow:0 2px 6px rgba(0,0,0,0.05); }
    .rank-num{ font-size:1.3rem; font-weight:700; }
    .player-name{ font-size:1.05rem; font-weight:700; }
    .player-detail{ font-size:0.95rem; color:#555; }
  </style>
</head>
<body>

<header>
  <div class="title">L-Crown（西武ライオンズ データサイト）</div>
  <nav class="nav-menu">
    <a href="game">試合速報</a>
    <a href="news">ニュース</a>
    <a href="about">サイトについて</a>
  </nav>
</header>

<div class="container">
  <!-- 試合速報 -->
  <section class="game-card" id="game">
    <h2>試合速報</h2>
    <div class="match-card">
      <div class="teams">
        <div class="team lions">
          <div class="logo"><span>L</span></div>
          <div><div class="team-name">Lions</div><div class="team-sub">埼玉西武</div></div>
        </div>
        <div class="score"><div class="runs">3 - 2</div></div>
        <div class="team hawks">
          <div class="logo"><span>H</span></div>
          <div><div class="team-name">Hawks</div><div class="team-sub">福岡ソフトバンク</div></div>
        </div>
      </div>
      <div class="meta"><div class="inning">7回表</div><div class="status">ベルーナドーム</div></div>
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

  <!-- TOP3ランキング -->
  <section class="rank-section" id="rank">
    <h2>TOP3 ランキング</h2>
    <div class="ranking-tabs">
      <button class="active" data-target="batting">打撃</button>
      <button data-target="pitching">投球</button>
    </div>

    <div id="batting" class="ranking-content active">
      <div class="ranking-card"><div class="rank-num">1</div><div><div class="player-name">山川 穂高</div><div class="player-detail">打率 .320 / HR 35</div></div></div>
      <div class="ranking-card"><div class="rank-num">2</div><div><div class="player-name">森 友哉</div><div class="player-detail">打率 .310 / HR 28</div></div></div>
      <div class="ranking-card"><div class="rank-num">3</div><div><div class="player-name">源田 壮亮</div><div class="player-detail">打率 .305 / 盗塁 25</div></div></div>
    </div>

    <div id="pitching" class="ranking-content">
      <div class="ranking-card"><div class="rank-num">1</div><div><div class="player-name">髙橋 光成</div><div class="player-detail">防御率 2.10 / 12勝</div></div></div>
      <div class="ranking-card"><div class="rank-num">2</div><div><div class="player-name">平良 海馬</div><div class="player-detail">防御率 2.30 / 30H</div></div></div>
      <div class="ranking-card"><div class="rank-num">3</div><div><div class="player-name">増田 達至</div><div class="player-detail">防御率 2.50 / 28S</div></div></div>
    </div>
  </section>
</div>

<footer style="text-align:center; padding:40px; color:#777;">© 2025 L-Crown / Seibu Lions Data</footer>

<script>
const tabs = document.querySelectorAll('.ranking-tabs button');
const contents = document.querySelectorAll('.ranking-content');
tabs.forEach(btn => {
  btn.addEventListener('click', () => {
    tabs.forEach(t => t.classList.remove('active'));
    btn.classList.add('active');
    contents.forEach(c => c.classList.remove('active'));
    document.getElementById(btn.dataset.target).classList.add('active');
  });
});
</script>

</body>
</html>
