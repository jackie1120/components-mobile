<template>
  <div>
    <van-field
      readonly
      clickable
      required
      label="合同业务类型"
      placeholder="请选择合同业务类型"
    />
    <zv-field-picker
      required
      label="Picker测试1"
      placeholder="Picker测试1"
      v-model="form.picker"
      :columns=columns
    />
    <zv-field-picker
      required
      label="Picker测试2"
      placeholder="Picker测试2"
      v-model="form.picker2"
      :columns=columns2
    />
    <van-button @click="submit">提交</van-button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      columns: [
        { text: '测试A', value: 'A' },
        { text: '测试B', value: 'B' },
        { text: '测试C', value: 'C' }
      ],
      columns2: [
        { text: '测试2A', value: '2A' },
        { text: '测试2B', value: '2B' },
        { text: '测试2C', value: '2C' }
      ],
      form: {
        picker: 'B',
        picker2: '2C'
      }
    }
  },
  methods: {
    submit () {
      console.log(this.form)
    }
  }
}
</script>

<style>

</style>
