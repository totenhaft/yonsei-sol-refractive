# 연세솔안과 시력교정술 적합성 검사 시스템

## 🏥 소개

연세솔안과에서 사용하는 시력교정술 적합성 검사 웹 애플리케이션입니다.
LASIK, LASEK/PRK, SMILE 수술의 적합성을 자동으로 평가하고, AI 기반 각막 지형도 분석 기능을 제공합니다.

## ✨ 주요 기능

### 1. 양안(OD/OS) 개별 입력 시스템
- 환자 기본 정보 (이름, 등록번호, 나이, 성별)
- 굴절 검사 (SPH, CYL, AXIS, SE 자동 계산)
- 각막 검사 (CCT, K1, K2, Steep Axis)
- Topography 패턴 선택
- 수술 파라미터 (광학부, Flap/Epi/Cap 두께)

### 2. 자동 계산
- **Munnerlyn's Formula** 기반 절삭량 계산
- **RSB** (Residual Stromal Bed) 계산
- **PTA** (Percent Tissue Altered) 계산
- **수술 후 예상 K값** 계산

### 3. 위험도 평가
- **Randleman ERSS** (Ectasia Risk Score System)
- **PTA 기반 위험도**
- **ERSS + PTA 복합 위험도 매트릭스**

### 4. AI 각막 지형도 분석 🤖
- Galilei G4, Pentacam, Orbscan 데이터 파싱
- BAD-D, I-S value, KISA%, 후면 융기 등 자동 분석
- 원추각막 의심 소견 자동 분류

### 5. Wellington Nomogram 권장
- 연령, 굴절력 기반 교정값 권장

### 6. 관리자 기능
- 🔐 로그인/로그아웃
- 🔍 환자 검색
- 💾 환자 데이터 저장/불러오기

## 🚀 배포 방법

### GitHub Pages 배포

1. 이 저장소를 Fork 합니다.
2. Settings > Pages에서 Source를 "main branch"로 설정합니다.
3. `https://[username].github.io/yonsei-sol-refractive/`에서 접근 가능합니다.

### Firebase 연동 (선택)

Firebase를 연동하면 여러 사용자가 환자 데이터를 공유할 수 있습니다.

1. [Firebase Console](https://console.firebase.google.com)에서 새 프로젝트 생성
2. Authentication > Sign-in method에서 이메일/비밀번호 활성화
3. Firestore Database 생성
4. 프로젝트 설정 > 웹 앱 추가 후 설정값 복사
5. `index.html`의 `DEMO_MODE`를 `false`로 변경하고 Firebase SDK 추가

### Firestore 보안 규칙

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /patients/{patientId} {
      allow read, write: if request.auth != null;
    }
  }
}
```

## 📁 파일 구조

```
yonsei-sol-refractive/
├── index.html          # 메인 애플리케이션 (이름을 yonsei-sol-refractive.html에서 변경)
├── logo.jpg            # 연세솔안과 로고
└── README.md           # 이 파일
```

## 💻 사용 방법

1. 환자 정보 입력 (이름, 등록번호, 나이, 성별)
2. 양안 굴절 및 각막 검사 데이터 입력
3. (선택) AI 분석을 위해 Topography 데이터 붙여넣기
4. "양안 계산하기" 버튼 클릭
5. 결과 확인 및 저장

## ⚠️ 주의사항

- 본 프로그램은 **참고용**이며, 최종 수술 결정은 반드시 **전문의와 상담**하세요.
- AI 분석 결과는 보조적 정보이며, 임상적 판단을 대체하지 않습니다.
- 환자 데이터는 HIPAA/개인정보보호법에 따라 적절히 관리하세요.

## 📚 참고 문헌

- Randleman JB, et al. Risk factors and prognosis for corneal ectasia after LASIK. Ophthalmology. 2008
- Santhiago MR, et al. Role of percent tissue altered on ectasia after LASIK. J Refract Surg. 2016
- Chan C, et al. Comparison of SCORE, ERSS, PTA for ectasia. Ophthalmology. 2018
- Belin MW, Ambrósio R. Scheimpflug imaging for keratoconus and ectatic disease. Indian J Ophthalmol. 2013

---

© 2024 연세솔안과 YONSEI SOL EYE CLINIC. All rights reserved.
