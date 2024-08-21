- Markup Language: 태그 등을 이용하여 문서나 데이터의 구조를 명시하는 언어
- <head></head> : HTML 문서에 관련된 설명, 설정 등 컴퓨터가 식별하는 메타데이터를 작성. / 사용자에게 보이지 않음
## CSS 적용 방법
1. 인라인 스타일
2. 내부 스타일 시트
3. 외부 스타일 시트

## CSS Selectors 종류
- 기본 선택자 : 전체(*) 선택자 / 요소(tag) 선택자 / 클래스(class) / 아이디(id) 선택자 / 속성(attr) 선택자 등
- 결합자 (Combinators) : 자손 결합자(" " (space)) / 자식 결합자(">")

- 요소 선택자: 지정한 모든 태그를 선택
- 클래스 선택자(.(dot)): 주어진 클래스 속성을 가진 모든 요소를 선택
- 아이디 선택자('#'): 주어진 아이디 속성을 가진 요소 선택 / 문서에는 주어진 아이디를 가진 요소가 하나만 있어야 함

- 자손 결합자(" "(space)) : 첫 번째 요소의 자손 요소들 선택 / 예)p span은 <p> 안에 있는 모든 <span>를 선택 (하위 레벨 상관없이)
- 자식 결합자(">"): 첫 번째 요소의 직계 자식만 선택 / 예) ul > li은 <ul>안에 있는 모든 <li>를 선택 (한단계 아래 자식들만)

## Specificity (명시도)
- 명시도가 높은 순
  1. !important
  2. Inline 스타일
  3. 선택자 : (높음) id선택자 > class 선택자 > 요소 선택자 (낮음)
  4. 소스 코드 선언 순서

## CSS Box Model
- 박스 타입
1. Block box
2. Inline box
- 박스 표시(Display)타입
1. Outer display type
   - 박스가 문서 흐름에서 어떻게 동작할지를 결정
   - 속성: block, inline
    ### block 특징
    - 항상 새로운 행으로 나뉨
    - width와 height 속성 사용 가능
    - padding, margin, border로 인해 다른 요소를 상자로부터 밀어냄
    - width 속성을 지정하지 않으면 박스는 inline 방향으로 사용 가능한 공간을 모두 차지함
    - 대표적인 block타입 태그: h1~6, p, div
2. Inner display type
   ### inline 특징
   - 속성: flex
   - 새로운 행으로 넘어가지 않음
   - width와 height속성을 사용할 수 없음
   - 수직 방향: padding, margins, borders가 적용되어 다른 요소를 밀어낼 수 있음
   - 대표적인 inline 타입 태그: a, img, span, strong, em





