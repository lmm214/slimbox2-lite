slimbox2-lite
=============
相对官方作了以下改动：

1. 去除了灯箱底部的图片信息显示

```
//删除去了以下 4 个 DOM 相关的代码
bottomContainer, bottom, caption, number
```

2. 图片灯箱自适应，再也不怕插入高清

```
function animateBox() {
	center.className = "";
	//CSS 内新增 background-size":"100%"，之后增加对浏览器宽、高和图片宽、高判断。
	$(image).css({backgroundImage: "url(" + activeURL + ")", visibility: "hidden", display: "","background-size":"100%"});
	var p_w = preload.width,p_h = preload.height,w_w = win.width(),w_h = win.height();
	if (p_w >= w_w || p_h >= w_h){
		if ( w_w >= w_h ){
			$(sizer).width(w_h*0.8*p_w/p_h);
			$([sizer, prevLink, nextLink]).height(w_h*0.8);
		}else{
			$(sizer).width(w_w*0.8);
			$([sizer, prevLink, nextLink]).height(w_w*0.8*p_h/p_w);
		}			
	}else{
		$(sizer).width(preload.width);
		$([sizer, prevLink, nextLink]).height(preload.height);
	}
	//End
```