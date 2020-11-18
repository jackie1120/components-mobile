<template>
  <div class="textcheck">
    <van-button
      class="textcheck__item"
      v-for="(item, index) in list"
      plain
      :key="index"
      :type="isChecked(item.value) ? 'primary' : 'default'"
      @click="toggle(item.value)"
    >{{ item.text }}</van-button>
  </div>
</template>

<script>
export default {
  name: 'ZvCheckboxText',
  props: {
    value: {
      required: true
    },
    list: {
      type: Array,
      required: true
    },
    valueType: {
      type: String,
      default: 'array'
    },
    split: {
      type: String,
      default: ','
    }
  },
  computed: {
    valueArr () {
      if (typeof this.value === 'undefined' || this.value === '') return []
      if (this.valueType === 'string') return this.value.split(this.split)
      else return this.value
    }
  },
  methods: {
    toggle (val) {
      const index = this.valueArr.findIndex(item => item === val)
      let newVal
      if (index === -1 && val) {
        // 添加item
        newVal = this.valueArr.concat([val])
      } else {
        // 删除item
        newVal = this.valueArr
        newVal.splice(index, 1)
      }
      this.updateValue(newVal)
    },
    updateValue (newVal) {
      if (this.valueType === 'string') {
        this.$emit('input', newVal.join(this.split))
      } else {
        this.$emit('input', newVal)
      }
    },
    isChecked (val) {
      return this.valueArr.find(item => item === val) !== undefined
    }
  }
}
</script>

<style lang="less" scoped>
.textcheck {
  display: flex;
  flex-wrap: wrap;
  .textcheck__item {
    margin-right: 8px;
    margin-bottom: 8px;
    white-space: nowrap;
  }
}
// .textcheck {
//   display: grid;
//   gap: 8px 8px;
//   grid-template-columns: repeat(auto-fill, minmax(50px, 1fr));
// }
</style>
