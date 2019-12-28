[help 페이지] float 에러
====
# float erro
![float으로 인한 에러](img/help_slide_error.PNG)
```
.purpleStrokeTitle {
    float:right;
    top:4%;
    left:0;
    margin-right: 6%; 
    color:#fff;
    font:3.0rem 'robotR';
    z-index:1;
}
```
# float & margin-top
![그에 따른 해결 방법 feat margin-top](img/marginTop_float_width.PNG)
```
.help_page .sliderInner {
    float:left;
    width:100%;
    margin-top:36px;
}
```

# 최종해결
![최종해결](img/help_fix.PNG)
```
.purpleStrokeTitle {
    float 삭제
    left:auto;
    right:4%;
}

-전제삭제-
.help_page .sliderInner {
    float:left;
    width:100%;
    margin-top:36px;
}
```

.purpleStrokeTitle가 absolute 인데 after 덕분에 가능했던거 같다.
slick을 사용할때 부분은 건들지 말고 슬라이더 이미지가 들어가는 부분에 height 만 넣으면 잘 작동한다.