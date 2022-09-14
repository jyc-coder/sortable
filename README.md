# sortable

music-player 에서 플레이리스트 항목을 drag&drop으로 정렬하는 기능을 부여하기 위해 제작된 컴포넌트


# 기능 
- drag & drop 으로 항목을 이동시켜 정렬하는 기능
- 해당 항목을 클릭하면 항목의 위치(인덱스)값을 `alert`한다.


# 사용 기술 
- react
- react-dom
- react-scripts


# 테스트 화면 

![ezgif com-gif-maker (38)](https://user-images.githubusercontent.com/56331400/190108419-c8f09ef8-ddbc-4aab-8a39-dcdb47ca1f5c.gif)


# 구조

## App
`SortbleList`를 렌더링한다. (props : data,renderItem,onDropItem,onClickItem)
  - data : 리스트 항목에 들어가는 데이터. 내용과 인덱스가 들어간다.
  - renderItem : data를 바탕으로 렌더링되는 항목의 디자인. 이때의 데이터는 data를 참고한다. 
  - onDropItem : drag & drop을 하면 콘솔창에 리스트를 출력한다
  - onClickItem : 항목을 클릭하면 항목의 index값이 출력된다.
  
## SortableList 
`data`의 수만큼 반복하여 `SortableListItem`을 렌더링한다. 이때 맨 아래 항목에는 비어있는 `SortableListItem`을 만들어서 나중에 항목을 맨 아래로 옮길 때
실선을 보여주며 사용자가 끝을 구분할 수 있게 한다. (props: key,index,draggable,onDropItem,onDroItem,onDragStart,onClickItem)
  - key,index : index값을 가진다.
  - draggable : boolean 값으로 기본값은 true, draggable의 값에 따라 드래그할 수 있는지 없는지가 결정됨
  - onDropItem : drag & drop으로 정렬된 리스트를 리턴한다 (onDrop)
  
## SortableListItem 
`renderItem`의 데이터를 li의 형태로 렌더링한다.(props : draggable, onDragStart, onDragEnd, onDragEnter, onDragLeave ,onDragOver ,onDrop ,onClick)
  - onDrageStart : 드래그를 시작하는 순간 해당 항목의 클래스에 `dragstart`를 추가해서 투명하게 표시한다.
  - onDragEnd : 드래그가 끝나는 순간 `dragstart`를 제거한다.
  - onDragEnter : 드래그를 하는중에서 다른항목을 지나칠때 `dragover`클래스를 추가해서 상부에 녹색 선이 표시되게 한다. 
  - onDragLeave : 드래그를 하는 항목이 지나가면 `dragover`클래스가 사라지면서 선이 사라진다.
  - onDragOver : 드롭을 허용하기 위해 기본 동작 취소 (새로운 탭이 나타나는 이벤트같은 일련의 기본 이벤트를 막기위함)
  - onDrop : `SortableList`에서 정의한 onDropItem의 onDrop 메소트를 그대로 보내준다. 
  - onClick : `onClickItem`을 그대로 보내준다. (alert로 인덱스 표시)
  
