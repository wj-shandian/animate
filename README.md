# animate
### 前言
偶然间看到一些官网的文字的动画效果，滚动页面，文字滑出，感觉效果很好看，于是就想看一下是怎么实现的，发现是用css3属性实现的

于是就有了这个练习demo

主要是想看一下实现的过程

主要的css代码如下
```
.bounceInLeft {
        -webkit-animation-name: bounceInLeft;
        animation-name: bounceInLeft;
        margin-left: 100px;
        width: 100px;
        -webkit-animation-duration: 1s;
        animation-duration: 1s;
        /* -webkit-animation-fill-mode: both; */
        /* animation-fill-mode: both; */
    }

    @keyframes bounceInLeft {

        from,
        60%,
        75%,
        90%,
        to {
            -webkit-animation-timing-function: cubic-bezier(0.215, 0.61, 0.355, 1);
            animation-timing-function: cubic-bezier(0.215, 0.61, 0.355, 1);
        }

        0% {
            opacity: 0;
            -webkit-transform: translate3d(-3000px, 0, 0);
            transform: translate3d(-3000px, 0, 0);
        }

        60% {
            opacity: 1;
            -webkit-transform: translate3d(25px, 0, 0);
            transform: translate3d(25px, 0, 0);
        }

        75% {
            -webkit-transform: translate3d(-10px, 0, 0);
            transform: translate3d(-10px, 0, 0);
        }

        90% {
            -webkit-transform: translate3d(5px, 0, 0);
            transform: translate3d(5px, 0, 0);
        }

        to {
            -webkit-transform: translate3d(0, 0, 0);
            transform: translate3d(0, 0, 0);
        }
    }

    @-webkit-keyframes bounceInLeft {

        from,
        60%,
        75%,
        90%,
        to {
            -webkit-animation-timing-function: cubic-bezier(0.215, 0.61, 0.355, 1);
            animation-timing-function: cubic-bezier(0.215, 0.61, 0.355, 1);
        }

        0% {
            opacity: 0;
            -webkit-transform: translate3d(-3000px, 0, 0);
            transform: translate3d(-3000px, 0, 0);
        }

        60% {
            opacity: 1;
            -webkit-transform: translate3d(25px, 0, 0);
            transform: translate3d(25px, 0, 0);
        }

        75% {
            -webkit-transform: translate3d(-10px, 0, 0);
            transform: translate3d(-10px, 0, 0);
        }

        90% {
            -webkit-transform: translate3d(5px, 0, 0);
            transform: translate3d(5px, 0, 0);
        }

        to {
            -webkit-transform: translate3d(0, 0, 0);
            transform: translate3d(0, 0, 0);
        }
    }
    ```
    当然要是你自己不想写，还有一个animate的动画库https://daneden.github.io/animate.css/

    有很多动画效果可以使用，只要引用css文件，并添加相应的class名字就可以了

    官网的一些动画效果，我发现是滚动到位置时才会触发动画，这个时候就需要我们监听滚动事件，来添加class

    代码如下
    ```
    window.addEventListener('scroll', function () {
        var div = document.getElementById('div2');
        var top = div.getBoundingClientRect().top;
        var show = document.documentElement.clientHeight;
        if ((top + 10) < show) {
            div.className = "bounceInLeft"
        }
    }, true);
    ```
    这样加载到可视窗口，就会有相应的动画效果。