06——JQ ajax  jsonp

```javascript
1.// jquery 的 ajax
    $.ajax({
        type:"get",
        url:"fetData.php",
        //data:$("form").serialize()
        data:{

        },
        dataType:'json',
        success:function(data){

        }
    })
2.// $.ajax 的其他相关知识点（了解）
    $(document).ajaxStart(function(){})
    $(document).ajaxStop(function(){})
    $.ajax({
        beforeSend:function(){

        },
        cache:false,
        error:function(){

        },
        complete:function(){

        },
        timeout:3000
    })
3.// $.ajax 实现 jsonp
    // 用 jquery 自动生成的回调接收数据
    $.ajax({
        type:"get",
        url:"跨域的地址",
        data:{

        },
        dataType:"jsonp",
        success:function(data){
            console.log(JSON.parse(data));
        }
    });

    // 用户自定义的回调接收数据
    function get(data) {

    }
    $.ajax({
        type:"get",
        url:"跨域的地址",
        data:{

        },
        dataType:"jsonp",
        jsonpCallback:"get"
    })
4.// 实现 ajax 的更简洁的方法（了解）
	$.get();
	$.post();
	$.getJSON();
	$.getScript();
```

