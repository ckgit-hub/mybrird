<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        * {
            padding: 0;
            margin: 0;
            /* 新盒模型 Width = width (padding+border) 不用内减 */
            box-sizing: border-box;
           
        }
        /* box 旋转 */
        .box {
            position: relative;
            width: 200px;
            height: 200px;
            margin: 50px auto 0;
            /* perspective: 800px; */
            /* 所以变形执行完都会回到最初状态  我们想保留3d效果 +属性
           transform-style: flat 2d平面(默认值) / perserve-3d(保留3d效果)
             */
            transform-style:preserve-3d;

            /* transform:rotate3d(1,1,0,-45deg);   为了观察*/
            animation: rotate 2s  0s ease-in infinite alternate;
            

        }
       .box  .side {
           position: absolute;
           left: 0;
           top: 0;
           width: 200px;
           height: 200px;
           border:2px solid #333;
           line-height: 200px;
           text-align: center;
           font-size: 20px;
           color: #222;
           transition: transform 1s;



        }
        /* 前面向z轴的正方向 100px +100px */
        .front {
            transform:translateZ(100px);

        }
        .back {
            transform:translateZ(-100px)  rotateY(180deg);

        }
        .left {
            transform:translateX(-100px)   rotateY(-90deg) ;
          
        }
        .right {
            transform:translateX(100px)   rotateY(90deg) ;

        }
        .top {
            transform:translateY(-100px)   rotateX(90deg) ;

        }
        .bottom {
            transform:translateY(100px)   rotateX(-90deg) ;
        }
        /* .box:hover .side {
            transform:translateZ(200px);  旋转的度数不进行保留
        } */
        .box:hover .front {
            transform:translateZ(200px);

        }
        .box:hover .back {
            transform: rotateY(180deg) translateZ(200px);

        }
        .box:hover .left {
            transform: rotateY(-90deg) translateZ(200px);

        }
        .box:hover .right {
            transform:rotateY(90deg) translateZ(200px);

        }
        .box:hover .top {
            transform: rotateX(90deg)  translateZ(200px);

        }
        .box:hover .bottom {
            transform: rotateX(-90deg)  translateZ(200px);

        }
        @keyframes rotate {
            0% {
                transform: rotateX(0deg) rotateY(0deg);

            }
            100% {
                transform:rotateX(360deg) rotateY(360deg);


            }
        }
     
     
    </style>
</head>
<body>
    <div class="box">
        <div class="side top">top</div>
        <div class="side bottom">bottom</div>
        <div class="side left">left</div>
        <div class="side right">right</div>
        <div class="side front">front</div>
        <div class="side back">back</div>
    </div>
</body>
</html>
