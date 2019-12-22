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
    