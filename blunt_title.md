[ blunt 표현 방법 ] 
=====
###  h2태그title과 보라색 stroke 표현방법.
* HTML
    ```
    <h2 class="purpleStrokeTitle">collabo</h2>
    ```
* CSS
    ```
    .purpleStrokeTitle {
        position:relative;
        top:0;
        left:0;
        color:#fff;
        font:3.0rem 'robotR';
        z-index:1;
    }

    .purpleStrokeTitle:after {
        content:"";
        display:block;
        position:absolute;
        top:50%;
        right:50%;
        width:110%;
        height:12px;
        transform:translate(50%,-6px);
        background:rgba(135,72,238,.7);
        z-index:-1;
    }

    ```
.purpleStrokeTitle으로 통일 시키기 전에는 각 페이지마다 보라색 선의 width값,top과 left 값을 각 분기별로 px값으로 계속해서 변경해줬다. width 값을 준 이유는 h2태그에 들어가는 글자수가 다 달라서..멍청이짓을 정성들여서 했음. 위 코드로 변경한 후 나름 깔끔해진 것 같아 한결 뿌듯했다.