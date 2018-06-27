# 我的note笔记

#### 1、移动端1px处理
```css\n
  .box{
    position: relative;
    border:none;
  }
  .box:after{
    content: '';
    position: absolute;
    bottom: 0;
    background: #000;
    width: 100%;
    height: 1px;
    -webkit-transform: scaleY(0.5);
    transform: scaleY(0.5);
    -webkit-transform-origin: 0 0;
    transform-origin: 0 0;
  }
  //四条边
  .box{
      position: relative;
      margin-bottom: 20px;
      border:none;
  }
  .box:after{
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      border: 1px solid #000;
      -webkit-box-sizing: border-box;
      box-sizing: border-box;
      width: 200%;
      height: 200%;
      -webkit-transform: scale(0.5);
      transform: scale(0.5);
      -webkit-transform-origin: left top;
      transform-origin: left top;
  }
 ```
