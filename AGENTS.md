# AGENTS.md

## Project Identity

```yaml
platform: web
```

### 프로젝트 요약

- **이름**: wiki-import-test
- **목적**: 공통 위키 import·부트스트랩 흐름 검증용 테스트 프로젝트
- **스택**: HTML, CSS (정적 파일만 — `index.html`, `style.css` 등)
- **제약**: Next.js, React, 번들러, 패키지 매니저를 설치·도입하지 않는다

---

## Wiki Baseline

### 위키 부트스트랩 (작업 시작 전 필수)

공통 위키는 이 프로젝트 안에 두지 않는다. 홈 디렉터리 아래 `.llm-wiki` 한 곳에서만 관리한다.

1. 먼저 홈 절대경로를 구한다. 셸 종류에 맞게:
   - bash / zsh / Git Bash / WSL: `echo "$HOME"`
   - PowerShell: `echo $HOME`
   - cmd: `echo %USERPROFILE%`

   구한 값을 `HOME_DIR`로 삼고, 위키 루트 = `HOME_DIR` + `/.llm-wiki` 로 정한다.

2. 위키 루트에 `wiki/index.md`가 없으면 머신당 1회 clone한다:
   `git clone https://github.com/jeong-hoi-seok/llm-wiki.git "<위키 루트>"`
   이미 있으면 최신화한다:
   `git -C "<위키 루트>" pull --ff-only`

3. clone/pull이 실패하면(네트워크·권한) 사실을 말하고 중단한다.

### 읽기 순서

> 아래 파일을 반드시 직접 열어서 읽는다. 경로만 인지하는 것으로 갈음하지 않는다.

1. 부트스트랩 1단계에서 구한 절대경로로 `<위키 루트>/wiki/index.md`를 직접 연다.
   (`$HOME`·`~`를 그대로 읽기 도구에 넘기지 말고, 푼 절대경로를 쓴다.)

2. 위 `platform` 값에 맞는 문서만 추가로 읽는다:

| 위키 태그 | `web` | `app` |
|---|---|---|
| `[공통]` | ✅ | ✅ |
| `[웹]` | ✅ | ❌ |
| `[앱]` | ❌ | ✅ |
| `[웹·앱]` | ✅ | ✅ |

### 응답 규칙 (검증용)

작업 결과물 하단에 참고한 위키 문서를 반드시 명시한다:

```
<!-- wiki-ref: 컨벤션/커밋 컨벤션.md, 개발원칙/가독성.md -->
```

명시하지 않은 경우, 위키를 읽지 않은 것으로 간주한다.
