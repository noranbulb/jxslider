﻿jxslider
-
피씨와 모바일에서 슬라이드 배너를 표현하기 위한 플러그인이며 제이쿼리를 `head 태그` 사이에 필수로 넣어야한다.
제이쿼리 버전에 버그 영향이 있지만  최상위 버전을 지양한다면 익스플로러 8에서도 작동이 가능한 플러그인이다.

https://jxslider.netlify.com/

#### html

 ``` sh
 <div class="jx-slider" id="jx-slider">

      <div class="jx-box">
            <div class="jx-wrap">
                  <div class="jx-unit"><div class="jx-cont"><span class="thumb"><img src="resources/imgs/img_1.jpg" alt=""></span></div></div>
                  <div class="jx-unit"><div class="jx-cont"><span class="thumb"><img src="resources/imgs/img_2.jpg" alt=""></span></div></div>
                  <div class="jx-unit"><div class="jx-cont"><span class="thumb"><img src="resources/imgs/img_3.jpg" alt=""></span></div></div>
            </div>
      </div>

      <div class="jx-control"> </div> <!-- 페이징을 생성 노드-->

      <button type="button" class="jx-btn jx-left">&lt; </button> <!-- 좌버튼 생성 노드 -->
      <button type="button" class="jx-btn jx-right">&gt; </button> <!-- 우버튼 생성 노드 -->

      <button type="button" class="jx-stop">stop</button> <!-- 정지 버튼 생성 노드 -->
</div>

````


#### javascript

```` sh
<head>
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-1.9.1.js"></script>
    <script src="https://code.jquery.com/jquery-migrate-1.2.1.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-easing/1.4.1/jquery.easing.js"></script>
    <script src="resources/js/jxslider-ver-x2.js"></script>
</head>

<body>

..기본 슬라이드 객체 생략..

<script>
      var option =
      {
            nView : 3
      };
      new JXSLIDER( $("#jx-slider") ,  option );
</script>

</body>

````


### option

Option | Type | Default | Description
------ | ---- | ------- | -----------
nView            |  number  |  1  | 화면에 몇개의 객체를 보여줄것인가
sDirection      |  string  |  horizontal  | 움직이는 방향 ( horizontal  or vertical )
nMargin         |  number  | 0 | 객체마다 간격 `margin-right 값이 적용`
nOnMargin     |  number  | 0 | jx-unit 중에 선택된(.on) 객체에만 margin-left 와 margin-right가 적용이 된다. `값이 50 이면 양쪽으로 값이 들어가서 총 값은 100이 된다. 이경우는 선택되어진 객체에 nMargin과 다른 값을 적용하고 싶을때 넣는것이고 nMargin값보다 작거나 값을 넣지 않을경우는 nMargin값이 적용된다.` `중요한 사실은 oEffect 영향을 끼쳐서 정확한 값을 찾기 어려우므로 왠만하면 nMargin값과 동일하거나 넣지 않아야 좋다. 만약 값을 넣었다면 bResize 값을 false를 넣고 css에서 효과를 주기를 권장한다`
nUlSpeed       |  number  |  400 | 움직이는 속도
bAuto           |  boolean  |  false  | 자동롤링
nAutoSpeed   |  number  |  3000  | 자동롤링 속도
bDrag         |  boolean  |  true  | 드래그 가능
bLoop           |  boolean  |  true  | 무한 반복
bResize         |  boolean  |  true  | 리사이징 `리사이징을 하지 않을경우 모바일에서 하나의 컨텐츠가 클경우 문제가 생길수도 있으며 oEffect 옵션에 영향도 끼친다. false을 넣게 되면 oEffect 효과 계산이 실시간 계산이 되지 않으므로 자연스러운 효과를 기대하기 어렵다. 그래서 css에 효과를 추가를 하고 oEffect 옵션을 넣지 않는것도 좋다.`
nSans           |  number  |  10  | 드래그 민감도
bGroupMove  |  boolean  |  false  | 이동을 nView에 값에 따라서 이동
bAction         |  boolean  |  false  | 객체를 클릭하면 칸 차이를 인식하여 이동  `링크가 있는경우에는 현제 활성화된=on 객체는 링크 연결이 되고 나머지는 움직이게 된다.`
nStart            |  number  |  0  | 몇번째 객체를 처음부터 보여줄려할때 사용. 1을 사용하면 앞에서 1개의 객체를 제일 뒤로 붙인다. `단. nView = 3, bGroupMove = true 일경우는 3개씩 페이징 이동하기 때문에 1이면 3개씩 단위로 뒤에 이동하여 붙게 된다. nBackCopy 옵션은 작동안하게 된다`
nBackCopy     |  number  |  0  | 뒤객체를 숫자만큼 앞으로 붙여서 센터 정렬처럼 유사하게 보일려 할때 사용. `부모의 사이즈나 위치는 조정해야함. nStart = 0 값을 가져야 함. bLoop = true 여야함.`
oResponsive     |  array  |  []  | 브라우저에 맞게 반응형을 하기 위함. `bGroupMove = true 라면 false로 변하게 된다.`
bAaptiveHeight |  boolean  |  false  | 활성화된 객체의 높이값에 맞춰서 슬라이드 높이를 조절한다. `nView = 1 일때 사용하는게 좋으나 아닐때는 좌우에 나타난 정보들을 숨겼다가 나타나게 css를 추가하는게 좋다.`
sEffectClass | string | 'jx-cont' | 어떤 객체에 효과를 적용할것인지 클래스 명을 지정해준다. `<div class="jx-unit"><div class="jx-cont"> 이렇게 안에 꼭 객체가 있어야하며 효과가 필요없을때는 jx-cont 가 없어도 된다.`
bEffBalnce | boolean | true | 센터 객체를 기준으로 양쪽 객체의 효과를 거리에 따라 변화준다(기본값: true). false값은 양쪽 객체들이 min값에 맞춰서 똑같이 적용.
oEffect | array | [] | 어떤 효과를 넣을것인지 배열로 넘겨준다. `ex : oEffect : [ {name : 'transform' , ef : [{name : 'rotateY', max : 0, min : 70 }, {name : 'scale', max : 1, min : .7 } ] } , {name : 'opacity', max : 1, min : 1.5 } ]` `transform 같은 경우는 배열로 다시 한번 감싸서 넘겨줘야 한다.`
reCallFnc |  string  |  -  | 슬라이드가 끝난후 외부에서 넘긴 함수를 실행시키는 방법 `외부에서 함수를 정의하고 속성에 스트링 타입으로 함수명을 적어주면 된다. ex ) {reCallFnc : testCall} 넘겨주고 function testCall(v) { console.log(v); } `




