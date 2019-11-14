<template>
  <li>
    <slot name="pre-icon" :value="value"></slot>
    <span class="red" v-if="del">{{title}}</span>
    <span v-else style="text-decoration: line-through;">
      {{title}}
    </span>
    <!-- 默认值 -->
    <slot name="suf-icon">🐶🐶</slot>
    <button v-show="!del" @click="handleClick">删除</button>
  </li>
</template>

<script>
  export default {
    props: {
      title: String,
      del: {
        type: Boolean,
        default: false,
      }
    },
    data() {
      return {
        value: Math.random()
      }
    },
    methods: {
      // 原生DOM绑定方法
      handleClick(e) {
        // eslint-disable-next-line
        console.log('点击删除', e)
        this.$emit('delete', this.title, e)
      }
    }
  }
</script>

<style scoped>
  .red {
    color: red;
  }
</style>