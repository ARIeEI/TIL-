[blunt] pallax js function __ feat. 🦝
======
# stupid 🐢
처음에는 each를 못 써서, 코드가 거칠고 인정사정 없었다. 야생본연의 모습이였음.
```
//parallax
var th = $(this);
var par1 = $('.cont1');
var par2 = $('.cont2');
var par3 = $('.cont3');
var par4 = $('.cont4');
var par5 = $('.cont5');
var par6 = $('.cont6');
var par7 = $('.cont7');
var par8 = $('.cont8');
var par9 = $('.cont9');
var par10 = $('.cont10');
var par11 = $('.cont11');
var par12 = $('.cont12');
var par13 = $('.cont13');
var par14 = $('.cont14');

$(window).scroll(function(){
    var th = $(this);
    starAniM2(th,par1,'AniR');
    starAniM2(th,par2,'AniR');
    starAniM2(th,par3,'AniD');
    starAniM2(th,par4,'AniR');
    starAniM2(th,par5,'AniD');
    starAniM2(th,par6,'AniD');
    starAniM2(th,par7,'AniR');
    starAniM2(th,par8,'AniD');
    starAniM2(th,par9,'big');
    starAniM2(th,par10,'big');
    starAniM2(th,par11,'AniD');
    starAniM2(th,par12,'AniD');
    starAniM2(th,par13,'AniD');
    starAniM2(th,par14,'AniD');
});

if($(window).width() >= 768){
    $(window).scroll(function(){
     var th = $(this);
    starAni2(th,par1,'AniR');
    starAni2(th,par2,'AniR');
    starAni2(th,par3,'AniD');
    starAni2(th,par4,'AniR');
    starAni2(th,par5,'AniD');
    starAni2(th,par6,'AniD');
    starAni2(th,par7,'AniR');
    starAni2(th,par8,'AniD');
    starAni2(th,par9,'big');
    starAni2(th,par10,'big');
    starAni2(th,par11,'AniD');
    starAni2(th,par12,'AniD');
    starAni2(th,par13,'AniD');
    starAni2(th,par14,'AniD');
    });
}
        //mobile
function starAniM2(th,vv,mm){
    if(th.scrollTop() > vv.offset().top-780){
            vv.addClass(mm);
    }else{
            vv.removeClass(mm);
    }
}
        //pc
function starAni2(th,vv,mm){
    if(th.scrollTop() > vv.offset().top-1290){
            vv.addClass(mm);
    }else{
            vv.removeClass(mm);
    }
}...
to be continued 였음..
```
# 🦝each
## 🦝님의 가르침으로 each를 사용해서 많이 다듬어진 코드
```
var anir = $('.anir✨');
anir.each(function(){
    var anirContent = $(this);

    $(window).scroll(function(){
    if ($(window).scrollTop() > anirContent.offset().top - window.innerHeight) {
            anirContent.addClass('AniR✨');
            } else {
                    anirContent.removeClass('AniR✨');
            }
    });
});

// var anir,var anid,var aniu 각각 3개로 each로 만들었음.
```
# function
## ✨빼고 똑같은 위 코드를 함수 하나로 리펙토링..!
```
function scrollAnimation ( selector, active ){
    var thisSelector = $(selector);

    thisSelector.each(function(index, item){
        var selectorChildren = thisSelector👿.children(); // [element, element]
        //변수를 이렇게 잡으면 해당( $(selector)) 모든 설렉터의 자식들을 그냥 다 불러오는 방식.
        //이 함수에 맞지 않음.

        console.log('selectorChildren', selectorChildren);  //selectorChildren 선택한거 확인중.
        console.log('item', $(item).children());            // $(item).children() 선택한거 확인중.

        $(window).scroll(function(){
            if($(window).scrollTop() > $(this👿).offset().top - window.innerHeight){
                $(this👿).addClass(active);
            } else {
                $(this👿).removeClass(active);
            }
                //$(item) 대신 $(this)를 사용하면 $(window)잡아버림.
        });
    });
}
```
## 오류 수정(👿), $(item)과 $(window)도 변수로 만들어줌. (리펙토링)
> 코드길이의 변화는 없지만, 수정에 용이하고에 용이하고, $()이렇게 되어 있으면 컴터가 그 만큼 작동하고 용량?이 커지기 때문에, 변수로 만들어 주어 컴퓨터의 일을 줄여줌.
//내부 설렉터 변수 $ 를 앞에 붙임.
// 이름도 상황에 타당하게 
```
function scrollAnimation ( selector, active ){
    var thisSelector = $(selector);
    thisSelector.each(function(index, item){
        var $window = $(window);
        var $item = $(item);
        var $itemChildren = $item.children();
        // var $itemChildren = $item.children;
        $window.scroll(function(){
            if($window.scrollTop() > $item.offset().top - window.innerHeight){
                $itemChildren.addClass(active);
            } else {
                $itemChildren.removeClass(active);
            }
        });
    });
}

scrollAnimation ('.aniu', 'AniU');
scrollAnimation ('.anid', 'AniD');
scrollAnimation ('.anir', 'AniR');
```

○ 처음부터 함수로 만들어서 쓰려고 했다면 멘붕 먼저 왔을 같다. 길더라도 하나하나 만들어서 작동시켜, 오류를 잡고, 그 코드로 다시 리펙토링 하는 과정을 반복 하다 보니, 하나의 함수로 만들 수 있었다.
시작부터 100이 아니라 1을 생각하면서 코드를 짜는게 좋을 것 같다.