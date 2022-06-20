# webpack-img

webpack过程中对不同使用场景下的各种资源文件的处理，包括img,svg

场景包括


- 0 :src="../../../static/img/operateImg.png"

**静态目录下的图片**
结果使用相对路径引入图片，打包时webpack不会处理这个路径，原样保留

- 1 src="@/assets/img/scene-try.png"

打包时webpack处理成 base64的图片信息， 比如 `src="data:image/png;base64,iVBORw0KGgoAAAANSUu1//...../gAAAABJRU5ErkJggg=="`

`@/`表示当前工程的`src`路径

缺点：图片信息大时，入口文件也会大，影响首页加载显示的速度

- 2 :src="require('../../../../static/img/into.png')"

同2

- 3 :src="showImg" showImg: '../../../static/img/operateImg.png'

打包时webpack处理过程会将`showImg: require('../../../static/img/operateImg.png')`转化为`zGIB:function(t,e,a){t.exports=a.p+"static/img/operateImg.8c1572c.png"}`

```javascript
    data() {
      return {
        showImg: require('../../../static/img/operateImg.png'),
      }
    }    
```

- 4 src="../../../assets/images/loginlogo.png"

**非static目录下的图片**

```javascript
// <img class="title-img" alt="" src="../../../assets/images/loginlogo.png" />的部分编译输出的时如下部分
bVAf:function(t,e){t.exports="data:image/png;base64,iVBORw0KGgoAAAAN...FTkSuQmCC"}
a("img",{staticClass:"title-img",attrs:{alt:"",src:i("bVAf")}})

```

- 5 `login.vue` 文件`lang="css"` 中的 background: url(../assets/images/loginbg.jpg) no-repeat fixed 会原样输出

- 6 `home.scss`文件中的`background: url("../../assets/img/user.svg") no-repeat 0px/16px;`

`home.scss`文件中的`background: url("../../assets/img/user.svg") no-repeat 0px/16px;`会转化为`background:url(data:image/svg+xml;base64,PHN2ZyB4...Pjwvc3ZnPg==)`
