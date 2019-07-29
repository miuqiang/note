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
 #### 常用正则
  ```
  //用户名正则，4到16位（字母，数字，下划线，减号）
  var uPattern = /^[a-zA-Z0-9_-]{4,16}$/;
  //密码强度正则，最少6位，包括至少1个大写字母，1个小写字母，1个数字，1个特殊字符
  var pPattern = /^.*(?=.{6,})(?=.*\d)(?=.*[A-Z])(?=.*[a-z])(?=.*[!@#$%^&*? ]).*$/;
  //正整数正则
  var posPattern = /^\d+$/;
  //负整数正则
  var negPattern = /^-\d+$/;
  //整数正则
  var intPattern = /^-?\d+$/;
  //正数正则
  var posPattern = /^\d*\.?\d+$/;
  //负数正则
  var negPattern = /^-\d*\.?\d+$/;
  //数字正则
  var numPattern = /^-?\d*\.?\d+$/;
  //Email正则
  var ePattern = /^([A-Za-z0-9_\-\.])+\@([A-Za-z0-9_\-\.])+\.([A-Za-z]{2,4})$/;
  //手机号正则
  var mPattern = /^((13[0-9])|(14[5|7])|(15([0-3]|[5-9]))|(18[0,5-9]))\d{8}$/;
  //身份证号（18位）正则
  var cP = /^[1-9]\d{5}(18|19|([23]\d))\d{2}((0[1-9])|(10|11|12))(([0-2][1-9])|10|20|30|31)\d{3}[0-9Xx]$/;
  //URL正则
  var urlP= /^((https?|ftp|file):\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/;
  //车牌号正则
  var cPattern = /^[京津沪渝冀豫云辽黑湘皖鲁新苏浙赣鄂桂甘晋蒙陕吉闽贵粤青藏川宁琼使领A-Z]{1}[A-Z]{1}[A-Z0-9]{4}[A-Z0-9挂学警港澳]{1}$/;
  //包含中文正则
  var cnPattern = /[\u4E00-\u9FA5]/;
  ```
  
  #### input只能输入数字
  ```
  oninput = "value=value.replace(/[^\d]/g,'')"
  
  ```
#### js 常用正则
```
只能输英文:<input type="text" oninput="value=value.replace(/[^a-zA-Z]/g,'')">
        只能输入汉字：<input oninput="value=value.replace(/[^\u4E00-\u9FA5]/g,'')" onbeforepaste="clipboardData.setData('text',clipboardData.getData('text').replace(/[^\u4E00-\u9FA5]/g,''))">
        只能输入英文、数字、@符号和.<>?\：符号:<input type="text" oninput="value=value.replace(/[^a-za-z0-9u4e00-u9fa5.@]/g,'')"><br><br>
        只能输入英文字母和数字,不能输入中文:<input oninput="value=value.replace(/[^\w\/]/ig,'')"><br><br>
        只能输入数字、字母、下划线:<input ID="txtShopNumber" runat="server" class="input_text" oninput="value=value.replace(/[^(\-)\w\.\/]/ig,'')"/>
        只能输入数字的：<input oninput="value=value.replace(/[^\d]/g,'') " onbeforepaste="clipboardData.setData('text',clipboardData.getData('text').replace(/[^\d]/g,''))" ID="Text2">
```
  
