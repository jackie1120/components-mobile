<template>
  <div
    class="switch"
    :style="{'font-size': fontSize}"
    :class="{'switch--active': isActive}"
    @click="toggle"
  >
    <div class="switch__node" :class="{'switch__node--active': isActive}"></div>
    <div v-if="showText" class="switch__text" :class="{'switch__text--active': isActive}">{{ text }}</div>
  </div>
</template>

<script>
export default {
  name: 'ZvSwitch1',
  props: {
    size: {
      type: [Number, String],
      default: '30'
    },
    activeValue: {
      type: [Number, String, Boolean],
      default: true
    },
    inactiveValue: {
      type: [Number, String, Boolean],
      default: false
    },
    activeText: {
      type: String,
      default: '是'
    },
    inactiveText: {
      type: String,
      default: '否'
    },
    value: {
      type: [Number, String, Boolean],
      required: true
    },
    showText: {
      type: Boolean,
      default: true
    }
  },
  computed: {
    fontSize () {
      return this.size + 'px'
    },
    isActive () {
      return this.value === this.activeValue
    },
    text () {
      return this.isActive ? this.activeText : this.inactiveText
    }
  },
  methods: {
    toggle () {
      this.$emit('input', this.isActive ? this.inactiveValue : this.activeValue)
    }
  }
}
</script>

<style lang="less" scoped>
.switch {
  border: 1px solid rgba(0, 0, 0, 0.1);
  background: #ffffff;
  display: inline-block;
  position: relative;
  border-radius: 1em;
  cursor: pointer;
  transition: background-color 0.3s;
  height: 1em;
  line-height: 1em;
  width: 2em;
  box-sizing: content-box;
  &--active {
    background-color: #1989fa;
  }
  .switch__node {
    position: absolute;
    background: #ffffff;
    border-radius: 100%;
    width: 1em;
    height: 1em;
    transition: transform 0.3s;
    box-shadow: 0 3px 1px 0 rgba(0,0,0,.05), 0 2px 2px 0 rgba(0,0,0,.1), 0 3px 3px 0 rgba(0,0,0,.05);
    &--active {
      transform: translateX(1em);
    }
  }
  .switch__text {
    font-size: 1em;
    transform: translateX(1.5em);
    color: #cccccc;
    font-size: 0.7em;
    &--active {
      transform: translateX(0.3em);
      color: #ffffff;
    }
  }
}
</style>
