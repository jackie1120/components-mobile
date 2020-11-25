<template>
  <div class="switch" :style="{'font-size': fontSize}">
    <van-switch ref="switch" v-bind="$attrs" v-on="$listeners" :size="size" />
    <span class="switch__text" :class="{'switch__text--active': isActive}" @click="toggle">{{ text }}</span>
  </div>
</template>

<script>
export default {
  name: 'ZvSwitch',
  props: {
    size: {
      type: [Number, String],
      default: '30'
    },
    activeText: {
      type: String,
      default: '是'
    },
    inactiveText: {
      type: String,
      default: '否'
    }
  },
  computed: {
    fontSize () {
      return this.size + 'px'
    },
    isActive () {
      if (this.$attrs['active-value']) {
        return this.$attrs.value === this.$attrs['active-value']
      } else {
        return this.$attrs.value === true
      }
    },
    text () {
      return this.isActive ? this.activeText : this.inactiveText
    }
  },
  methods: {
    toggle () {
      const activeValue = this.$attrs['active-value'] ? this.$attrs['active-value'] : true
      const inactiveValue = this.$attrs['inactive-value'] ? this.$attrs['inactive-value'] : false
      this.$emit('input', this.isActive ? inactiveValue : activeValue)
    }
  }
}
</script>

<style lang="less" scoped>
.switch {
  position: relative;
  display: inline-block;
  cursor: pointer;
  .switch__text {
    position: absolute;
    height: 1em;
    line-height: 1em;
    left: 1.5em;
    font-size: 0.7em;
    z-index: 999;
    top: 0.3em;
    color: #cccccc;
    &--active {
      left: 0.3em;
      color: #ffffff;
    }
  }
}
</style>
