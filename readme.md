
# node-ccap —— node.js generate captcha using c++ library CImg.

You can generate captcha without install any other libraries or software, only do npm install ccap, that's all.

node-ccap support linux and windows.

compile maybe cost you 1 minute,simply wait;

if you install jpeg lib,you can rebuild it using binding.gyp.jpeg file, support jpeg export.default is bmp!

##performance

  generate captcha picture 1204/sec;//BMP unzip

##Install

   npm install ccap

   var ccap = require('ccap')

##Instantiated

   these three ways all will be ok:

	var captcha = ccap();
	
	var captcha = ccap(width, height, offset);

	var captcha = ccap({
		
		width:256,//set width,default is 256

		height:60,//set height,default is 60

		offset:40,//set text spacing,default is 40

		quality:100,//set pic quality,default is 50

		generate:function(){//Custom the function to generate captcha text
		
		     //generate captcha text here

		     return text;//return the captcha text

		}
	
	});
	   

##API
   
	var captcha = ccap();

	var ary = captcha.get();//ary[0] is captcha's text,ary[1] is captcha picture buffer.

	var text = ary[0];

	var buffer = ary[1];


##Simple Example
	
	var http = require('http');
	
	var ccap = require('ccap')();//Instantiated ccap class 

	http.createServer(function (request, response) {

		if(request.url == '/favicon.ico')return response.end('');//Intercept request favicon.ico

		var ary = ccap.get();

		var txt = ary[0];

		var buf = ary[1];

		response.end(buf);

		console.log(txt);

	}).listen(8124);

	console.log('Server running at http://127.0.0.1:8124/');



## 授权协议

基于MIT协议发布：

```
Copyright (c) 2013 wu zhonghua <snoopyxdy@gmail.com>

The MIT License

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```