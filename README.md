<!doctype html>
<html lang="ja">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>L-Crown | 西武ライオンズ データ速報</title>
  <style>
    :root{
      --lions-blue:#092048;
      --accent:#1e3a8a;
      --bg:#f5f7fa;
      --card:#ffffff;
      --muted:#94a3b8;
      --border:#e2e8f0;
    }
    body{
      margin:0;
      background:var(--bg);
      font-family:'Hiragino Sans','Noto Sans JP',sans-serif;
      color:#1a1a1a;
    }

    /* ヘッダー */
    header{
      background:var(--lions-blue);
      color:#fff;
      padding:12px 20px;
      font-size:1.3rem;
      font-weight:700;
      display:flex;
      align-items:center;
      justify-content:space-between;
    }
    header .title{ font-size:1.4rem; }

    /* レイアウト */
    .container{
      max-width:1100px;
      margin:0 auto;
      padding:20px;
    }

    /* ▼ 試合速報カード */
    .game-card{
      background:var(--card);
      padding:20px;
      border-radius:14px;
      box-shadow:0 2px 6px rgba(0,0,0,0.08);
      margin-bottom:25px;
    }
    .game-title{
      font-size:1.3rem;
      font-weight:700;
      color:var(--lions-blue);
      margin-bottom:12px;
    }

    /* ▼ ニュース */
    .news-section{
      background:var(--card);
      padding:20px;
      border-radius:14px;
      box-shadow:0 2px 6px rgba(0,0,0,0.08);
      margin-bottom:25px;
    }
    .news-title{
      font-size:1.3rem;
      font-weight:700;
      color:var(--lions-blue);
      margin-bottom:15px;
    }
    .news-list{
      list-style:none;
      padding:0;
      margin:0;
    }
    .news-item{
      display:flex;
      gap:12px;
      padding:10px 0;
      border-bottom:1px solid var(--border);
    }
    .news-item:last-child{ border-bottom:none; }
    .news-date{
      font-size:0.9rem;
      width:90px;
      color:#555;
      flex-shrink:0;
    }
    .news-text{
      text-decoration:none;
      color:#1a1a1a;
      font-size:1rem;
    }
    .news-text:hover{ text-decoration:underline; }

    /* ▼ TOP3ランキング */
    .rank-section{
      background:var(--card);
      padding:20px;
      border-radius:14px;
      box-shadow:0 2px 6px rgba(0,0,0,0.08);
      margin-bottom:25px;
    }
    .rank-header{
      font-size:1.3rem;
      font-weight:700;
      color:var(--lions-blue);
      margin-bottom:12px;
    }
    .rank-buttons{
      display:flex;
      gap:10px;
      margin-bottom:12px;
    }
    .rank-btn{
      padding:6px 12px;
      border-radius:8px;
      background:#e5eaf3;
      border:none;
      cursor:pointer;
    }
    .rank-btn.active{
      background:var(--lions-blue);
      color:#fff;
      font-weight:700;
    }
    .rank-list{
      list-style:none;
      padding:0;
      margin:0;
    }
    .rank-item{
      padding:10px 0;
      border-bottom:1px solid var(--border);
    }
    .rank-item:last-child{ border-bottom:none; }

    /* ▼ フッター */
    footer{
      text-align:center;
      color:var(--muted);
      padding:30px 0;
      margin-top:40px;
    }
  </style>
</head>
<body>

<header>
  <div class="title">L-Crown（西武ライオンズ データサイト）</div>
</header>

<div class="container">

  <!-- ▼ 試合速報エリア -->
  <section class="game-card">
    <h2 class="game-title">試合速報</h2>
    <p>ここに最新の試合速報を掲載します。（スコアカードや状況など）</p>
  </section>

  <!-- ▼ ニュースエリア -->
  <section class="news-section">
    <h2 class="news-title">ニュース</h2>
    <ul class="news-list">
      <li class="news-item">
        <span class="news-date">2025/03/01</span>
        <a href="#" class="news-text">サイトをリニューアルしました。</a>
      </li>
      <li class="news-item">
        <span class="news-date">2025/02/28</span>
        <a href="#" class="news-text">選手データを最新版に更新しました。</a>
      </li>
      <li class="news-item">
        <span class="news-date">2025/02/27</span>
        <a href="#" class="news-text">今季の日程ページを公開しました。</a>
      </li>
    </ul>
  </section>

  <!-- ▼ ランキングエリア -->
  <section class="rank-section">
    <h2 class="rank-header">TOP3 ランキング</h2>

    <div class="rank-buttons">
      <button class="rank-btn active" onclick="showRank('bat')">打撃</button>
      <button class="rank-btn" onclick="showRank('pit')">投球</button>
    </div>

    <ul id="rank-bat" class="rank-list">
      <li class="rank-item">1位 ●●：打率 .345</li>
      <li class="rank-item">2位 ●●：打率 .321</li>
      <li class="rank-item">3位 ●●：打率 .310</li>
    </ul>

    <ul id="rank-pit" class="rank-list" style="display:none;">
      <li class="rank-item">1位 ●●：防御率 1.23</li>
      <li class="rank-item">2位 ●●：防御率 1.85</li>
      <li class="rank-item">3位 ●●：防御率 2.20</li>
    </ul>
  </section>

</div>

<footer>
  © 2025 L-Crown / Seibu Lions Data
</footer>

<script>
function showRank(type){
  document.getElementById("rank-bat").style.display = (type === 'bat') ? "block" : "none";
  document.getElementById("rank-pit").style.display = (type === 'pit') ? "block" : "none";
  
  document.querySelectorAll('.rank-btn').forEach(btn => btn.classList.remove('active'));
  if(type === 'bat'){
    document.querySelector('.rank-buttons button:nth-child(1)').classList.add('active');
  } else {
    document.querySelector('.rank-buttons button:nth-child(2)').classList.add('active');
  }
}
</script>

</body>
</html>
