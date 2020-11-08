## FLEX

-   레이아웃을 만들거나 아이템, 컨텐츠의 배치를 설정하기에 좋은 도구.
-   요새는 거의 flex를 사용한다.
-   FLEX는 container 속성과 item 속성으로 구성되어 있다.

![enter image description here](https://css-tricks.com/wp-content/uploads/2018/10/01-container.svg){: width="10" height="10"}

**<Container 속성>**




Container						     item


<Container 속성>

정의(display)
    .container{
        display:flex; /* or inline-flex */
    }

플렉스 컨테이너를 정의한다. 주어진 값에 따라 인라인 또는 블록으로 정의할 수 있다.

flex-direction






item이 container에 배치되는 방향을 정의한다.
가로, 세로로 배치된다.

    .container{
        flex-direction : row | row-reverse | column | column-reverse
    }

row(default) : 왼쪽에서 오른쪽으로 
row-reverse : 오른쪽에서 왼쪽으로
column : 위에서 아래로
column-reverse : 아래에서 위로
flex wrap

기본적으로 flex item 은 모두 한 줄에 맞추려고 한다.
		이 속성을 사용하여 항목을 wrapping 할 수 있다.
    .container{
        flex-wrap : nowrap | wrap | wrap-reverse;
    }

nowrap(default) : 모든 item들이 한 줄에 있다.
wrap : item 들은 위에서 아래로 여러 줄로 줄 바꿈
wrap-reverse : item들은 아래에서 위로 여러 줄로 wrapping 

flex-flow
flex-direction과 flex-wrap 을 한 번에 사용할 수 있는 약자.
기본 값은 row, no-wrap이다.
    .container{
        flex-flow : column wrap;
    }

justify-content
중심축에 따라 정렬을 한다.
item들의 여유 공간을 분산하는 데 도움이 된다.


















    .container{
        justify-content :flex-start,flex-end,center,space-around,space-between,space-evenly
    }

flex-start (default): 기본 설정으로, item은 container의 앞쪽에서부터 배치됩니다.
flex-end : item은 container의 뒤쪽에서부터 배치됩니다.
center : item은 container의 가운데에서부터 배치됩니다.
space-between : item은 요소들 사이에만 여유 공간을 두고 배치됩니다.
space-around : item는 앞, 뒤, 그리고 요소들 사이에도 모두 여유 공간을 두고 배치됩니다
space-evenly : item 사이의 간격과 가장 자리 공간까지 같도록 분산

align item 
현재 라인의 교차축을 따라 item이 배치되는 방식을 정의
flex-direction이 row값이면 세로지만 column이면 가로




















    .container{
        align-items: stretch | flex-start | flex-end | center |baseline
        }

stretch : 기본 설정으로, item의 높이가 container의 높이와 같게 변경된 뒤 연이어 배치
 flex-start : item는 container의 위쪽에 배치
 flex-end : item는 container의 아래쪽에 배치
 center : item는 container의 가운데에 배치
baseline : item는 container의 기준선(baseline)에 배치
align content 
교차 축(cross-axis)의 정렬 방법을 설정
주의할 점은 flex-wrap 속성을 통해 Items가 여러 줄(2줄 이상)이고 여백이 있을 경우만 사용할 수 있다.

stretch(default) : Container의 교차 축을 채우기 위해 Items를 늘림
flex-start : Items를 시작점(flex-start)으로 정렬	
flex-end : Items를 끝점(flex-end)으로 정렬	
center : Items를 가운데 정렬	
space-between : 시작 Item은 시작점에, 마지막 Item은 끝점에 정렬되고 나머지 Items는 사이에 고르게 정렬됨	
space-around : Items를 균등한 여백을 포함하여 정렬















<Item 속성>

order
기본적으로 item들은 소스 순서대로 배치되지만
order 속성을 사용하여 순서를 제어할 수 있다.
default값 :0

    .item {
        order : 5;
    }

flex-grow 
item의 크기를 비율로 설정함
1로 설정된 경우 균등하게 item의 크기가 지정되지만 만약 특정 item에 flex-grow 를 2로 준다면 다른 item에 비해 2배 커진다.

    .item {
        flex-grow : 2;
    }

flex-shrink
Item이 감소하는 너비의 비율을 설정합니다.
숫자가 크면 더 많은 너비가 감소합니다.
Item이 가변 너비가 아니거나, 값이 0일 경우 효과가 없습니다.
    .item {
        flex-shrink : 2;
    }

flex-basis
Item의 (공간 배분 전) 기본 너비를 설정합니다.
값이 auto일 경우 width, height 등의 속성으로 Item의 너비를 설정할 수 있습니다.
하지만 단위 값이 주어질 경우 설정할 수 없습니다.
auto : 가변 Item과 같은 너비	auto
단위 : px, em, cm 등 단위로 지정
    .item {
        flex-basis : auto;
    }

flex 
Item의 너비(증가, 감소, 기본)를 설정하는 단축 속성입니다.
flex: 증가너비 감소너비 기본너비;
.item {
    flex: 1 1 20px;  /* 증가너비 감소너비 기본너비 */
    flex: 1 1;  /* 증가너비 감소너비 */
    flex: 1 20px;  /* 증가너비 기본너비 (단위를 사용하면 flex-basis가 적용됩니다) */
  }

align-self 
교차축에서 개별 item의 정렬 방법을 설정한다. 
필요에 의해 특정 item만 정렬 방법을 변경하려고 할 경우 사용한다.
align-items 속성보다 우선순위가 높다.

auto(default) : Container의 align-items 속성을 상속받음
stretch : Container의 교차 축을 채우기 위해 Item을 늘림	
flex-start : Item을 각 줄의 시작점(flex-start)으로 정렬	
flex-end : Item을 각 줄의 끝점(flex-end)으로 정렬	
center : Item을 가운데 정렬	
baseline : Item을 문자 기준선에 정렬
