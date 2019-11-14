<template>
  <input type="checkbox" :checked="checked" @change="$emit('change', $event.target.checked)">
</template>

<script>
  export default {
    // 告诉vue底层, v-model 是哪个属性和哪个事件的简写方式
    model: {
      prop: 'checked',
      event: 'change'
    },
    props: {
      checked: Boolean
    },
    methods: {
      handleChange() {
        this.$emit('change', this.checked)
      }
    }
  }
</script>

<style>

</style>