# 我的note笔记

#### 1、移动端1px处理
```css\n
  .scale-1px{
    position: relative;
    border:none;
  }
  .scale-1px:after{
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

