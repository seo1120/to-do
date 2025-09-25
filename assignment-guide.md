# Week 2 과제: Todo 리스트 앱 만들기

## 🎯 과제 개요

Week 2에서 배운 **HTML, CSS, Tailwind, JavaScript**를 종합하여 실용적인 Todo 리스트 앱을 만드는 과제입니다.

### 📅 제출 기한
- **마감**: Week2 금요일 6PM PDT 까지 

### 🎁 과제의 목적
1. **Week 2 복습**: 배운 내용을 실제 프로젝트에 적용
2. **Week 3 준비**: JavaScript DOM 조작 실력 향상
3. **실무 스킬**: CRUD 패턴과 데이터 저장 경험

---

## 📋 필수 요구사항 (모든 학생)

### ✅ 1. 할일 추가 (Create)
```javascript
// 구현해야 할 기능
- 입력창에 할일 내용 입력
- "추가" 버튼 클릭으로 목록에 추가
- Enter 키로도 추가 가능
- 빈 값 입력 방지 (유효성 검사)
```

### ✅ 2. 할일 삭제 (Delete)
```javascript
// 구현해야 할 기능
- 각 할일마다 "삭제" 버튼
- 클릭시 해당 할일 제거
- 삭제 확인 대화상자 (선택사항)
```

### ✅ 3. 완료 상태 토글 (Update)
```javascript
// 구현해야 할 기능
- 체크박스로 완료/미완료 상태 변경
- 완료된 항목은 시각적으로 구분 (취소선, 색상 변경 등)
- 상태 변경시 즉시 화면 업데이트
```

### ✅ 4. 데이터 저장 (LocalStorage)
```javascript
// 구현해야 할 기능
- 모든 할일 데이터를 브라우저에 저장
- 페이지 새로고침 후에도 데이터 유지
- JSON 형태로 저장/불러오기
```

---

## 🎨 디자인 요구사항

### 🎯 Tailwind CSS 활용 (필수)
- **색상 시스템**: `bg-blue-500`, `text-gray-700` 등 Tailwind 클래스 사용
- **레이아웃**: `flex`, `grid`, `space-y-4` 등으로 깔끔한 배치
- **반응형**: `md:`, `lg:` 접두어로 모바일 대응
- **호버 효과**: `hover:bg-blue-600` 등으로 인터랙션 강화

### 🖼️ 기본 디자인 가이드
```html
<!-- 권장 구조 -->
<div class="max-w-2xl mx-auto p-6">
  <!-- 헤더 -->
  <header class="text-center mb-8">
    <h1 class="text-4xl font-bold text-blue-600">Todo 리스트</h1>
  </header>

  <!-- 입력 영역 -->
  <div class="bg-white rounded-lg shadow-md p-6 mb-6">
    <!-- 입력 폼 -->
  </div>

  <!-- 목록 영역 -->
  <div class="bg-white rounded-lg shadow-md p-6">
    <!-- Todo 항목들 -->
  </div>
</div>
```

---

## 🛠 기술적 요구사항

### 📁 파일 구조
```
your-project/
├── index.html          # 메인 HTML 파일
└── README.md           # 프로젝트 설명 (선택사항)
```

### 💻 사용 기술
- **HTML5**: 시맨틱 태그 사용 권장
- **Tailwind CSS**: CDN 방식으로 스타일링
- **Vanilla JavaScript**: 외부 라이브러리 사용 금지
- **LocalStorage**: 데이터 저장

### 🔧 필수 JavaScript 기능
```javascript
// 반드시 구현해야 할 함수들
function addTodo()      // 할일 추가
function deleteTodo()   // 할일 삭제
function toggleTodo()   // 완료 상태 토글
function loadTodos()    // LocalStorage에서 불러오기
function saveTodos()    // LocalStorage에 저장하기
function renderTodos()  // 화면에 목록 표시
```

---

## 🌟 선택 과제 (도전하고 싶은 학생)

### 🟡 중급 기능
- [ ] **전체 삭제 버튼**: 모든 할일을 한 번에 삭제
- [ ] **완료된 항목 삭제**: 완료된 항목만 선별 삭제
- [ ] **할일 수정 기능**: 기존 할일 내용 편집
- [ ] **통계 표시**: 전체/완료/남은 할일 개수 표시

### 🔴 고급 기능
- [ ] **우선순위**: 높음/보통/낮음 설정
- [ ] **카테고리**: 업무/개인/쇼핑 등 분류
- [ ] **필터링**: 전체/진행중/완료 항목 필터
- [ ] **정렬**: 생성순/가나다순/우선순위순
- [ ] **진행률 바**: 완료 비율을 시각적으로 표시

---

## 📚 개발 가이드

### 🚀 시작하기
1. `todo-starter.html` 파일 다운로드
2. 브라우저에서 열어서 구조 확인
3. JavaScript 함수들을 하나씩 완성
4. 개발자 도구(F12)로 디버깅

### 💡 개발 팁

#### 1단계: 기본 구조 이해
```javascript
// 전역 변수로 할일 목록 관리
let todos = [];

// 할일 객체 구조
const todo = {
    id: Date.now(),           // 고유 ID
    text: "할일 내용",        // 할일 텍스트
    completed: false,         // 완료 여부
    createdAt: new Date()     // 생성 시간
};
```

#### 2단계: DOM 조작 마스터
```javascript
// 요소 선택
const input = document.getElementById('todoInput');
const list = document.getElementById('todoList');

// 값 가져오기/설정하기
const text = input.value;
input.value = '';

// HTML 생성
list.innerHTML = '<div>새로운 내용</div>';
```

#### 3단계: LocalStorage 활용
```javascript
// 저장
localStorage.setItem('todos', JSON.stringify(todos));

// 불러오기
const savedTodos = localStorage.getItem('todos');
if (savedTodos) {
    todos = JSON.parse(savedTodos);
}
```

#### 4단계: 이벤트 처리
```javascript
// 클릭 이벤트
<button onclick="addTodo()">추가</button>

// 키보드 이벤트
input.addEventListener('keypress', function(e) {
    if (e.key === 'Enter') {
        addTodo();
    }
});
```

### 🐛 자주 발생하는 오류

#### 1. "Cannot read property of null"
```javascript
// 문제: 요소를 찾지 못함
const input = document.getElementById('wrongId'); // null

// 해결: ID 확인
const input = document.getElementById('todoInput'); // 올바른 ID
```

#### 2. LocalStorage 데이터 손실
```javascript
// 문제: JSON 변환 실패
localStorage.setItem('todos', todos); // [object Object]

// 해결: JSON.stringify 사용
localStorage.setItem('todos', JSON.stringify(todos));
```

#### 3. 화면 업데이트 안 됨
```javascript
// 문제: 배열 수정 후 화면 업데이트 안 함
todos.push(newTodo);

// 해결: renderTodos() 호출
todos.push(newTodo);
renderTodos(); // 화면 다시 그리기
```

---

## 📝 제출 방법

### 1. GitHub 저장소 생성
1. GitHub에서 새 저장소 생성
2. 저장소명: `week2-todo-assignment` (권장)
3. Public으로 설정

### 2. 파일 업로드
1. 완성된 HTML 파일 업로드
2. README.md 파일 작성 (선택사항)

### 3. GitHub Pages 배포
1. Settings → Pages 탭
2. Source: Deploy from a branch
3. Branch: main
4. 배포 URL 확인

### 4. 제출 양식
```
이름: 홍길동
Week 2 Todo 과제 제출

GitHub 저장소: https://github.com/username/week2-todo-assignment
배포 URL: https://username.github.io/week2-todo-assignment
구현 기능: ✅ 추가 ✅ 삭제 ✅ 완료토글 ✅ 저장 🟡 통계표시
```

---

## 🆘 도움 받기

### 💬 질문 방법
1. **먼저 시도**: 에러 메시지 확인, console.log() 활용
2. **동료 도움**: 같은 과제를 하는 친구들과 토론
3. **강사 질문**: 구체적인 에러 상황과 시도한 방법 설명

### 🔍 참고 자료
- **MDN Web Docs**: JavaScript 문법 확인
- **Tailwind CSS 공식 문서**: 클래스명 찾기
- **Week 2 수업 자료**: html_tailwind_comparison.html 등

### 🚫 주의사항
- **직접 코딩**: AI 도구나 완성된 코드 복사 금지
- **이해 중심**: 작동하더라도 이해하지 못한 코드는 지양
- **단계별 완성**: 한 번에 모든 기능을 구현하려 하지 말 것

---

*Week 2 Todo 과제 가이드 - Global PBL Fall 2025*