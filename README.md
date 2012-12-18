WebService
==========

337平台提供的 web service 规格说明

公共参数
------
api支持jsonp协议的方法调用，以下为公共参数：

1.api_key 应用调用key用来识别调用者身份，请向相关人士索取

2.callback 如通过jsonp调用，必须通过此参数提供回调函数名 [jsonp][jsonp]

例如：

`http://api.337.com/user/session?api_key=xlfc%40elex337_tw_1&callback=Elex337.ApiServer._callbacks.e121508720694aa`

返回：

`Elex337.ApiServer._callbacks.e121508720694aa({"status":-1})`

在对返回内容说明时，此文档仅对“回调方法的参数”进行说明，即上例中的{"status":-1}


[jsonp]: http://en.wikipedia.org/wiki/JSONP 

语言
-----
某些api需要指定终端用户的语言（例如取游戏服列表功能）。语言参数可从以下表格内选取

<table border="1">
  <tr>
    <th>语言</th>
    <th>代号</th>
  <th>语言</th>
    <th>代号</th>
	<th>语言</th>
    <th>代号</th>
  </tr>
<tr>
    <td>繁体中文</td>
    <td>tw</td>
<td>简体中文</td>
    <td>cn</td>
<td>葡语</td>
    <td>pt</td>
  </tr>
<tr>
    <td>德语</td>
    <td>de</td>
<td>土耳其语</td>
    <td>tr</td>
<td>英语</td>
    <td>en</td>
</tr>
<tr>
    <td>西班牙语</td>
    <td>es</td>
<td>波兰语</td>
    <td>pl</td>
<td>荷兰语</td>
    <td>nl</td>
</tr>
<tr>
    <td>阿拉伯</td>
    <td>ar</td>
	<td>泰语</td>
    <td>th</td>
</tr>
</table>


在后续的api地址说明上，若地址中包含[lang]则表示需要提供语言参数
比如“取服列表”功能，面向繁体中文用户时，请请求`http://www.337.com/tw/api/get_game_server`

*如果不传递语言参数，则会由337服务器根据客户端信息判断用户语言。这将造成一定的性能损失与延迟。

1.取服列表
---
URL：
`http://www.337.com/[lang]/api/get_game_server`

参数
<table border="1">
<tr>
    <th>参数</th>
    <th>说明</th>
</tr>
<tr>
    <td>gKey</td>
    <td>所查询游戏的gKey</td>
</tr>
</table>

例：
`http://www.337.com/tw/api/get_game_server?api_key=xlfc%40elex337_tw_1&gKey=xlfc%40elex337_tw_1`

返回服数组：
<table border="1">
<tr>
    <th>参数</th>
    <th>说明</th>
</tr>
<tr>
    <td>key</td>
    <td>服id</td>
</tr>
<tr>
    <td>version</td>
    <td>服版本号</td>
</tr>
<tr>
    <td>lang</td>
    <td>服的发布语言</td>
</tr>
<tr>
    <td>sns_type</td>
    <td>发布平台类型</td>
</tr>
<tr>
    <td>weight</td>
    <td>权重</td>
</tr>
<tr>
    <td>title</td>
    <td>服名称</td>
</tr>
<tr>
    <td>status</td>
    <td>服状态</td>
</tr>
<tr>
    <td>url</td>
    <td>服链接</td>
</tr>
</table>


2.取游戏新闻&攻略
---
URL:
`http://www.337.com/[lang]/api/get_site_news`

参数
<table border="1">
<tr>
    <th>参数</th>
    <th>说明</th>
</tr>
<tr>
    <td>gKey</td>
    <td>所查询游戏的gKey</td>
</tr>
<tr>
    <td>type</td>
    <td>1表示新闻；4表示攻略，默认为1</td>
</tr>
<tr>
    <td>max</td>
    <td>最多返回条数，默认为5</td>
</tr>
</table>

例：
`http://www.337.com/tw/api/get_site_news?api_key=xlfc%40elex337_tw_1&gKey=xlfc%40elex337_tw_1&type=1`

返回服数组：
<table border="1">
<tr>
    <th>参数</th>
    <th>说明</th>
</tr>
<tr>
    <td>did</td>
    <td>文章id</td>
</tr>
<tr>
    <td>link</td>
    <td>文章链接</td>
</tr>
<tr>
    <td>time</td>
    <td>文档创建时间</td>
</tr>
<tr>
    <td>title</td>
    <td>文章标题</td>
</tr>
</table>


3.取玩家的游戏历史
---
URL:
`http://www.337.com/[lang]/api/get_user_game_server`

参数
<table border="1">
<tr>
    <th>参数</th>
    <th>说明</th>
</tr>
<tr>
    <td>gKey</td>
    <td>所查询游戏的gKey</td>
</tr>
<tr>
    <td>gameuid</td>
    <td>gameuid</td>
</tr>
</table>

例：
`http://tw.337.com/api/get_user_game_server?gameuid=elex337_23577489&gKey=ddt@elex337_pt_1`

返回服数组：
<table border="1">
<tr>
    <th>参数</th>
    <th>说明</th>
</tr>
<tr>
    <td>server_name</td>
    <td>服名称</td>
</tr>
<tr>
    <td>last_play_time</td>
    <td>上一次游戏时间</td>
</tr>
<tr>
    <td>server_id</td>
    <td>服id</td>
</tr>
<tr>
    <td>url</td>
    <td>游戏地址</td>
</tr>
</table>


