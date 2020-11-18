基于文本的多选，默认情况下value是数组，也可以通过指定valueType为string，返回基于split(默认`,`)拼接的字符串
```js
<zv-checkbox-text :list="list" v-model="form.checkbox" />
<zv-checkbox-text :list="columns" v-model="form.checkbox2" valueType="string" />

 list: [
  { text: '测试2A', value: '2A' },
  { text: '测试2B', value: '2B' },
  { text: '测试2C', value: '2C' }
],
```