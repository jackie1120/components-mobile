<template>
  <div>
    <van-field
      readonly
      clickable
      v-bind="$attrs"
      :value="pickerValue | dictionaryTransform(columns)"
      @click="showPicker"
    ></van-field>
    <van-popup v-model="show" position="bottom" get-container="body">
      <van-picker
        show-toolbar
        :columns="columns"
        :default-index="index"
        @cancel="show = false"
        @confirm="pickerConfirm($event)"
      ></van-picker>
    </van-popup>
  </div>
</template>

<script>
export default {
  name: 'ZvFieldPicker',
  props: {
    readonly: {
      type: Boolean,
      default: false
    },
    columns: {
      type: Array,
      required: true
    },
    value: {
      type: String
    }
  },
  data () {
    return {
      show: false,
      pickerValue: ''
    }
  },
  computed: {
    index () {
      return this.columns.findIndex(item => item.value === this.value)
    }
  },
  watch: {
    value: {
      immediate: true,
      handler (val) {
        this.pickerValue = val
      }
    }
  },
  filters: {
    dictionaryTransform (val, columns) {
      if (val === '' || !val) return ''
      try {
        const item = columns.find(element => element.value === val.toString())
        return item.text
      } catch (e) {
        return val
      }
    }
  },
  methods: {
    showPicker () {
      if (!this.readonly) this.show = true
    },
    pickerConfirm (value) {
      this.pickerValue = value.value
      this.show = false
      this.$emit('input', value.value)
    }
  },
  mounted () {
    this.pickerValue = this.value
  }
}
</script>

<style>

</style>
