##### 박스 모델

4 개의 영역(component)으로 이루어져 있다: content, padding, border, margin

* `content`
  * 글이나 이미지 등 요소의 실제 내용이 포함된 영역
  * width, height 로 조절 가능, 단위로는 px, em, % 가 있다.
    * inline 요소로는 `span`, `a` , `img` 요소가 있는데,  `span` 과 `a` 등 inline 요소는 width 와 height 값을 지정해도 실제로 실제 layout 에는 적용이 되지 않는다. 
    * 멀티미디어를 나타내는 `img` 요소는 width 와 height 가 적용된다.
* `padding`
  * 안쪽 여백, border 와 content 사이의 영역
  * padding top, padding right, padding bottom, padding left 영역
  * 배경 색, 배경 이미지가 적용되는 박스의 내부 영역
* `border`
  * padding 과 margin 사이의 영역, 상하좌우 조정 가능
  * 아무 속성도 적용하지 않으면 기본적으로 아무 스타일도 적용되지 않는다.
  * style 값, width 값, color 값



보통 어떤 상자의 크기(width, height)를 말할 때, content 값만 해당되고 padding 과 border 는 해당되지 않는다. `box-sizing: border-box;` 를 적용하면 padding 과 border 도 적용이 된다.



* `margin`
  * 요소 바깥여백 경계
  * 다른 요소 두 개가 서로 맞닿아 margin 끼리 닿을 때
    * margin 통합(상쇄): 맞닿아 있는 margin끼리는 더 큰 값을 두 요소의 여백으로 정한다.



inline 속성은 width 값이 적용되지 않는다. inline 속성을 갖고 width 값을 적용시키고 싶다면 `display: inline-block;` 을 적용하면 가능하다.



##### normal flow 벗어나 복잡한 방식의 레이아웃을 배치하는 방법



* `float` 
  * 값으로는 right, left 가 있다.
  * `clear` 속성으로 해제 가능 : right, left, both 



* `position`
  * 기본 값은 static: `position: static;`
  * `position: relative;` 
    * top, bottom, right, left 값이 있다.
    * 전체 문서의 layout 흐름은 전혀 변하지 않는다.
  * `position: absolute;`
    * 새로운 layout 흐름이 생긴다.
    * 원래 자신의 자리가 없어진다.
    * position 값이 static 이 아닌 부모요소를 기준으로 위치
  * `position: fixed;`
    * 스크롤이 생겨도 화면의 지정한 위치에서 움직이지 않는다.
    * 브라우저 창을 기준으로 위치가 선정



##### 선택자 selector

`특정 html 요소를 선택해서 style 을 적용할 수 있도록 한다. `



* `class-selector`
* `tag-selector`
  * 자주 사용하는 것은 유지 보수에 좋지 않다.
  * 우선순위가 제일 낮다.
* `id-selector`
  * 중복 불가능, class 보다 우선순위가 높아 덮어 씌어진다.
* `가상 요소`
  * 존재하지 않는 요소를 존재하는 것 처럼 부여, 문서 특정 부분을 선택한다.
  * layout 영역에서 드래그로 선택이 되지 않는다.



`구체성 우선순위는 어떻게 될까?`

​	`id 선택자`의 구체성 값: 100점

​	`class 선택자` 및 `가상 클래스`의 구체성 값: 10점

​	`태그 선택자` 및 `가상요소`의 구체성 값: 1점

이 값들의 합이 무엇이 더 큰 값인지로 비교하여 우선순위 결정 가능



##### cascading

`style 겹치는 부분을 잘 봐야한다. 상황별 적용해야하는 style 이 전부 다르다. 이것을 cascading 이라고 하는데 이러한 방법들은 합리적인 원칙이다.` 