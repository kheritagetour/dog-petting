# 쓰담쓰담 멍멍 (Pat Pat Puppy)

- 한국어: https://kheritagetour.github.io/dog-petting/
- English: https://kheritagetour.github.io/dog-petting/en/

진흙투성이 강아지를 거품, 샤워기, 수건으로 씻기고 손과 효자손으로 쓰다듬는 3D 웹 놀이입니다. Three.js로 만들었습니다.

## 사용한 에셋

- 손 모델: [WebXR Input Profiles](https://github.com/immersive-web/webxr-input-profiles)의 `generic-hand` (MIT License, Copyright (c) 2019 Amazon)
- 지도: [Leaflet](https://leafletjs.com) (BSD-2-Clause), 지도 데이터 © [OpenStreetMap](https://www.openstreetmap.org/copyright) 기여자

## Google 로그인 켜기

`index.html`(과 `en/index.html`)의 `const FIREBASE_CONFIG=null;`을 Firebase 웹 앱 설정 객체로 바꾸면 Google 로그인과 클라우드 저장이 켜집니다. Firebase 콘솔에서 Authentication → Google 로그인, 승인된 도메인에 `kheritagetour.github.io` 추가, Firestore 데이터베이스 생성이 필요합니다. Firestore 규칙 예시:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{db}/documents {
    match /users/{uid} {
      allow read, write: if request.auth != null && request.auth.uid == uid;
    }
  }
}
```
