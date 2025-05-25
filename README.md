# hukugyouzinndann
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>副業スタイル診断</title>
  <style>
    :root {
      --bg-color: #f4f4f9;
      --card-bg: #ffffff;
      --primary: #0073e6;
      --accent: #ff8c00;
      --text-dark: #333333;
    }
    body {
      background: var(--bg-color);
      font-family: "Noto Sans JP", sans-serif;
      color: var(--text-dark);
      margin: 0;
      padding: 20px;
    }
    .quiz-container {
      max-width: 600px;
      margin: auto;
      background: var(--card-bg);
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      overflow: hidden;
    }
    .progress {
      height: 6px;
      background: #ddd;
      border-radius: 3px;
      overflow: hidden;
      margin: 16px 0;
    }
    .progress-bar {
      height: 100%;
      background: var(--primary);
      width: 0%;
      transition: width 0.3s;
    }
    .slide {
      padding: 24px;
      display: none;
      animation: fadeIn 0.5s ease-in;
    }
    .slide.active {
      display: block;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
    h2 {
      margin-top: 0;
      color: var(--primary);
      font-size: 1.5rem;
    }
    .options { list-style: none; padding: 0; margin: 16px 0; }
    .options li { margin: 10px 0; }
    .options input[type="radio"] { accent-color: var(--accent); margin-right: 8px; }
    .btn {
      display: inline-block;
      background: var(--accent);
      color: #fff;
      border: none;
      padding: 12px 24px;
      border-radius: 6px;
      font-size: 1rem;
      cursor: pointer;
      transition: background 0.3s;
      text-decoration: none;
    }
    .btn:hover { background: #e67e00; }
    .cta { display: block; text-align: center; margin-top: 20px; }
    .result { text-align: center; }
  </style>
</head>
<body>
  <div class="quiz-container">
    <!-- プログレスバー（IDを指定） -->
    <div class="progress">
      <div id="progress" class="progress-bar"></div>
    </div>
    <div id="quiz">
      <!-- スライド 0: 導入 -->
      <div class="slide active" data-step="0">
        <h2>副業スタイル診断スタート！</h2>
        <p>あなたの強みやライフスタイルに合わせた“最適な副業”を簡単チェック！</p>
        <button class="btn" onclick="nextSlide()">▶︎ はじめる</button>
      </div>
      <!-- スライド 1: 質問 q1 -->
      <div class="slide" data-step="1" data-score-key="q1">
        <h2>1. AIやツールを使った仕事に今すぐ取り組みたい度は？</h2>
        <ul class="options">
          <li><label><input type="radio" name="q1" value="3"/>A. 今すぐ始めたい！</label></li>
          <li><label><input type="radio" name="q1" value="2"/>B. 興味はあるが準備が必要</label></li>
          <li><label><input type="radio" name="q1" value="1"/>C. まだ様子見</label></li>
        </ul>
        <button class="btn" onclick="nextSlide()">▶︎ 次へ</button>
      </div>
      <!-- スライド 2: 質問 q2 -->
      <div class="slide" data-step="2" data-score-key="q2">
        <h2>2. １週間あたり、副業にどれくらい時間を割けそう？</h2>
        <ul class="options">
          <li><label><input type="radio" name="q2" value="3"/>A. 10時間以上</label></li>
          <li><label><input type="radio" name="q2" value="2"/>B. 5～10時間</label></li>
          <li><label><input type="radio" name="q2" value="1"/>C. 5時間未満</label></li>
        </ul>
        <button class="btn" onclick="nextSlide()">▶︎ 次へ</button>
      </div>
      <!-- スライド 3: 質問 q3 -->
      <div class="slide" data-step="3" data-score-key="q3">
        <h2>3. 月＋5万円を目指す学習ペースは？</h2>
        <ul class="options">
          <li><label><input type="radio" name="q3" value="3"/>A. 毎日しっかり学ぶ</label></li>
          <li><label><input type="radio" name="q3" value="2"/>B. 週2～3日コツコツ</label></li>
          <li><label><input type="radio" name="q3" value="1"/>C. 週1日ペース</label></li>
        </ul>
        <button class="btn" onclick="nextSlide()">▶︎ 次へ</button>
      </div>
      <!-- スライド 4: 質問 q4 -->
      <div class="slide" data-step="4" data-score-key="q4">
        <h2>4. 得意／楽しめる作業はどれ？</h2>
        <ul class="options">
          <li><label><input type="radio" name="q4" value="3"/>A. データ分析・レポート作成</label></li>
          <li><label><input type="radio" name="q4" value="2"/>B. クリエイティブ制作</label></li>
          <li><label><input type="radio" name="q4" value="1"/>C. ライティング・投稿</label></li>
        </ul>
        <button class="btn" onclick="nextSlide()">▶︎ 次へ</button>
      </div>
      <!-- スライド 5: 質問 q5 -->
      <div class="slide" data-step="5" data-score-key="q5">
        <h2>5. 副業収入を得たい期間は？</h2>
        <ul class="options">
          <li><label><input type="radio" name="q5" value="3"/>A. 3ヶ月以内</label></li>
          <li><label><input type="radio" name="q5" value="2"/>B. 半年以内</label></li>
          <li><label><input type="radio" name="q5" value="1"/>C. 1年以内</label></li>
        </ul>
        <button class="btn" onclick="nextSlide()">▶︎ 次へ</button>
      </div>
      <!-- スライド 6: 質問 q6 -->
      <div class="slide" data-step="6" data-score-key="q6">
        <h2>6. AIスクールに入って学ぶことに対する意欲は？</h2>
        <ul class="options">
          <li><label><input type="radio" name="q6" value="3"/>A. すぐに申し込みたい！</label></li>
          <li><label><input type="radio" name="q6" value="2"/>B. 詳しい情報が欲しい</label></li>
          <li><label><input type="radio" name="q6" value="1"/>C. 自分で調べたい</label></li>
        </ul>
        <button class="btn" onclick="showResult()">▶︎ 結果を見る</button>
      </div>
      <!-- スライド 7: 結果表示 -->
      <div class="slide" data-step="7" id="resultSlide">
        <div class="result">
          <h2>あなたの診断結果は――</h2>
          <p id="resultText"></p>
          <a class="btn cta" href="https://lin.ee/D08E4sf" target="_blank">▶︎ 無料相談はこちら（公式LINE）</a>
        </div>
      </div>
    </div>
  </div>
  <script>
    const slides = document.querySelectorAll('.slide');
    let current = 0;
    const answers = {};

    function updateProgress() {
      const bar = document.getElementById('progress');
      if (bar) {
        const percent = current / (slides.length - 1) * 100;
        bar.style.width = percent + '%';
      }
    }

    function nextSlide() {
      const slide = slides[current];
      const key = slide.getAttribute('data-score-key');
      if (key) {
        const checked = slide.querySelector(`input[name="${key}"]:checked`);
        if (!checked) {
          alert('いずれか選択してください。');
          return;
        }
        answers[key] = parseInt(checked.value);
      }
      slides[current].classList.remove('active');
      current++;
      if (current < slides.length) {
        slides[current].classList.add('active');
        updateProgress();
      }
    }

    function showResult() {
      nextSlide();
      const totalScore = Object.values(answers).reduce((a, b) => a + b, 0);
      let type, msg;
      if (totalScore <= 9) {
        type = 'じっくりスタンダードタイプ';
        msg = 'マイペースに学びたいあなたにおすすめです。';
      } else if (totalScore <= 13) {
        type = 'アクティブチャレンジャータイプ';
        msg = '実践を重視する行動派のあなたにおすすめです。';
      } else if (totalScore <= 16) {
        type = 'マスター志向タイプ';
        msg = '短期集中でスキル習得したいあなたにおすすめです。';
      } else {
        type = 'AIフルコミットタイプ';
        msg = '本格的にコミットする覚悟のあるあなたにおすすめです。';
      }
      document.getElementById('resultText').innerHTML = `【${type}】<br>${msg}`;
    }
    document.addEventListener('DOMContentLoaded', updateProgress);
  </script>
</body>
</html>
