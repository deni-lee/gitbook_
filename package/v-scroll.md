# v-scroll

v-scroll基於better-scroll滾動指令

## 安裝

```javascript
npm install v-scroll --save
```

## 使用

```javascript
import Vue from 'vue'
import vscroll from 'v-scroll'
Vue.use(vscroll)
```

```javascript
<div id="app" v-scroll>
    <div id="inner">
      //.....
    </div>
</div>
```

```javascript
< div id = “ app ” v-scroll = “ {method：appScroll，opts：appScrollOpts  ” >  
    < div id = “ inner” > 

    </ div >
</ div >
new Vue（{
     data（）{
        return{

            //配置
            appScrollOpts：{
                click：true，
            }
        }
    }，
    method： {
        appScroll（scroll）{

            //方法
            console.log（scroll）
        }
    }
}）。$ mount（“＃app”）
```

## 參考文獻

[https://ustbhuangyi.github.io/better-scroll/doc/zh-hans/\#better-scroll %E6%98%AF%E4%BB%80%E4%B9%88](https://ustbhuangyi.github.io/better-scroll/doc/zh-hans/#better-scroll%20%E6%98%AF%E4%BB%80%E4%B9%88) better scroll

[https://github.com/olyy111/v-scroll\#readme](https://github.com/olyy111/v-scroll#readme) v-scroll

