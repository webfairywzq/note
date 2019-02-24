09——node js 爬虫

1. 网络爬虫（又称网页蜘蛛、网络机器人）

   是一种按照一定的规则，自动地抓取万维网信息的程序或脚本

   （说白了就是=http客户端=，通过 http 协议和远程 http 服务器通信，获取 html 页面内容和浏览器不同的一点就是：==爬虫不会把抓取的内容渲染出来，而是解析页面内容然后保存到数据库里面==）

2. 用到 2 个模板：

   1. request ：

      一个简化了的 HTTP 请求客户端，用于向其他服务器发起请求

      request(网址，function(err,res,body){

      ​	console.log(body);

      })

   2. cheerio：

      是 nodejs 的抓取页面模块，为服务器特别定制的、快速、灵活、实施的 jQuery 核心实现，适合各种 web 爬虫程序

3. 爬虫程序： phantomjs（可以爬去动态数据）

4. 步骤：

   1. 引入模板：

      ```javascript
      const request = require("request");
      const cheerio = require("cheerio");
      const fs = require("fs");
      const path = require("path");
      const mysql = require("mysql");
      ```

   2. 创建数据库：

      ```javascript
      var conn = mysql.createConnection({
      	host : "localhost",
      	user :"root",
      	password :"root",
      	port :"3306", //端口号
      	database :"shopmes"
      })
      conn.connect();
      ```

   3. 爬取所需信息：

      ```javascript
      request("https://www.epet.com/cleargoodsmcat.html",function(err,res,body){
      	var $ = cheerio.load(body);
      	var list = $(".qcGoodsBox.bgwhite  .fl.rela"); //与 jquery 用法相同，找到所需信息，再进一步进行获取
      	list.each(function(index){
      		var imgsrc = $(this).find(".cloud-zoom  img").attr("src00"); //拿到图片信息
      		//将图片存入 downloading 文件夹中
      	//request(imgsrc).pipe(fs.createWriteStream(__dirname+"/downloading/"+path.parse(imgsrc).base));
      	//__dirname：绝对路径； path.parse(ingsrc).base：拿到图片名字==
      		var title = $(this).find(".qcGoodsTit  a").text();  // 拿到对应 a 标签下的文本信息，
      		//使用 text() 直接得到文本信息；使用 html() 由于里面可能有标签、尖括号等，得到十六进制信息，还需进行转换
      		//  得到对应的价格信息（现价和原价）
      		var price = $(this).find(".qcPriceBox  .ft20").text();
      		var yprice = $(this).find(".qcPriceBox  ft12").text();  
          	conn.query("insert  into  shopgoods(image,message,price,yprice)  values(?,?,?,?)", [imgsrc,title,price,yprice], function(err,results,f){
        				console.log(results);
        		})
        	})
        	conn.end();  //自动断开数据库连接；
        })  
      ```

