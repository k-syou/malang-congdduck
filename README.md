# 말랑콩떡 App

Flutter로 개발된 커플 캘린더 앱입니다.

## 자동 배포 설정

이 프로젝트는 GitHub Actions와 Firebase App Distribution을 사용하여 자동 배포가 설정되어 있습니다.

### 설정 단계

1. **Firebase 프로젝트 생성**
   - [Firebase Console](https://console.firebase.google.com/)에서 새 프로젝트 생성
   - Android와 iOS 앱 등록

2. **GitHub Secrets 설정**
   - `FIREBASE_APP_ID_ANDROID`: Android 앱의 Firebase App ID
   - `FIREBASE_APP_ID_IOS`: iOS 앱의 Firebase App ID
   - `FIREBASE_SERVICE_ACCOUNT_ANDROID`: Android용 서비스 계정 JSON
   - `FIREBASE_SERVICE_ACCOUNT_IOS`: iOS용 서비스 계정 JSON

3. **Firebase 설정 파일 업데이트**
   - `firebase.json`에서 앱 ID 업데이트
   - `.firebaserc`에서 프로젝트 ID 업데이트

### 자동 배포 프로세스

- `master` 또는 `main` 브랜치에 푸시할 때마다 자동으로 빌드
- Android APK와 iOS IPA 파일이 자동으로 Firebase App Distribution에 업로드
- 테스터 그룹에 자동으로 배포

### 수동 배포

```bash
# Firebase CLI 설치
npm install -g firebase-tools

# 로그인
firebase login

# 앱 배포
firebase appdistribution:distribute "build/app/outputs/flutter-apk/app-release.apk" \
  --app $FIREBASE_APP_ID_ANDROID \
  --groups testers \
  --release-notes "새로운 버전"
```

## 개발 환경

- Flutter 3.16.0+
- Dart 3.0.0+
- Android Studio / Xcode
