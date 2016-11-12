# renwusuishubiaoyidong
跟随鼠标移动事件onmousedown  onmousemove  onmouseup

样式：img{position: absolute;}

js部分：
function moveEvent(_coords){
		var _timer=0;
		var i=0;
		var _img=document.getElementById("img");
		_img.src="2.gif";
		function exec(){
			window.clearTimeout(_timer);			
				_img.style.left=_coords[i][0]+"px";
				_img.style.top=_coords[i][1]+"px";
				i++;
			if (i>=_coords.length) {
				_img.src="1.gif";
				return;
			}
			_timer=window.setTimeout(exec,30);
		}
		exec();		
	}
	function boundEvent(){
		var _coords=new Array();
		document.onmousedown=function(){
			document.onmousemove=function(e){								
				var e=e||window.event;
				_coords.push([e.clientX,e.clientY]);
			}
		}
		document.onmouseup=function(){
			document.onmousemove=null;
			moveEvent(_coords);
		}
	}
	window.onload=function(){
		boundEvent();
	}
  
  主体部分：
  <img src="1.gif" id="img" />
