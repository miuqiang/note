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
### js 实现深拷贝
```
1、
function deepClone(arr){
    var obj=arr.constructor==Array?[]:{};
　　//第二种方法 var obj=arr instanceof Array?[]:{}
　　//第三种方法 var obj=Array.isArray(arr)?[]:{}
　　for(var item in arr){
        if(typeof arr[item]==="object"){
            obj[item]=deepClone(arr[item]);
        }else{
            obj[item]=arr[item];
        }
    }
    return obj;
}
2、var obj = JSON.parse( JSON.stringify(obj) )
```
#### 保留小数点（非四舍五入）
```
const toFixed = (n, fixed=2) => ~~(Math.pow(10, fixed) * n) / Math.pow(10, fixed);
// Examples
toFixed(25.198726354, 1);       // 25.1
toFixed(25.198726354, 2);       // 25.19
toFixed(25.198726354, 3);       // 25.198
```
#### 反转字符串
```
const reverse = str => str.split('').reverse().join('');
reverse('hello world');     
// Result: 'dlrow olleh'
```
#### 要转成图片的字符串
```
/**
 * @param string val 要转成图片的字符串
 */
function textToImg(val) {
    var len = 12;/*文字长度*/
    var i = 0;
    var fontSize = 12;/*文字大小*/
    var fontWeight = 'normal';/*normal正常;bold粗*/
    var txt = val;
    var canvas = document.createElement("canvas");
    if (txt == '') {
        alert('请输入文字！');
        
    }
    if (len > txt.length) {
        len = txt.length;
    }
    canvas.width = fontSize * len;
    canvas.height = fontSize * (3 / 2)
            * (Math.ceil(txt.length / len) + txt.split('\n').length - 1);
    var context = canvas.getContext('2d');
    context.clearRect(0, 0, canvas.width, canvas.height);
    context.fillStyle = '#333';/*颜色*/
    context.font = fontWeight + ' ' + fontSize + 'px 微软雅黑';
    context.textBaseline = 'top';
    canvas.style.display = 'none';
    //console.log(txt.length);
    function fillTxt(text) {
        while (text.length > len) {
            var txtLine = text.substring(0, len);
            text = text.substring(len);
            context.fillText(txtLine, 0, fontSize * (3 / 2) * i++,
                    canvas.width);
        }
        context.fillText(text, 0, fontSize * (3 / 2) * i, canvas.width);
    }
    var txtArray = txt.split('\n');
    for (var j = 0; j < txtArray.length; j++) {
        fillTxt(txtArray[j]);
        context.fillText('\n', 0, fontSize * (3 / 2) * i++, canvas.width);
    }
    var imageData = context.getImageData(0, 0, canvas.width, canvas.height);
    //var img = $("img");
    //img.src = canvas.toDataURL("image/png");
    return canvas.toDataURL("image/png");
}
```
