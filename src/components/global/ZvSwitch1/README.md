基于html的开关控件，支持显示开关的文字信息。属性信息如下：
* size(可选)：控件大小，默认30
* value(必填)：控件绑定值，支持字符串、数字、布尔
* ictive-value(可选)：选中状态的值，支持字符串、数字、布尔，默认true
* inactive-value(可选)：未选中状态的值，支持字符串、数字、布尔，默认false
* active-text(可选)：选中状态的文字，默认是
* inactive-text(可选)：未选中状态的文字，默认否
* show-text(可选)：是否显示文字，默认是

```html
<zv-switch1 v-model="form.switch3" size=24 />
<zv-switch1 v-model="form.switch2" />
```