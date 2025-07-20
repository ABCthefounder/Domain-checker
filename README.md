# 🌐 도메인 체커 Pro

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live%20Demo-brightgreen?style=flat-square)](https://your-username.github.io/domain-checker-pro/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://opensource.org/licenses/MIT)
[![Web App](https://img.shields.io/badge/Web%20App-Progressive-blue?style=flat-square)](https://your-username.github.io/domain-checker-pro/)

실시간 도메인 가용성 확인을 위한 현대적인 웹 애플리케이션입니다.

## ✨ 주요 기능

- 🔍 **실시간 도메인 체크**: 도메인 등록 가능 여부를 즉시 확인
- 🔄 **자동 모니터링**: 설정한 간격으로 자동 체크 (5-60분)
- 📊 **시각적 대시보드**: 직관적인 결과 표시와 통계
- 💾 **로컬 저장**: 브라우저에서 도메인 목록 자동 저장
- 📱 **반응형 디자인**: 모든 디바이스에서 완벽한 사용성
- 🎨 **현대적 UI**: 글래스모피즘과 부드러운 애니메이션

## 🚀 라이브 데모

**[👆 여기를 클릭해서 바로 사용해보세요!](https://your-username.github.io/domain-checker-pro/)**

## 📸 스크린샷

![Domain Checker Pro Screenshot](screenshots/demo.png)

## 🎯 사용 방법

### 1. 도메인 추가
- **단일 추가**: 입력창에 도메인 입력 후 "추가" 버튼 클릭
- **일괄 추가**: 여러 도메인을 줄바꿈으로 구분하여 입력

### 2. 도메인 체크
- **즉시 체크**: "지금 체크" 버튼으로 수동 실행
- **자동 체크**: "자동 체크 시작"으로 주기적 모니터링

### 3. 결과 확인
- 🟢 **Free**: 등록 가능한 도메인
- 🔴 **Taken**: 이미 등록된 도메인  
- 🟡 **Error**: 체크 중 오류 발생

## 🛠 기술 스택

- **Frontend**: HTML5, CSS3, JavaScript (Vanilla)
- **Styling**: CSS Grid, Flexbox, CSS Variables
- **Features**: Local Storage, Fetch API, Async/Await
- **Design**: Glassmorphism, Gradient Backgrounds
- **Hosting**: GitHub Pages

## 📦 로컬 실행

```bash
# 1. 리포지토리 클론
git clone https://github.com/your-username/domain-checker-pro.git

# 2. 폴더 이동
cd domain-checker-pro

# 3. 웹 서버 실행 (Python 예시)
python -m http.server 8000

# 4. 브라우저에서 접속
# http://localhost:8000
```

## 🔧 커스터마이징

### 색상 테마 변경
```css
/* CSS 파일에서 색상 변수 수정 */
:root {
  --primary-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  --success-color: #48bb78;
  --warning-color: #ed8936;
  --error-color: #f56565;
}
```

### 체크 간격 기본값 변경
```javascript
// JavaScript에서 기본값 수정
document.getElementById('checkInterval').value = "15"; // 15분으로 변경
```

## 🤝 기여하기

1. 이 리포지토리를 Fork
2. 새 브랜치 생성 (`git checkout -b feature/amazing-feature`)
3. 변경사항 커밋 (`git commit -m 'Add some amazing feature'`)
4. 브랜치에 Push (`git push origin feature/amazing-feature`)
5. Pull Request 생성

## 📋 할 일 목록

- [ ] 백엔드 API 연동으로 실제 WHOIS 조회
- [ ] 도메인 히스토리 트래킹
- [ ] 이메일 알림 기능
- [ ] 다크/라이트 테마 토글
- [ ] 데이터 내보내기 (CSV, JSON)
- [ ] PWA 지원

## 📄 라이선스

이 프로젝트는 MIT 라이선스 하에 배포됩니다. 자세한 내용은 [LICENSE](LICENSE) 파일을 참조하세요.

## 👨‍💻 개발자

**Your Name**
- GitHub: [@your-username](https://github.com/your-username)
- 이메일: your.email@example.com

## ⭐ 지원하기

이 프로젝트가 도움이 되었다면 ⭐ 스타를 눌러주세요!

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/your-username">Your Name</a>
</p>