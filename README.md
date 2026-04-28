<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ANIME-BIZ AI 컨설턴트 | 캡스톤 프로젝트</title>
  
  <link rel="stylesheet" as="style" crossorigin href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.css" />
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  
  <style>
    /* 웹사이트 고급 디자인 (CSS) */
    :root {
      --primary-color: #3498db; /* 신뢰감을 주는 블루 */
      --secondary-color: #e67e22; /* 포인트 오렌지 (일본 애니 느낌) */
      --text-color: #2c3e50;
      --bg-light: #ecf0f1;
      --white: #ffffff;
    }

    body {
      font-family: 'Pretendard', sans-serif;
      background-color: var(--bg-light);
      color: var(--text-color);
      margin: 0;
      padding: 0;
      line-height: 1.6;
    }

    /* 1. 하이라이트 배너 영역 (Hero Section) */
    .hero {
      background: linear-gradient(135deg, #1e375a 0%, #3498db 100%);
      color: var(--white);
      padding: 80px 20px;
      text-align: center;
      position: relative;
      overflow: hidden;
    }
    
    /* 빙과 vs 이태원 느낌을 주는 추상적인 오버레이 디자인 */
    .hero::before {
      content: '';
      position: absolute;
      top: -50%;
      left: -20%;
      width: 80%;
      height: 200%;
      background: rgba(230, 126, 34, 0.1);
      transform: rotate(-15deg);
      border-radius: 50%;
    }

    .hero-content {
      position: relative;
      z-index: 2;
      max-width: 900px;
      margin: 0 auto;
    }

    .hero-tag {
      display: inline-block;
      background-color: var(--secondary-color);
      color: white;
      padding: 5px 15px;
      border-radius: 20px;
      font-weight: bold;
      font-size: 0.9em;
      margin-bottom: 15px;
      box-shadow: 0 4px 6px rgba(0,0,0,0.2);
    }

    .hero h1 {
      font-size: 3em;
      margin: 0 0 15px 0;
      font-weight: 800;
      letter-spacing: -1px;
    }

    .hero p {
      font-size: 1.2em;
      opacity: 0.9;
      max-width: 600px;
      margin: 0 auto;
    }

    /* 메인 컨텐츠 영역 */
    .container {
      max-width: 1000px;
      margin: -50px auto 50px auto; /* 배너 위로 살짝 겹치게 */
      padding: 0 20px;
      position: relative;
      z-index: 3;
    }

    /* 섹션 공통 스타일 */
    .main-section {
      background-color: var(--white);
      padding: 40px;
      border-radius: 16px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.05);
      margin-bottom: 30px;
    }

    h2 {
      color: var(--text-color);
      font-size: 1.8em;
      margin-top: 0;
      margin-bottom: 25px;
      display: flex;
      align-items: center;
      gap: 10px;
    }
    
    h2 i {
      color: var(--primary-color);
    }

    /* 2. 프로젝트 소개 영역 */
    .intro-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 30px;
      margin-top: 20px;
    }

    .intro-card {
      background-color: #f8f9fa;
      padding: 20px;
      border-radius: 10px;
      border: 1px solid #eee;
    }
    
    .intro-card strong {
      display: block;
      color: var(--primary-color);
      font-size: 1.1em;
      margin-bottom: 8px;
    }

    /* 3. 구글 폼 영역 */
    .form-section {
      padding: 20px; /* 아이프레임 주변 여백 */
    }

    .form-section iframe {
      width: 100%;
      height: 750px;
      border: none;
      border-radius: 12px;
      background: #fafafa;
    }

    /* 4. AI 분석 결과 영역 */
    #results {
      margin-top: 20px;
    }

    .result-card {
      background-color: var(--white);
      border: 1px solid #eee;
      padding: 25px;
      margin-bottom: 25px;
      border-radius: 12px;
      transition: all 0.3s ease; /* 호버 애니메이션 */
      position: relative;
    }

    .result-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 10px 20px rgba(0,0,0,0.08);
      border-color: #d6eaf8;
    }

    .result-card h3 {
      margin-top: 0;
      color: var(--text-color);
      font-size: 1.4em;
      border-bottom: 1px solid #eee;
      padding-bottom: 10px;
    }

    .probability-badge {
      position: absolute;
      top: 25px;
      right: 25px;
      background-color: var(--secondary-color);
      color: white;
      padding: 8px 15px;
      border-radius: 8px;
      font-weight: 800;
      font-size: 1.1em;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    }

    .result-content {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 20px;
      margin-top: 15px;
    }

    .result-item {
      background-color: #fbfcfc;
      padding: 15px;
      border-radius: 8px;
      border: 1px solid #f0f0f0;
    }

    .result-item strong {
      display: block;
      color: var(--primary-color);
      margin-bottom: 5px;
      display: flex;
      align-items: center;
      gap: 5px;
    }

    .loading-text {
      text-align: center;
      color: #999;
      font-size: 1.1em;
      padding: 40px;
    }

    /* 푸터 영역 */
    footer {
      text-align: center;
      padding: 30px;
      color: #7f8c8d;
      font-size: 0.9em;
    }
  </style>
  
  <script src="https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.3.2/papaparse.min.js"></script>
</head>
<body>

  <header class="hero">
    <div class="hero-content">
      <div class="hero-tag">CAPSTONE PROJECT</div>
      <h1>ANIME-BIZ AI 컨설턴트</h1>
      <p>애니메이션 성지순례와 지역 상권의 데이터를 분석하여, 여러분의 지역 활성화 기획안에 성공적인 AI 솔루션을 제공합니다.</p>
    </div>
  </header>

  <div class="container">
    
    <section class="main-section">
      <h2><i class="fas fa-info-circle"></i> 시스템 소개 및 이용 가이드</h2>
      <p>본 시스템은 다카야마시의 <빙과> 성지순례 성공 사례와 현대적인 상권(예: 이태원)의 특성을 비교 분석한 AI 모델을 기반으로 작동합니다. 아래 폼에 기획안을 제출하시면, Make 자동화 로봇이 무료 Google Gemini AI를 활용하여 즉시 분석을 진행합니다.</p>
      
      <div class="intro-grid">
        <div class="intro-card">
          <strong><i class="fas fa-check-circle"></i> 성공 확률 높이는 팁</strong>
          단순 방문을 넘어선 '체험형 콘텐츠', '지역 상권과의 수익 공유 구조', '지속 가능한 파트너십'을 기획내용에 포함하세요.
        </div>
        <div class="intro-card">
          <strong><i class="fas fa-exclamation-triangle"></i> 주의사항</strong>
          단발성 이벤트나 단순 포토존 설치 위주의 기획은 AI가 '지속성 부족'으로 판단하여 낮은 점수를 줄 수 있습니다.
        </div>
      </div>
    </section>

    <section class="main-section form-section">
      <h2><i class="fas fa-pen-fancy"></i> 1. 기획안 제출하기</h2>
      <iframe src="https://docs.google.com/forms/d/e/1FAIpQLSfGfqgT9i3M97qU-rwgqz7jklNgUnA-WernWtEOPq825fGNDQ/viewform?embedded=true">로드 중...</iframe>
    </section>

    <section class="main-section">
      <h2><i class="fas fa-chart-bar"></i> 2. AI 실시간 분석 결과</h2>
      <div id="results" class="loading-text">
        <i class="fas fa-spinner fa-spin"></i> 구글 스프레드시트에서 데이터를 불러오는 중입니다...
      </div>
    </section>
  </div>

  <footer>
    © 2024 캡스톤 프로젝트 - 지역 활성화 AI 분석 시스템
  </footer>

  <script>
    // ⚠️ 매우 중요: 아래 따옴표 안에 아까 발급받은 '구글 스프레드시트 CSV 웹 게시 링크'를 붙여넣으세요!
    const sheetCSVUrl = '여기에_구글_스프레드시트_웹_게시_CSV_링크를_넣으세요';

    function loadResults() {
      if (sheetCSVUrl === '여기에_구글_스프레드시트_웹_게시_CSV_링크를_넣으세요') {
        document.getElementById('results').innerHTML = '<div class="result-card" style="border-color: #e74c3c; color: #e74c3c;"><strong>⚠️ 설정 필요:</strong> 코드를 열어서 하단의 <code>sheetCSVUrl</code> 변수에 구글 스프레드시트 CSV 링크를 연결해 주세요!</div>';
        return;
      }

      Papa.parse(sheetCSVUrl, {
        download: true,
        header: true,
        complete: function(results) {
          const data = results.data;
          const resultsDiv = document.getElementById('results');
          resultsDiv.innerHTML = ''; 

          // 최신 데이터가 위로 오도록 역순으로 출력
          for (let i = data.length - 1; i >= 0; i--) {
            const row = data[i];
            
            // 데이터가 있는 행만 출력
            if (row['기획안 제목']) { 
              const card = `
                <div class="result-card">
                  <h3>📌 ${row['기획안 제목']}</h3>
                  <div class="probability-badge">${row['AI 예상 성공 확률'] || '--%'}</div>
                  
                  <div class="result-content">
                    <div class="result-item">
                      <strong><i class="fas fa-brain"></i> AI 구조화 평가</strong>
                      ${row['AI 구조화 평가'] || 'Make 로봇이 분석을 준비하고 있습니다.'}
                    </div>
                    <div class="result-item">
                      <strong><i class="fas fa-lightbulb"></i> AI 핵심 보완 피드백</strong>
                      ${row['AI 핵심 보완 피드백'] || '잠시 후 새로고침 해주세요.'}
                    </div>
                  </div>
                </div>
              `;
              resultsDiv.innerHTML += card;
            }
          }
        }
      });
    }

    // 웹페이지가 열리면 즉시 데이터 불러오기
    window.onload = loadResults;
  </script>

</body>
</html>
