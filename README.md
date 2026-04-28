<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ANIME-BIZ AI 컨설턴트 | 캡스톤 프로젝트</title>
  
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.css" />
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  
  <style>
    :root { --primary: #3498db; --secondary: #e67e22; --text: #2c3e50; --bg: #f0f2f5; --white: #fff; }
    body { font-family: 'Pretendard', sans-serif; background: var(--bg); color: var(--text); margin: 0; }
    
    /* 상단 배너 */
    .hero { background: linear-gradient(135deg, #1e375a 0%, #3498db 100%); color: var(--white); padding: 40px 20px; text-align: center; }
    .hero h1 { margin: 0; font-size: 2.2em; font-weight: 800; }
    
    /* 메인 컨테이너 */
    .container { max-width: 900px; margin: 20px auto 50px; padding: 0 20px; }
    
    /* 탭 메뉴 디자인 */
    .tab-menu { display: flex; justify-content: center; gap: 15px; margin-bottom: 30px; }
    .tab-btn { background: var(--white); border: 2px solid #ddd; color: #777; padding: 12px 25px; border-radius: 30px; font-size: 1.1em; font-weight: bold; cursor: pointer; transition: 0.3s; }
    .tab-btn:hover { border-color: var(--primary); color: var(--primary); }
    .tab-btn.active { background: var(--primary); border-color: var(--primary); color: var(--white); box-shadow: 0 4px 10px rgba(52, 152, 219, 0.3); }

    /* 콘텐츠 영역 */
    .tab-content { display: none; background: var(--white); padding: 30px; border-radius: 15px; box-shadow: 0 5px 20px rgba(0,0,0,0.05); animation: fadeIn 0.4s; }
    .tab-content.active { display: block; }
    @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

    /* 구글 폼 */
    iframe { width: 100%; height: 800px; border: none; border-radius: 8px; }

    /* 결과 카드 */
    .result-card { background: #f8f9fa; border-left: 6px solid var(--primary); padding: 20px; margin-bottom: 20px; border-radius: 8px; position: relative; }
    .result-card h3 { margin-top: 0; color: #2980b9; }
    .prob-badge { position: absolute; top: 20px; right: 20px; background: var(--secondary); color: white; padding: 5px 12px; border-radius: 20px; font-weight: bold; font-size: 0.9em; }
    .res-box { margin-top: 15px; background: var(--white); padding: 15px; border-radius: 8px; border: 1px solid #eee; }
    .res-box strong { color: var(--primary); display: block; margin-bottom: 5px; }
  </style>
  
  <script src="https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.3.2/papaparse.min.js"></script>
</head>
<body>

  <header class="hero">
    <h1>🚀 ANIME-BIZ AI 컨설턴트</h1>
    <p>지역 활성화 기획안 제출 및 실시간 AI 분석</p>
  </header>

  <div class="container">
    
    <div class="tab-menu">
      <button class="tab-btn active" onclick="openTab('submitTab', this)"><i class="fas fa-pen"></i> 기획안 제출</button>
      <button class="tab-btn" onclick="openTab('resultTab', this); fetchResults();"><i class="fas fa-chart-bar"></i> 분석 결과 확인</button>
    </div>

    <div id="submitTab" class="tab-content active">
      <iframe src="https://docs.google.com/forms/d/e/1FAIpQLSfGfqgT9i3M97qU-rwgqz7jklNgUnA-WernWtEOPq825fGNDQ/viewform?embedded=true">로드 중...</iframe>
    </div>

    <div id="resultTab" class="tab-content">
      <div id="results-container">
        <p style="text-align:center; color:#888;"><i class="fas fa-spinner fa-spin"></i> 분석 데이터를 불러오는 중...</p>
      </div>
    </div>

  </div>

  <script>
    // ⚠️ 여기에 구글 스프레드시트 웹 게시 CSV 링크를 꼭 넣어주세요!
    const csvUrl = '여기에_웹게시_CSV_링크를_넣으세요';

    // 탭 전환 기능
    function openTab(tabName, btn) {
      document.querySelectorAll('.tab-content').forEach(tab => tab.classList.remove('active'));
      document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
      document.getElementById(tabName).classList.add('active');
      btn.classList.add('active');
    }

    // 결과 불러오기 기능
    function fetchResults() {
      if (csvUrl === 'https://docs.google.com/spreadsheets/d/1WbBuZokGh77HuEmz8pP9YDtpnYyRjz1kA9IhObQl45w/edit?usp=sharing') {
        document.getElementById('results-container').innerHTML = '<p style="color:red; text-align:center;">⚠️ 코드를 열어서 CSV 링크를 연결해 주세요!</p>';
        return;
      }

      Papa.parse(csvUrl, {
        download: true,
        header: true,
        complete: function(results) {
          const data = results.data;
          const container = document.getElementById('results-container');
          container.innerHTML = '';

          for (let i = data.length - 1; i >= 0; i--) {
            const row = data[i];
            if (row['기획안 제목']) {
              container.innerHTML += `
                <div class="result-card">
                  <div class="prob-badge">예상 성공률: ${row['AI 예상 성공 확률'] || '--%'}</div>
                  <h3>📌 ${row['기획안 제목']}</h3>
                  <div class="res-box">
                    <strong><i class="fas fa-microchip"></i> AI 구조화 평가</strong>
                    ${row['AI 구조화 평가'] || '분석 대기 중...'}
                  </div>
                  <div class="res-box">
                    <strong><i class="fas fa-lightbulb"></i> 핵심 보완 피드백</strong>
                    ${row['AI 핵심 보완 피드백'] || '분석 대기 중...'}
                  </div>
                </div>
              `;
            }
          }
        }
      });
    }
  </script>
</body>
</html>
