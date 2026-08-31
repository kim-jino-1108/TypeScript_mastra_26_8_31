# step1.ts 실행 세팅 가이드 (초보자용)

이 문서는 `4_mastra` 폴더에서 `step1.ts` 파일 하나를 실행하기 위한 준비 과정을
아주 쉽게 정리한 것입니다. 순서대로 따라 하면 됩니다.

---

## 0. step1.ts는 무엇을 하나요?

- Mastra(타입스크립트용 AI 에이전트 프레임워크)로 **에이전트 객체 1개를 만들기만** 합니다.
- 모델을 실제로 호출하지 않습니다. 그냥 만들고 이름만 출력합니다.
- 성공하면 터미널에 아래 한 줄이 뜹니다.

  ```
  Created agent: Assistant
  ```

---

## 1. 준비물 (한 번만 설치)

### 1-1. Node.js 24 버전

- 이 코드는 Node에 내장된 기능을 쓰기 때문에 **Node 24 LTS** 가 필요합니다.
- 설치 여부/버전 확인:

  ```bash
  node --version
  ```

- `v24.x.x` 처럼 나오면 OK. 없거나 낮으면 https://nodejs.org 에서 24 LTS 설치.

### 1-2. 작업 폴더 이동

터미널(PowerShell)을 열고 **이 폴더 안**으로 이동합니다. 아래 명령은 모두 이 폴더에서 실행합니다.

```bash
cd C:\Users\jino7\Desktop\2026_Ai_Python-Source\TypeScript_mastra_26_8_31\4_mastra
```

### 1-3. 패키지 설치

이 폴더에서 한 번만 실행하면 `node_modules` 폴더가 만들어집니다.

```bash
npm install
```

> 참고: 지금 이 폴더에는 이미 `node_modules` 가 있어서 설치가 끝난 상태입니다.
> 새로 받은 경우에만 실행하면 됩니다.

---

## 2. API 키 설정 (.env 파일)

- 모델 호출용 키 `OPENAI_API_KEY` 가 필요합니다.
- 위치는 이 폴더가 아니라 **저장소 최상위 폴더의 `.env` 파일** 입니다.
  프로그램이 상위 폴더로 올라가면서 가장 가까운 `.env` 를 자동으로 찾습니다.

  ```
  C:\Users\jino7\Desktop\2026_Ai_Python-Source\.env
  ```

- `.env` 파일 안에 아래 형식으로 한 줄 있으면 됩니다.

  ```
  OPENAI_API_KEY=sk-여기에-본인-키
  ```

> 참고: `step1.ts` 는 모델을 실제로 부르지 않으므로 키가 비어 있어도 "Created agent" 는 출력됩니다.
> 하지만 step2 이후를 위해 지금 넣어두는 게 좋습니다. (현재 이 저장소 `.env` 에는 키가 이미 설정되어 있습니다.)

---

## 3. 실행

이 폴더에서:

```bash
npm run step1
```

- 이 명령은 내부적으로 `tsx step1.ts` 를 실행하는 것과 같습니다.
  (`tsx` = 타입스크립트를 컴파일 없이 바로 실행해 주는 도구, 이미 설치됨)

### 성공 화면

```
> mastra-worker@1.0.0 step1
> node --disable-warning=ExperimentalWarning --import tsx step1.ts

Created agent: Assistant
```

`Created agent: Assistant` 가 보이면 세팅 성공입니다.

---

## 4. 자주 나는 오류와 해결

| 증상 | 원인 | 해결 |
| --- | --- | --- |
| `'npm' 은(는) ... 인식되지 않습니다` | Node.js 미설치 | Node 24 LTS 설치 후 터미널 재시작 |
| `Cannot find module '@mastra/core/agent'` | 패키지 미설치 | 이 폴더에서 `npm install` |
| `Cannot find package 'tsx'` | 개발 도구 미설치 | 이 폴더에서 `npm install` |
| SQLite / ExperimentalWarning 관련 경고 | Node 버전이 낮음 | Node 24 LTS로 업그레이드 |
| step2부터 인증 오류(401 등) | API 키 없음/오타 | 저장소 최상위 `.env` 의 `OPENAI_API_KEY` 확인 |

---

## 5. 한눈에 보는 요약

```bash
# 1) 폴더 이동
cd C:\Users\jino7\Desktop\2026_Ai_Python-Source\TypeScript_mastra_26_8_31\4_mastra

# 2) (처음 한 번) 패키지 설치
npm install

# 3) 실행
npm run step1
```

기대 출력: `Created agent: Assistant`
