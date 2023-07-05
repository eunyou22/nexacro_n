# [투비소프트] Nexacro N 컴포넌트 개발 간단 예제

### 사원정보 프로그램 만들기
![empProgram](/images/empProgram.PNG)
<br>

## 1. DataSet & Binding
![dataset1](/images/dataset1.PNG)
- **Dataset**
  - 데이터를 테이블 형태로 관리하는 오브젝트
  - 내부에서 사용하는 데이터로 컴포넌트와 바인딩하여 사용
  - 서버와의 통신시 데이터를 주고받는 형식으로 사용
  - 데이터가 수정, 삭제되면 변경 전 내용을 Origin Buffer에 저장
  - 입력방식
    - Dataset Editor에서 컬럼과 레코드 직접 입력
    - Dataset Editor 하단 [Source] 탭 선택 후 XML 형식으로 입력
- **DB와 바인딩 구조**
  - ![dataset2](/images/dataset2.PNG)
- **Data Binding**
  - 컴포넌트에 나타내고 싶은 데이터셋 연결
  - 데이터 컴포넌트와 표현 컴포넌트를 스크립트 코딩 없이 연결하여 데이터 입출력, 컴포넌트 동작 가능
  - 데이터 바인딩 방법
    1. Dataset 생성 <br>
        ![dataset4](/images/dataset4.PNG)
    2. 바인딩하고 싶은 컴포넌트에 해당 Dataset을 드래그 <br>
        ![dataset3](/images/dataset3.PNG)
<br><br>




## 2. Component Properties
- 컴포넌트에 속성을 지정하고 싶다면 `Properties` 탭에서 수정 가능 <br>
![properties](/images/properties.PNG)
    - Grid Expr <br>
      - 그리드에 텍스트 대신 표현식 값을 나타내도록 지정할 수 있음
        - 바인딩 값과 expr이 둘 다 있는 경우 expr이 우선순위
      - 종류
        - 사칙연산 `EMPL_ID + FULL_NAME` 
        - 예약어 `currow`
        - 메서드 
          - 그리드에 바인딩된 데이터셋 값에 접근 `dataset.getSum("SALARY")`
          - 그리드를 기준으로 Form의 데이터셋에 접근 `comp.parent.ds_emp.getSum("SALARY")`
        - 내부함수 `nexacro.round(12.8745,2)`
        - 함수호출 `comp.parent.fn_name()`
        - 변수 참조 `comp.parent.var1[this.로 정의된 변수명]`
        - 삼항연산 `GENDER == "M" ? "남자" : "여자"`
    ![gridExpr](/images/gridExpr.PNG) <br>
    - Tip!
      - 찾고 싶은 속성명 필터링 검색 가능 <br>
        ![filtering](/images/filtering.PNG) <br>
      - 속성명 선택 > F1키 누르면 설명 볼 수 있음 <br>
        ![f1](/images/f1.PNG)
- **Event 추가**
  - 특정 이벤트 발생 시 실행할 함수를 추가 할 수 있음 <br>
    ![addEvent1](/images/addEvent1.PNG)
  - **함수명 생성방식**
    - 사용자 지정 함수명: 원하는 함수명 입력 후 엔터키
    - 기본 함수명: 이벤트 오른쪽 빈 영역 더블클릭 시 "컴포넌트아이디_이벤트명" 형식으로 자동생성<br>
  - 샘플
      ```
      this.Button00_onclick = function(obj:nexacro.Button,e:nexacro.ClickEventInfo) {
          this.alert("Hello World!");
      };
      ```
<br><br>



## 3. 실행
- **Generate**
  - 넥사크로는 작성된 소스코드를 바로 실행하지 않고 자바스크립트 코드로 변환(=generate)하는 과정이 필요함. 
  - Generate는 Form을 생성, 수정 후 저장하는 시점에 자동으로 처리
    - Generate Path 확인 : `[Menu] Tools > Options > Project > Generate > Generate Path`
  - 이 경로에 생성한 파일을 실행
- **Quick View**
  - Generate된 파일을 실행하여 결과 확인 (단축키: `Ctrl + F6`)
    ![quickview](/images/quickview.PNG) <br>
    ![run](/images/run.PNG) <br>




<br><br><br>
<br><br><br>


