HTML5————移动端处理屏幕适配

<script>
    ;(function(){
        function w(){
            var r=document.documentElement;
            var a=r.getBoundingCLientRect().width;
            if(a>750){
                a=750;
            }
            rem=a/7.5;
     		r.style.fontSize=rem+"px";
        }
        var t;
        w();
        window.addEventListener("resize",function(){
            clearTimeOut(t);
            t=setTimeOut(w,300);
        },false);
    })();
</script>

