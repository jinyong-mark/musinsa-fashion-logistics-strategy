# Edge 텔레그램 연동 - 패션물류 서비스 전략 프로젝트

## 1. Edge에 저장소 주소 등록

**파일:** `/Users/mark/Edge_project/.env` 또는 `config.json`

```
# GitHub 저장소 모니터링
PROJECT_REPOS={
  "패션물류서비스": {
    "url": "https://github.com/[YOUR_USERNAME]/musinsa-fashion-logistics-strategy",
    "branch": "main",
    "polling_interval": 3600  # 1시간마다 확인
  }
}

# 텔레그램 봇 설정 (기존 유지)
TELEGRAM_BOT_TOKEN=xxxxx
TELEGRAM_USER_ID=xxxxx
```

## 2. Edge 트리거 설정

마크님이 원하는 알림 패턴:

```
# 매일 08:00 당발 분석 상태 브리핑
DAILY_BRIEFING_TIME=08:00
BRIEFING_PROJECTS=["패션물류서비스"]

# GitHub 저장소 변경 감지
ON_GITHUB_UPDATE={
  "action": "notify",
  "target": "telegram",
  "message": "📊 패션물류 서비스 전략 - {file} 업데이트됨"
}
```

## 3. 텔레그램 명령어

Edge 텔레그램 봇(@Edge_EA_bot)에서:

```
/project fashion-logistics     # 프로젝트 상태 조회
/status                        # 현재 분석 진행상황
/update                        # 최신 분석 내용 받기
/remind 18:00                  # 매일 18시 리마인더
/subscribe                     # 모든 업데이트 구독
```

## 4. Slack 연동 (선택)

마크님의 Slack DM에서도 같은 명령어 사용 가능:
- Slack: musinsa.slack.com
- 채널: @Edge_EA_bot (DM)

---

## 현재 상태

✅ 분석 보고서 작성 완료
📦 GitHub 저장소 대기 (옵션 A/B 선택 필요)
⏳ Edge 설정 (저장소 URL 확정 후)
📱 Telegram 연동 (자동)

---

**다음 순서:**
1. GitHub 저장소 생성 (옵션 선택)
2. Edge config 수정 (저장소 URL 입력)
3. Edge 재시작 (`python3 /Users/mark/Edge_project/edge.py`)
4. 텔레그램에서 `/project fashion-logistics` 테스트

