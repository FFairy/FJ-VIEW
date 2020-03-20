# Cell 单元格 
## 引入
#### 在app.json或index.json中引入组件
```
"fj-cell-group": "../../fj-dist/fj-cell-group/fj-cell-group",
"fj-cell": "../../fj-dist/fj-cell/fj-cell"
```

##  代码演示
#### 基础用法
Cell可以单独使用，也可以与CellGroup搭配使用。CellGroup可以为Cell提供上下外边框和 标题。
```
<fj-cell-group title="基础用法" >
    <!-- 基础用法 -->
    <fj-cell title="第三个单元格" border="true" value="这是内容">
    </fj-cell>
    <!-- 带icon 的基础用法 -->
    <fj-cell leftIcon="close" border="true"  title="第三个单元格" value="这是内容" valueIcon="add">
    </fj-cell>
</fj-cell-group>
```

#### url 跳转
设置isLink属性后会在单元格右侧显示箭头,url 为需要跳转的地址,linkType 为链接类型(默认为：navigateTo , 可选值为 navigateTo，redirectTo，switchTab，reLaunch) 设置isLink默认右侧为箭头，可使用slot改变右侧内容
```
<fj-cell-group title="url 跳转" >
    <!-- 基础用法 -->
    <fj-cell isLink="true" title="url 跳转" border="true" linkType="navigateTo" url="/pages/user/user">
    </fj-cell>
    <!-- 使用slot -->
    <fj-cell isLink="true" title="使用slot" linkSlot="true" url="/pages/user/user" linkType="navigateTo">
        <fj-icon slot="cell_link" type="clock"/>
    </fj-cell>
</fj-cell-group>
```

#### 使用插槽
如以上用法不能满足你的需求，可以使用插槽来自定义内容,想要使用cell_link插槽，需设置linkSlot为true,另外使用cell_link插槽之后, cell_value 插槽 默认不显示
```
<fj-cell-group title="使用插槽" >
    <!-- 基础用法 -->
    <fj-cell border="true" >
        <fj-icon slot="cell-left" type="clock"/>
        <text slot="cell_title">标题</text>
        <text slot="cell_value">内容</text>
        <text slot="cell_desc">描述</text>
    </fj-cell>
    <!-- 使用链接 的插槽 -->
    <fj-cell isLink="true" linkSlot="true" url="/pages/user/user">
        <fj-icon slot="cell-left" type="clock"/>
        <view slot="cell_title">
            <view>地址</view>
            <view>广东省东莞市</view>
        </view>
        <fj-icon slot="cell_link" type="clock"/>
        <text slot="cell_desc">描述</text>
    </fj-cell>
</fj-cell-group>
```
#### fj-class
当前默认样式无法满足你的需求，可以使用fj-class来自定义样式
```
<fj-cell-group title="使用插槽" >
    <!-- 基础用法 -->
    <fj-cell fj-class="cell-red" title="第三个单元格" border="true" value="这是内容">
</fj-cell-group>
.cenn-red{
    background-color:red;
}
```

##  API

#### CellGroup properties
| 属性    |   说明 |   类型  |  默认值 
| :-----:| :----: | :----: | :----: |
| fj-class | 自定义 class 类名 | String | - |

#### Cell properties 
| 属性    |   说明 |   类型  |  默认值 
| :-----:| :----: | :----: | :----: |
| fj-class | 自定义 class 类名 | String | - |
| leftIcon | 左侧图标,填图标名称，例如 add | String | - |
| title | 左侧标题 | String | - |
| value | 右侧内容 | String | - |
| valueIcon | 右侧图标,填图标名称，例如 add | String | - |
| desc | 描述 | String | - |
| border | 下边框 | Boolean | false |
| url | 链接地址 | String | - |
| isLink | 是否展示右侧箭头并开启尝试以 url 跳转 | Boolean | false |
| linkType | 链接类型，可选值为 navigateTo，redirectTo，switchTab，reLaunch | String | navigateTo |
| linkSlot | 链接右侧箭头自定义插槽 | Boolean | false |

#### Cell Slot
| 名称    |   说明 
| :-----:| :----: | 
| cell-left | 左侧图标插槽 | 
| cell_title | 左侧标题插槽 |
| cell_value | 右侧内容插槽 |
| cell_link | 进行页面跳转时，右侧插槽，需设置linkSlot为true，使用此插槽，cell_value插槽无效 |
| cell_desc | 描述插槽 |
