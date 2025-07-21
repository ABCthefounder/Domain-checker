<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🌐 도메인 체커 Pro - Domain Availability Checker</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .header {
            text-align: center;
            color: white;
            margin-bottom: 30px;
            animation: fadeInDown 0.8s ease-out;
        }

        .header h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .header p {
            font-size: 1.1rem;
            opacity: 0.9;
        }

        .info-banner {
            background: rgba(255, 193, 7, 0.9);
            color: #856404;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
            text-align: center;
            font-weight: 500;
        }

        .main-content {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 30px;
            animation: fadeInUp 0.8s ease-out 0.2s both;
        }

        .card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 40px rgba(0, 0, 0, 0.15);
        }

        .card-title {
            font-size: 1.3rem;
            font-weight: bold;
            color: #4a5568;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .input-section {
            margin-bottom: 20px;
        }

        .input-group {
            margin-bottom: 15px;
        }

        .input-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: 500;
            color: #4a5568;
        }

        .input-row {
            display: flex;
            gap: 10px;
            align-items: end;
        }

        input[type="text"], textarea, select {
            width: 100%;
            padding: 12px 16px;
            border: 2px solid #e2e8f0;
            border-radius: 10px;
            font-size: 14px;
            transition: all 0.3s ease;
            background: white;
        }

        input[type="text"]:focus, textarea:focus, select:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        textarea {
            resize: vertical;
            min-height: 100px;
            font-family: inherit;
        }

        .btn {
            padding: 12px 24px;
            border: none;
            border-radius: 10px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 14px;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            text-decoration: none;
            min-width: 120px;
            justify-content: center;
        }

        .btn-primary {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(102, 126, 234, 0.4);
        }

        .btn-success {
            background: linear-gradient(135deg, #48bb78 0%, #38a169 100%);
            color: white;
        }

        .btn-success:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(72, 187, 120, 0.4);
        }

        .btn-warning {
            background: linear-gradient(135deg, #ed8936 0%, #dd6b20 100%);
            color: white;
        }

        .btn-warning:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(237, 137, 54, 0.4);
        }

        .btn-danger {
            background: linear-gradient(135deg, #f56565 0%, #e53e3e 100%);
            color: white;
        }

        .btn:disabled {
            opacity: 0.6;
            cursor: not-allowed;
            transform: none !important;
            box-shadow: none !important;
        }

        .control-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 20px;
        }

        .interval-control {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .interval-control input {
            width: 80px;
        }

        .progress-container {
            margin: 20px 0;
        }

        .progress-bar {
            width: 100%;
            height: 8px;
            background: #e2e8f0;
            border-radius: 4px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #667eea, #764ba2);
            width: 0%;
            transition: width 0.3s ease;
        }

        .status-display {
            margin-top: 15px;
            padding: 12px;
            border-radius: 8px;
            font-weight: 500;
            text-align: center;
            min-height: 20px;
        }

        .status-ready {
            background: #f0fff4;
            color: #38a169;
            border: 1px solid #9ae6b4;
        }

        .status-checking {
            background: #ebf8ff;
            color: #3182ce;
            border: 1px solid #90cdf4;
        }

        .status-complete {
            background: #f0fff4;
            color: #38a169;
            border: 1px solid #9ae6b4;
        }

        .results-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .stats {
            display: flex;
            gap: 15px;
            font-size: 0.9rem;
        }

        .stat-item {
            display: flex;
            align-items: center;
            gap: 5px;
            padding: 5px 10px;
            background: rgba(102, 126, 234, 0.1);
            border-radius: 15px;
            font-weight: 500;
        }

        .domain-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 10px;
        }

        .domain-table th,
        .domain-table td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #e2e8f0;
        }

        .domain-table th {
            background: #f7fafc;
            font-weight: 600;
            color: #4a5568;
            position: sticky;
            top: 0;
        }

        .domain-table tbody tr:hover {
            background: #f7fafc;
        }

        .status-free {
            color: #38a169;
            font-weight: 600;
        }

        .status-taken {
            color: #e53e3e;
            font-weight: 600;
        }

        .status-error {
            color: #ed8936;
            font-weight: 600;
        }

        .status-pending {
            color: #718096;
            font-style: italic;
        }

        .table-container {
            max-height: 400px;
            overflow-y: auto;
            border-radius: 10px;
            border: 1px solid #e2e8f0;
        }

        .action-btn {
            padding: 6px 12px;
            font-size: 12px;
            border-radius: 6px;
            border: none;
            cursor: pointer;
            margin: 0 2px;
        }

        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 20px;
            border-radius: 10px;
            color: white;
            font-weight: 500;
            z-index: 1000;
            transform: translateX(400px);
            transition: transform 0.3s ease;
        }

        .notification.show {
            transform: translateX(0);
        }

        .notification.success {
            background: linear-gradient(135deg, #48bb78 0%, #38a169 100%);
        }

        .notification.warning {
            background: linear-gradient(135deg, #ed8936 0%, #dd6b20 100%);
        }

        .notification.error {
            background: linear-gradient(135deg, #f56565 0%, #e53e3e 100%);
        }

        .demo-mode {
            background: rgba(255, 107, 107, 0.1);
            border: 2px dashed #ff6b6b;
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 20px;
            text-align: center;
        }

        .demo-mode h3 {
            color: #ff6b6b;
            margin-bottom: 10px;
        }

        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @media (max-width: 768px) {
            .main-content {
                grid-template-columns: 1fr;
                gap: 20px;
            }
            
            .control-grid {
                grid-template-columns: 1fr;
            }
            
            .header h1 {
                font-size: 2rem;
            }
            
            .container {
                padding: 15px;
            }
        }

        .footer {
            text-align: center;
            color: white;
            margin-top: 40px;
            opacity: 0.8;
        }

        .github-link {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            color: white;
            text-decoration: none;
            padding: 10px 20px;
            border-radius: 10px;
            background: rgba(255, 255, 255, 0.1);
            transition: all 0.3s ease;
            margin-top: 10px;
        }

        .github-link:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🌐 도메인 체커 Pro</h1>
            <p>Domain Availability Checker - 실시간 도메인 가용성 확인</p>
        </div>

        <div class="info-banner">
            ⚠️ 데모 모드: 실제 도메인 체크 대신 랜덤 결과를 표시합니다. 실제 사용을 위해서는 백엔드 API가 필요합니다.
        </div>

        <div class="main-content">
            <!-- 좌측 패널 - 입력 및 제어 -->
            <div class="left-panel">
                <!-- 도메인 입력 카드 -->
                <div class="card">
                    <div class="card-title">
                        🎯 도메인 추가
                    </div>
                    
                    <div class="input-section">
                        <div class="input-group">
                            <label for="domainInput">단일 도메인:</label>
                            <div class="input-row">
                                <input type="text" id="domainInput" placeholder="example.com" />
                                <button class="btn btn-primary" onclick="addDomain()">
                                    ➕ 추가
                                </button>
                            </div>
                        </div>
                        
                        <div class="input-group">
                            <label for="bulkInput">일괄 입력 (줄바꿈으로 구분):</label>
                            <textarea id="bulkInput" placeholder="domain1.com&#10;domain2.com&#10;domain3.com"></textarea>
                            <button class="btn btn-primary" onclick="addDomainsBulk()" style="margin-top: 10px; width: 100%;">
                                📋 일괄 추가
                            </button>
                        </div>
                    </div>
                </div>

                <!-- 제어 패널 카드 -->
                <div class="card">
                    <div class="card-title">
                        ⚡ 제어 패널
                    </div>
                    
                    <div class="control-grid">
                        <button class="btn btn-success" id="checkNowBtn" onclick="checkDomainsNow()">
                            🚀 지금 체크
                        </button>
                        <button class="btn btn-primary" id="autoCheckBtn" onclick="toggleAutoCheck()">
                            🔄 자동 체크 시작
                        </button>
                    </div>
                    
                    <div class="interval-control">
                        <label>체크 간격:</label>
                        <input type="number" id="checkInterval" value="10" min="5" max="60" />
                        <span>분</span>
                    </div>
                    
                    <button class="btn btn-danger" onclick="clearAllDomains()" style="width: 100%; margin-top: 15px;">
                        🗑️ 전체 삭제
                    </button>
                    
                    <div class="progress-container">
                        <div class="progress-bar">
                            <div class="progress-fill" id="progressFill"></div>
                        </div>
                    </div>
                    
                    <div class="status-display status-ready" id="statusDisplay">
                        🟢 준비 완료
                    </div>
                </div>

                <!-- 데모 모드 설명 -->
                <div class="card">
                    <div class="demo-mode">
                        <h3>🔧 개발자를 위한 안내</h3>
                        <p><strong>현재 데모 모드로 동작합니다.</strong></p>
                        <p>실제 WHOIS 조회를 위해서는:</p>
                        <ul style="text-align: left; margin-top: 10px;">
                            <li>• 백엔드 API 서버 구축</li>
                            <li>• WHOIS API 연동 (예: whoisjson.com)</li>
                            <li>• CORS 프록시 서버 설정</li>
                        </ul>
                    </div>
                </div>
            </div>

            <!-- 우측 패널 - 결과 표시 -->
            <div class="right-panel">
                <div class="card">
                    <div class="results-header">
                        <div class="card-title">
                            📊 도메인 목록 및 결과
                        </div>
                        <div class="stats" id="statsDisplay">
                            <div class="stat-item">총: 0개</div>
                            <div class="stat-item">🟢 Free: 0개</div>
                            <div class="stat-item">🔴 Taken: 0개</div>
                            <div class="stat-item">🟡 Error: 0개</div>
                        </div>
                    </div>
                    
                    <div class="table-container">
                        <table class="domain-table">
                            <thead>
                                <tr>
                                    <th>도메인</th>
                                    <th>상태</th>
                                    <th>마지막 체크</th>
                                    <th>액션</th>
                                </tr>
                            </thead>
                            <tbody id="domainTableBody">
                                <!-- 동적으로 생성됨 -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>

        <div class="footer">
            <p>© 2025 도메인 체커 Pro. Made with ❤️</p>
            <a href="https://github.com/your-username/domain-checker" class="github-link" target="_blank">
                <span>⭐</span>
                GitHub에서 보기
            </a>
        </div>
    </div>

    <script>
        // 애플리케이션 상태
        let domains = [];
        let domainResults = {};
        let autoCheckInterval = null;
        let isAutoChecking = false;

        // 초기 도메인 설정
        const initialDomains = [
            "VoyageNest.com", "GlobeTrek.com", "Triply.com", "Nomadify.com", "JourniStay.com",
            "SleepUp.com", "NestFlow.com", "Roomzy.com", "StayGo.com", "Lodgezy.com",
            "Flyture.com", "Wanderon.com", "Roamify.com", "Jetly.com", "MoveXplore.com",
            "Innovize.com", "TechNest.com", "LinkUp.com", "Syncly.com", "Netluxe.com",
            "Biteify.com", "Tastyfy.com", "Brewloop.com", "Grillza.com", "Chimezy.com",
            "Tappix.com", "Fliptrix.com", "Snapza.com"
        ];

        // 페이지 로드 시 초기화
        document.addEventListener('DOMContentLoaded', function() {
            // 로컬 스토리지에서 데이터 로드
            loadFromStorage();
            
            // 초기 도메인이 없으면 기본 도메인 설정
            if (domains.length === 0) {
                domains = [...initialDomains];
                saveToStorage();
            }
            
            updateDisplay();
            
            // Enter 키 이벤트
            document.getElementById('domainInput').addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    addDomain();
                }
            });
        });

        // 도메인 추가
        function addDomain() {
            const input = document.getElementById('domainInput');
            const domain = input.value.trim();
            
            if (domain && !domains.includes(domain)) {
                domains.push(domain);
                input.value = '';
                updateDisplay();
                saveToStorage();
                showNotification(`✅ ${domain}이(가) 추가되었습니다!`, 'success');
            } else if (domains.includes(domain)) {
                showNotification('⚠️ 이미 추가된 도메인입니다.', 'warning');
            }
        }

        // 일괄 도메인 추가
        function addDomainsBulk() {
            const input = document.getElementById('bulkInput');
            const text = input.value.trim();
            
            if (text) {
                const newDomains = text.split('\n')
                    .map(domain => domain.trim())
                    .filter(domain => domain && !domains.includes(domain));
                
                domains.push(...newDomains);
                input.value = '';
                updateDisplay();
                saveToStorage();
                showNotification(`✅ ${newDomains.length}개의 새로운 도메인이 추가되었습니다!`, 'success');
            }
        }

        // 단일 도메인 삭제
        function removeDomain(domain) {
            if (confirm(`'${domain}'을(를) 삭제하시겠습니까?`)) {
                domains = domains.filter(d => d !== domain);
                delete domainResults[domain];
                updateDisplay();
                saveToStorage();
                showNotification('✅ 도메인이 삭제되었습니다!', 'success');
            }
        }

        // 전체 도메인 삭제
        function clearAllDomains() {
            if (confirm('모든 도메인을 삭제하시겠습니까?')) {
                domains = [];
                domainResults = {};
                updateDisplay();
                saveToStorage();
                showNotification('✅ 모든 도메인이 삭제되었습니다!', 'success');
            }
        }

        // 단일 도메인 재체크
        function recheckDomain(domain) {
            checkSingleDomain(domain);
        }

        // 즉시 도메인 체크
        async function checkDomainsNow() {
            if (domains.length === 0) {
                showNotification('⚠️ 체크할 도메인이 없습니다.', 'warning');
                return;
            }

            const btn = document.getElementById('checkNowBtn');
            btn.disabled = true;
            
            await checkAllDomains();
            
            btn.disabled = false;
        }

        // 모든 도메인 체크
        async function checkAllDomains() {
            const total = domains.length;
            const progressFill = document.getElementById('progressFill');
            const statusDisplay = document.getElementById('statusDisplay');
            
            statusDisplay.className = 'status-display status-checking';
            
            for (let i = 0; i < domains.length; i++) {
                const domain = domains[i];
                statusDisplay.textContent = `🔍 체크 중: ${domain} (${i + 1}/${total})`;
                
                const result = await checkSingleDomainSync(domain);
                domainResults[domain] = {
                    status: result,
                    lastCheck: new Date().toLocaleTimeString()
                };
                
                // 진행률 업데이트
                const progress = ((i + 1) / total) * 100;
                progressFill.style.width = progress + '%';
                
                updateDisplay();
                
                // Rate limiting - 데모에서는 빠르게
                await new Promise(resolve => setTimeout(resolve, 500));
            }
            
            statusDisplay.className = 'status-display status-complete';
            statusDisplay.textContent = `✅ 완료: ${new Date().toLocaleString()}`;
            progressFill.style.width = '0%';
            saveToStorage();
        }

        // 단일 도메인 체크 (비동기)
        async function checkSingleDomain(domain) {
            const result = await checkSingleDomainSync(domain);
            domainResults[domain] = {
                status: result,
                lastCheck: new Date().toLocaleTimeString()
            };
            updateDisplay();
            saveToStorage();
        }

        // 단일 도메인 체크 (동기) - 데모 버전
        async function checkSingleDomainSync(domain) {
            // 데모 모드: 랜덤 결과 생성
            await new Promise(resolve => setTimeout(resolve, 300 + Math.random() * 700));
            
            // 현실적인 확률로 결과 생성
            const rand = Math.random();
            if (rand < 0.15) return 'Free';     // 15% 확률로 Free
            else if (rand < 0.8) return 'Taken'; // 65% 확률로 Taken
            else return 'Error';                 // 20% 확률로 Error
        }

        // 자동 체크 토글
        function toggleAutoCheck() {
            if (isAutoChecking) {
                stopAutoCheck();
            } else {
                startAutoCheck();
            }
        }

        // 자동 체크 시작
        function startAutoCheck() {
            if (domains.length === 0) {
                showNotification('⚠️ 체크할 도메인이 없습니다.', 'warning');
                return;
            }

            isAutoChecking = true;
            const btn = document.getElementById('autoCheckBtn');
            btn.textContent = '⏹️ 자동 체크 중지';
            btn.className = 'btn btn-warning';
            
            const interval = parseInt(document.getElementById('checkInterval').value) * 60000; // 분을 밀리초로
            
            autoCheckInterval = setInterval(async () => {
                await checkAllDomains();
            }, interval);
            
            showNotification('🔄 자동 체크가 시작되었습니다!', 'success');
        }

        // 자동 체크 중지
        function stopAutoCheck() {
            isAutoChecking = false;
            const btn = document.getElementById('autoCheckBtn');
            btn.textContent = '🔄 자동 체크 시작';
            btn.className = 'btn btn-primary';
            
            if (autoCheckInterval) {
                clearInterval(autoCheckInterval);
                autoCheckInterval = null;
            }
            
            showNotification('⏹️ 자동 체크가 중지되었습니다.', 'warning');
        }

        // 화면 업데이트
        function updateDisplay() {
            updateTable();
            updateStats();
        }

        // 테이블 업데이트
        function updateTable() {
            const tbody = document.getElementById('domainTableBody');
            tbody.innerHTML = '';
            
            domains.forEach(domain => {
                const row = document.createElement('tr');
                const result = domainResults[domain];
                
                let statusClass = 'status-pending';
                let statusText = '⏳ 대기중';
                let lastCheck = '-';
                
                if (result) {
                    lastCheck = result.lastCheck;
                    switch (result.status) {
                        case 'Free':
                            statusClass = 'status-free';
                            statusText = '🟢 Free';
                            break;
                        case 'Taken':
                            statusClass = 'status-taken';
                            statusText = '🔴 Taken';
                            break;
                        case 'Error':
                            statusClass = 'status-error';
                            statusText = '🟡 Error';
                            break;
                    }
                }
                
                row.innerHTML = `
                    <td>${domain}</td>
                    <td class="${statusClass}">${statusText}</td>
                    <td>${lastCheck}</td>
                    <td>
                        <button class="action-btn btn-primary" onclick="recheckDomain('${domain}')">🔄</button>
                        <button class="action-btn btn-danger" onclick="removeDomain('${domain}')">🗑️</button>
                    </td>
                `;
                
                tbody.appendChild(row);
            });
        }

        // 통계 업데이트
        function updateStats() {
            const total = domains.length;
            const free = Object.values(domainResults).filter(r => r.status === 'Free').length;
            const taken = Object.values(domainResults).filter(r => r.status === 'Taken').length;
            const error = Object.values(domainResults).filter(r => r.status === 'Error').length;
            
            document.getElementById('statsDisplay').innerHTML = `
                <div class="stat-item">총: ${total}개</div>
                <div class="stat-item">🟢 Free: ${free}개</div>
                <div class="stat-item">🔴 Taken: ${taken}개</div>
                <div class="stat-item">🟡 Error: ${error}개</div>
            `;
        }

        // 알림 표시
        function showNotification(message, type = 'success') {
            // 기존 알림 제거
            const existingNotification = document.querySelector('.notification');
            if (existingNotification) {
                existingNotification.remove();
            }
            
            const notification = document.createElement('div');
            notification.className = `notification ${type}`;
            notification.textContent = message;
            
            document.body.appendChild(notification);
            
            // 애니메이션으로 표시
            setTimeout(() => {
                notification.classList.add('show');
            }, 100);
            
            // 3초 후 제거
            setTimeout(() => {
                notification.classList.remove('show');
                setTimeout(() => {
                    notification.remove();
                }, 300);
            }, 3000);
        }

        // 로컬 스토리지에 저장
        function saveToStorage() {
            const data = {
                domains: domains,
                domainResults: domainResults,
                checkInterval: document.getElementById('checkInterval').value
            };
            localStorage.setItem('domainCheckerData', JSON.stringify(data));
        }

        // 로컬 스토리지에서 로드
        function loadFromStorage() {
            const saved = localStorage.getItem('domainCheckerData');
            if (saved) {
                try {
                    const data = JSON.parse(saved);
                    domains = data.domains || [];
                    domainResults = data.domainResults || {};
                    if (data.checkInterval) {
                        document.getElementById('checkInterval').value = data.checkInterval;
                    }
                } catch (error) {
                    console.error('Error loading from storage:', error);
                }
            }
        }

        // 페이지 언로드 시 자동 체크 중지
        window.addEventListener('beforeunload', function() {
            if (isAutoChecking) {
                stopAutoCheck();
            }
        });
    </script>
</body>
</html>
