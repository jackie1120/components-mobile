基于van-switch，支持显示开关的文字信息。支持所有的van-switch属性和事件，并添加`active-text`(默认值：是)和`inactive-text`(默认值：否)属性能够显示开关文字

```html
<van-cell center title="开关">
  <template #right-icon>
    <zv-switch v-model="form.switch" active-value="01" inactive-value="02" size="24" active-text="开" inactive-text="关" />
  </template>
</van-cell>

<zv-switch v-model="form.switch2" />
```