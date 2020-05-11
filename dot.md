# 关于Web无障碍浏览

## `role` 属性

属性名|属性作用
--|--
`alert` | 表示警告
`alertdialog` | 表示警告弹出框
`application` | 表示应用
`button` | 表示按钮
`checkbox` | 表示复选框
`combobox` | 表示下拉列表框
`grid` | 表示网格
`gridcell` | 表示网格单元
`group` | 表示组合
`heading` | 表示应用程序标题头
`listbox` | 表示列表框
`log` | 表示日志记录
`menu` | 表示菜单
`menubar` | 表示菜单栏
`menuitem` | 表示菜单项
`menuitemcheckbox` | 表示可复选的菜单项
`menuitemradio` | 表示只能单选的菜单项
`option` | 表示选项
`presentation` | 表示称述
`progressbar` | 表示进度条
`radio` | 表示单选
`radiogroup` | 表示单选组
`region` | 表示区域
`row` | 表示行
`separator` | 表示分隔
`slider` | 表示滑动条
`spinbutton` | 表示微调
`tab` | 表示标签
`tablist` | 表示标签列表
`tabpanel` | 表示标签面板
`timer` | 表示计数
`toolbar` | 表示工具栏
`tooltip` | 表示提示文本
`tree` | 表示树形
`treeitem` | 表示树结构选项

## `aria` 属性

属性名 | 属性值
--|--
`aria-activedescendant` | 字符串。表示后代元素的id值
`aria-atomic` | 字符串.表示区域内容是否完整播报.值可以为true和false.当为true时,表示辅助设备需要把整个区域内容都通报给使用者; 如果为false则表示只需要同胞修改的部分.
`aria-autocomplete` | 字符串.表示用户的文本框的自动提示是否提供.可选值有: inline, list, both, none.
`aria-busy` | 字符串.表示当前区域的忙碌状态.默认为false, 表示清除busy状态; 可选为true, 表示该区域正在加载; 或为error, 表示该区域验证无效
`aria-controls` | 字符串.空格分隔的id属性值列表
`aria-describedby` | 字符串.空格分隔的id属性值列表
`aria-dropeffect` | 字符串.表示拖拽效果.可选值有: copy, move, reference, execute, popup, none, 依次表示: 复制, 移动, 参照, 执行, 弹出以及没有效果.
`aria-flowto` | 字符串.空格分隔的id值们
`aria-grabbed` | 字符串.拖拽中元素的捕获状态.可选值: true, false, undefine.默认为undefine, 表示元素捕获状态未知.true表示元素可以捕获;false表示不能被捕获.
`aria-haspopup` | 字符串.true表示点击的时候会出现菜单或是浮动元素; false表示没有pop-up效果.
`aria-label` | 字符串.
`aria-labelledby` | 字符串.空格分隔的id们
`aria-level` | 数值.表示等级
`aria-live` | 字符串.可选值有: off, polite, assertive, rude.默认为off, 表示不宣布更新;polite表示只有用户闲时宣布; assertive表示尽快对用户宣布; rude表示即时提醒用户,必要的时候甚至中断用户.
`aria-multiselecttable` | 字符串.表示是否可多选.默认为false, 表示一次只能选择一个项.true表示一次可以选择多个项.
`aria-owns` | 字符串.值为目标元素id
`aria-posinset` | 数值.表示当前位置.
`aria-readonly` | 字符串.表示是否只读.默认为false, 表示元素值可以被修改; true表示元素指不能被改变.
`aria-relevant` | 字符串.表示区域内哪些操作行为需要做出反应.可选值有: additions, removals, text, all, 可以空格分隔多个一起显示. additions表示新增节点的时候做出反应;removals表示删除节点时重要操作; text表示文本改变是值得重视的; all等同于同时使用上面三个属性值.
`aria-required` | 字符串.元素值是否必需.默认为false, 表示元素值可以为空;true 表示元素值必需的.
`aria-secret` | 字符串.表示机密状态.
`aria-setsize` | 数值.设置的尺寸大小值.
`aria-sort` | 字符串.表示表格或格栅中的项是以升序排序还是降序排列.可选值: ascending(升序), descending(降序), none, other
`aria-valuemax` | 数值.表允许的最大值.
`aria-valuemin` | 数值.表示允许的最小值.
`aria-valuenow` | 数值.表示当前值
`aria-valuetext` | 字符串.定义等同于aria-valuenow人可读的文本
`aria-checked` | 字符串.表示检查的状态.true表示元素被选择; false表示元素未被选择; mixed表示元素同时有选择和选择状态
`aria-disabled` | 字符串.表禁用状态, true表示当前是非激活状态; false表示清除非激活状态.
`aria-expanded` | 字符串.表示展开状态.默认未undefine, 表示当前展开状态未知.其他可选值: true表示元素是展开的: false表示元素不是展开的.
`aria-hidden` | 字符串.可选值为true和false, true表示元素隐藏(不可见), false表示元素可见.
`aria-invalid` | 字符串.表示元素值是否错误的.默认为false, 表示是OK的, 如果为true, 则表示值验证不通过.
`aria-pressed` | 字符串.表示按下的状态, 可选值有: true, false, mixed, undfined.默认为undfined, 表示按下状态未知; true表示元素往下(按钮按下);false表示元素抬起; mixed表示元素同时有按下和没有按下的状态.
`aria-selected` | 字符串. 表示选择状态. 可选值有: true, false, undfined 默认值为undfined, 表示元素选择状态未知. true表示元素已选择, false表示未被选中.

## `ARIA` 相关大图

![ARIA所有属性大图](https://image.zhangxinxu.com/image/blog/201203/aria.png)