# 주차 연락처 QR

차 앞유리에 전화번호를 그대로 붙여두는 게 불편해서 만들었습니다.
번호 대신 QR을 붙여두고, 스캔하면 전화·문자 버튼이 있는 페이지가 열립니다.

**배포 주소** : https://weenybeeny03.github.io/parking-qr/QR.html

## 화면

| 생성기 | 스캔 후 화면 |
|---|---|
| <img width="300" alt="생성기 화면" src="https://github.com/user-attachments/assets/4f8b9c1e-1dda-494c-b22b-3f2960f5ef1f" /> | <img width="200" alt="스캔 후 화면" src="https://github.com/user-attachments/assets/08f31f60-cbd9-4283-b62b-06f1d1e6f663" /> |

## 동작 방식

```
번호·동호수 입력
      ↓
park.html?phone=...&unit=... 주소를 만들어 QR로 변환
      ↓
스캔 → 해당 주소 열림 → 전화 / 문자 버튼
```

QR에 `tel:` 을 직접 넣으면 번호가 QR 안에 고정되어 버립니다.
대신 페이지 주소를 넣어, 화면 쪽에서 번호를 받아 처리하도록 분리했습니다.

## 사용 기술

HTML / CSS / Vanilla JS / qrcode.js / GitHub Pages

## 구현하면서 정리한 것

- 입력값이 바뀔 때마다 QR을 다시 그려야 해서, 기존 QR을 지우고(`clear`) 새로 그리는(`makeCode`) 처리를 직접 넣었습니다.
- 두 입력칸이 같은 동작을 공유하므로 `render` 함수로 분리했습니다.
- 페이지 간 값 전달은 쿼리스트링을 사용했고, 한글이 포함되어 `encodeURIComponent` 로 인코딩했습니다.

## 남은 과제

현재는 전화번호가 URL에 그대로 노출됩니다.
번호를 완전히 가리려면 QR에는 식별자만 넣고, 번호는 서버에 저장해 연결하는 구조가 필요합니다.
