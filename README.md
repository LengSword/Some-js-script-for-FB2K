# Some-js-scripts-for-FB2K

## ncm.js
FB2K ESLyric 下的能获取网易云音乐歌词并进行一些处理的脚本

修改说明：加强对日语歌兼容性

使用说明：
打开"设置->Tools->ESLyric"，

找到"Lyric Search"，把"Lyric matching level"改成30左右。

因为日语歌翻唱很多，歌名也比较混乱，比如后面加个"feat.","(Cover)","(カバー)"什么的。

日语歌歌名重名的似乎很少，所以匹配到歌名一般就OK，我的fork对这里进行了修改。

### 设置歌词输出顺序,删除即不获取
old_merge:并排合并歌词,newtype:并列合并,tran:翻译,origin:原版歌词；

(new_merge:不推荐使用 实现卡拉OK模式下不高亮翻译,不支持保存,英语字符歌词会显示时间轴:ESLyric实现问题)
``` javascript
var lrc_order = [
	"newtype",
	"new_merge",
        "origin",
        "tran"
    ];
```

### 更改或删除翻译外括号
``` javascript
var bracket = [ 
        "「", //左括号
		"」"  //右括号
    ];
```

### 其他
``` javascript
//搜索歌词数,如果经常搜不到试着改小或改大
var limit = 4;
//修复newtype歌词保存 翻译提前秒数 设为0则取消
var savefix = 0.01;
//new_merge歌词翻译时间轴滞后秒数
var timefix = 0.01;
//当timefix有效时设置offset(毫秒)
var offset=-20;
```

## cover.js
一个简单的获取网易云音乐封面的WSH脚本;

新建WSH面板载入脚本使用;

获取的封面保存在 歌曲目录\Cover[-%artist%]-%title%.jpg 下;

在WSH面板上会显示获取的封面；

也可在参数选项：显示 搜索模板 在“cover.jpg”下添加“Cover[-%artist%]-%title%.jpg”，以在封面显示器面板显示；

载入错误请重新加载；
