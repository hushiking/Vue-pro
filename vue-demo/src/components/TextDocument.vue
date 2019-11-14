<template>
  <div>
    <input type="text" v-model="tit">
    <textarea v-model="msg"></textarea>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    content: String
  },
  data() {
    return {
      tit: this.title,
      msg: this.content
    }
  },
  watch: {
    tit(newVal) {
      this.$emit('update:title', newVal)
    },
    msg(newVal) {
      this.$emit('update:content', newVal)
    }
  }
}
</script>

<style>

</style>