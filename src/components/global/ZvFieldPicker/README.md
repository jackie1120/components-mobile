结合了van-field和van-picker实现下拉选择器，支持所有的van-field属性。`columns`属性是对象数组的形式用于给picker传值

```js
<zv-field-picker
  required
  label="Picker测试1"
  placeholder="Picker测试1"
  v-model="form.picker"
  :columns=columns
/>

 columns2: [
  { text: '测试2A', value: '2A' },
  { text: '测试2B', value: '2B' },
  { text: '测试2C', value: '2C' }
],
```