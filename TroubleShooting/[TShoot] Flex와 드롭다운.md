# Flex와 드롭다운
  ## 적게 된 이유
  과제를 위해 헤더와 드롭다운을 만들어야 하는 일이 있었다.

  ![](https://media.discordapp.net/attachments/1089767490537656340/1150130211883585546/image-1.png?width=720&height=118)
  원래는 이런 드롭다운을 만드는 것이 원래 목적이였다.  
  하지만 제작해보니 **뭔가 잘못된 드롭다운**이 나왔다
  
  ![](https://media.discordapp.net/attachments/1089767490537656340/1150130212164599849/image-2.png?width=720&height=79)
  **~~?~~**

  ## 발생하는 원인
  이유는 단순하다. **FlexBox의 align-items 속성 때문이다.**  
  보통 `align-items: center`라고 작성하면 아이템들이 **수직으로 중앙정렬**된다.  
  <img src="https://css-tricks.com/wp-content/uploads/2019/10/flex-align.svg" width="250">  
  (이해를 돕기 위한 예)
  
  그런데 이 정렬이 드롭다운 리스트까지 적용되어 이상하게 뜨게 된다.

  ## 해결 방법
  아직까지 완벽한 해결 방법은 찾지 못했으나, 임시 해결 방법은 알아냈다.  
  속성에 `position: absolute(relative, fixed도 가능)`를 추가하면 해결된다.
  
  이 속성을 적용하면, 원리까진 모르겠으나 두 항목이 서로 분리되어 아래와 같이 출력된다. 
  ![](https://media.discordapp.net/attachments/1089767490537656340/1150130211883585546/image-1.png?width=720&height=118)

  아마 Position의 위치 설정과 Flex의 정렬 설정이 합쳐져 다음 줄로 정렬되는 것은 아닐까 싶다.

  ## 코드
  ```
  const Dropdown = Styled.div`
    padding: 10px;
    border-radius: 15px;
    box-sizing: border-box;
    font-size: 20px;
    font-family: "satoshi";
    cursor: pointer;
    & > div { // 드롭다운 리스트 (호버하지 않았을 시 숨긴다)
      gap: 10px;
      display: none;
      flex-direction: column;
      padding: 10px;
      margin-top: 10px;
      margin-left: -13px;
      position: absolute; // *해당 항목을 추가하여 문제를 해결하였다.*
      border-radius: 15px;
      box-sizing: border-box;
    }
    &:hover {
      font-weight: 500;
      & > div { //드롭다운 리스트 (호버시 띄운다)
        display : flex;
        transition: 0.2s;
        background: rgba(0, 0, 0, 0.1);*/
        font-weight: 400;
        & > span {
          padding: 10px;
          transition: 0.2s;
          border-radius: 10px;
          &:hover {
            transition: 0.2s;
            background: rgba(0, 0, 0, 0.1);
          }
        }
      }
    }
  `
  ```