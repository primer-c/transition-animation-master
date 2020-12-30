#### 1. 居中对齐

1. 绝对定位实现居中对齐

- 对需要居中对齐的元素绝对定位
- 利用transform变换,减去移动元素自身宽高一半；

  ```css
  ul {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%,-50%);
  }
  ```

2. flex弹性布局实现居中对齐

- 对需要移动的元素父元素设置宽高；
- 对父元素弹性布局；
- 主轴和交叉轴居中对齐

  ```css
  body {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  ```

3. grid布局实现居中对齐

- 同flex

  ```css
  body {
    min-height: 100vh;
    display: grid;
    justify-content: center;
    align-items: center;
  }
  ```

#### 2. skew()倾斜

- 利用元素的:before和:after伪元素

  ```css
  ul li:before {
    content: "";
    width: inherit;
    height: 10px;
  }
  ul li:after {
    content: "";
    width: 10px;
    height: inherit;
  }
  ```
- 利用绝对定位,调节位置

  ```css
  ul li:before {
    content: "";
    width: inherit;
    height: 10px;
    position: absolute;
    bottom: -10px;
    left: 0;
    background: #f00;
  }
  ul li:after {
    content: "";
    width: 10px;
    height: inherit;
    position: absolute;
    top: 0;
    left: -10px;
    background: #f00;
  }
  ```

- 对:befoer向下弯折

- 对:after向右弯折

  ```css
  ul li:before {
    transform-origin: top; 
    transform: skewX(-45deg);
  }
  ul li:after {
    transform-origin: right;
    transform: skewY(-45deg);
  }
  ```

#### 3. 字体图标的使用

1. 下载
1. 多版本下载
 - [[下载地址]](https://github.com/FortAwesome/Font-Awesome.git)
 - [[下载地址]](https://fontawesome.com/how-to-use/on-the-web/setup/hosting-font-awesome-yourself)

2. Git克隆
   ```bash
   git clone https://github.com/FortAwesome/Font-Awesome.git
   ```
   
3. 使用
 1.  css方法引入
 ```html
 <!DOCTYPE html>
 <html lang="zh-CN">
   <head>
      <title></title>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1">
      <link rel="shortcut icon" href="imgs/favicon.ico" type="image/x-icon"/>
      <link rel="stylesheet" href="less/Font-Awesome/css/brands.css">
      <link rel="stylesheet" href="less/Font-Awesome/css/all.css">
      <link rel="stylesheet" href="css/index.css"/>
   </head>
   <body>
      <span class="fas fa-camera"></span>
      <span class="fas fa-user"></span>
      <span class="fab fa-instagram"></span>
      <span class="fab fa-facebook"></span>
      <span class="fab fa-twitter"></span>
      <span class="fab fa-whatsapp"></span>
   </body>
 </html>
 ``` 

#### 4. 字体图标居中对齐

- 绝对定位让字体图标脱离文档流,使5层span叠在一处；

- 采用flex居中对齐
- `display: flex !important;`很重要

  ```css
  ul li a span{
    width: 80px;
    height: 80px;
    background: #333;
    font-size: 30px;
    color: orangered;
    display: flex !important; /*very important*/
    justify-content: center;
    align-items: center;
    position: absolute;
    left: 0;
    top: 0;
  }
  ```

#### 5. li:nth-child(i): hover 

- 改变span背景色

  ```css
  ul li:nth-child(i):hover span:  {
    background: #55acee;
  }
  ```

#### 6. li:hover span:nth-child(i)

- 改变`span:nth-child(i)`改变位置和透明度
- 对span设置过度： `transition`

  ```css
  ul li:hover span:nth-child(5) {
    transform: translate(40px, -40px);
    opacity: 1;
  }
  ul li:hover span:nth-child(4) {
    transform: translate(30px, -30px);
    opacity: 0.8;
  }
  ul li:hover span:nth-child(3) {
    transform: translate(20px, -20px);
    opacity: 0.6;
  }
  ul li:hover span:nth-child(2) {
    transform: translate(10px, -10px);
    opacity: 0.4;
  }
  ul li:hover span:nth-child(1) {
    transform: translate(0px, 0px);
    opacity: 0.2;
  }
  ```

#### 7.源码

- HTML: index.hmtl
- LESS: less/index.less
- CSS: css/index.css