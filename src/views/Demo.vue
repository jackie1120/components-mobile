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
    <zv-checkbox-text :list="columns" v-model="form.checkbox" />
    <zv-checkbox-text :list="columns" v-model="form.checkbox2" valueType="string" />
    <van-cell center title="开关">
      <template #right-icon>
        <zv-switch v-model="form.switch" active-value="01" inactive-value="02" size="24" active-text="开" inactive-text="关" />
      </template>
    </van-cell>
    <div><zv-switch v-model="form.switch2" /></div>
    <div><zv-switch1 v-model="form.switch3" size=24 /></div>
    <div><zv-switch1 v-model="form.switch3" size=24 :show-text=false /></div>
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
        picker2: '2C',
        checkbox: [],
        checkbox2: '',
        switch: '01',
        switch2: true,
        switch3: true
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
