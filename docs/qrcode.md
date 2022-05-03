# [qrcode](https://www.cnblogs.com/whkl-m/p/10797776.html)

## 实例化
   ```
    new QRCode(document.getElementById('qrcode'), 'http://www.baidu.com');
    
    // 或者配置一些选项
    var qrcode = new QRCode(document.getElementById("qrcode"), {
        text: "http://www.baidu.com",
        width: 128,
        height: 128,
        colorDark : "#000",
        colorLight : "#fff",
        correctLevel : QRCode.CorrectLevel.H
    });

   ```