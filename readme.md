# AiZhiQian随机图API食用说明

不来这里抽个卡嘛~( •̀ ω •́ )y → [Gacha](https://api-github.img11.eu.org/gacha)

本随机图API基于 [islandworld](https://iw233.cn/) 分享的数据，B站美图UP主们分享的图片和咱搜集的壁纸制作，图片 **绿色健康** 

随机图API及图床均已转为使用某些白嫖服务搭建，故为保障使用体验和稳定性，API有一定的调用限制，具体见下文

### 食用方法

API地址：https://api-github.img11.eu.org/random   
API地址：https://api-npm.img11.eu.org/random   
API地址：https://api-bili.img11.eu.org/random   
API地址：https://api-vika.img11.eu.org/random   
调用方法：GET

#### 速率和每日额度限制说明：

API限制：每IP每5秒内可以调用3次API，超出返回429



**此外，请注意，每个IP每24小时内仅可通过API获取10000张图片
达到限度后将无法使用API，API地址返回状态码403并给出恢复时间**

您可以 [访问这里](https://api-github.img11.eu.org/random?only_check=true) 以在不消耗额度的情况下查询您IP的剩余可用额度或可用额度恢复倒计时

#### 传入参数说明：

| 键         | 键描述                                                | 值类型  | 可用的值                                                  | 值描述                                                       |
| ---------- | ----------------------------------------------------- | ------- | --------------------------------------------------------- | ------------------------------------------------------------ |
| sort       | 索引的图片集 (可选，默认为approve)                    | Text    | random<br>people<br/>anime<br/>nature<br/>other<br/>phone | 索引全部图片<br/>索引美女图片 <br/>索引漫画图片 <br/>索引自然图片 <br/>索引其他图片 <br/>索引手机壁纸 |
| type       | 输出方法 (可选，默认为重定向)                         | Text    | text<br/>json                                             | 输出文本<br/>输出JSON格式                                    |
| num        | 输出图片数量 (可选，当num大于1时type固定为json)       | Integer | 小于等于100的任意正整数<br/>若不携带num则默认为1          |                                                              |
| thumbnail  | 使用缩略图(可选)                                      | Text    | large<br/>medium<br/>small                                | 最长边重设为800px<br/>最长边重设为176px<br/>最长边重设为96px |
| only_check | 检查可用额度 (可选，当此参数为任意真值时其它参数无效) | Any     | 任意真值，或不携带此参数                                  |                                                              |

Note：
图片均来自互联网，来源众多无法确认版权信息，侵删

Demo：

```http
GET https://api-github.img11.eu.org/random
GET https://api-github.img11.eu.org/random?thumbnail=large
GET https://api-github.img11.eu.org/random?sort=people
GET https://api-github.img11.eu.org/random?sort=anime&type=text
GET https://api-github.img11.eu.org/random?sort=nature&num=100
GET https://api-github.img11.eu.org/random?only_check=true
```

#### 返回参数说明：

注意：当携带num参数且num参数大于等于2时，API只会输出JSON格式

| 传入type | 返回值                                   | Demo                                                         |
| -------- | ---------------------------------------- | ------------------------------------------------------------ |
| text     | 图片URL                                  | `https://img.nahida.fun/2023/02/05/63e1b85fb27e9.jpg`        |
| json     | pic: 图片URL(s)数组 remain_num: 剩余额度 | `{ "pic": ["https:\/\/img.nahida.fun\/2023\/02\/05\/63e1b85fb27e9.jpg"],"remain_num": 2333 }` |
| 其它     | 重定向到图片URL                          | <img src="https://img.nahida.fun/2023/02/05/63e1b85fb27e9.jpg" style="max-width:180px;">  |

#### 将随机图API设置为网页背景

Demo(CSS)：

```css
html:before {
    background: url(https://api-github.img11.eu.org/random) no-repeat center 0/cover;
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    z-index: -1;
    content: "";
}
```

为了避免页面加载被过大的背景图阻塞导致加载缓慢，也可换用下面的方法

Demo(HTML)：

```html
<style>
.withBg:before {
    background: url(https://api-github.img11.eu.org/random) no-repeat center 0/cover;
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    z-index: -1;
    content: "";
}
</style>
<script>window.onload = () => document.documentElement.classList.add("withBg");</script>
```

#### 一个输出壁纸轮播HTML的API

API地址：https://api-github.img11.eu.org/player   
调用方法：GET

传入参数说明：

| 键   | 键描述                                        | 值类型  | 值描述                                          |
| ---- | --------------------------------------------- | ------- | ----------------------------------------------- |
| time | 每张图片的持续时间，单位为秒 (可选，默认为10) | Integer | 大于等于5的任意正整数<br/>若不携带time则默认为5 |

以下是在网页中插入随机轮播背景的使用例

Demo(HTML)：

```html
<iframe src="https://api-github.img11.eu.org/player?time=10" style="position:fixed;top:0;left:0;width:100%;height:100%;z-index:-1;border:none;overflow:hidden;"></iframe>
```

### API调用统计

| 图片总数 | 总调用量 | 总图片查看量 | 今日调用量 | 今日图片查看量 |
| -------- | -------- | ------------ | ---------- | -------------- |
| 95475    | 14447    | 17332        | 55         | 55             |

Note：时区使用UTC+0

### 鸣谢

随机图API的搭建离不开以下B站UP主的分享，在此表达衷心的感谢！(UID正序)

[islandworld](https://space.bilibili.com/7600422) [PaoMianの](https://space.bilibili.com/12644002) [轻百萌豚](https://space.bilibili.com/24957607) [星绘汐音](https://space.bilibili.com/37743601) [一只喵喵酱y](https://space.bilibili.com/234381697)<br>[諸星小紬](https://space.bilibili.com/290094404) [玟w玟_](https://space.bilibili.com/404271487) [奶昔酱不会忧郁丶](https://space.bilibili.com/471763466) [约尔yuer](https://space.bilibili.com/488095650) [和之凌雪](https://space.bilibili.com/501659561)<br>[小朱不只是可爱](https://space.bilibili.com/506769005) [游手好闲的孟极](https://space.bilibili.com/1391022645) [萌村百科](https://space.bilibili.com/2024069799)

### 友情链接

非常好用的AI以图识番(Gal)网站：[AnimeTrace](https://ai.animedb.cn/)

图床缓存由 [Cloudflare](https://www.cloudflare.com/) 提供服务
亚太加速由 [雨云](https://www.rainyun.com/) 提供服务
图床源站由 [Microsoft Azure](https://azure.microsoft.com/) 提供服务
部分方法已在 [GitHub](https://github.com/ZiAzusa/nahida-random-image) 开源

------

2022-2023: Nahida.Fun
Made with ♡ by [ZiAzusa](https://about.sukimoe.cn/)
