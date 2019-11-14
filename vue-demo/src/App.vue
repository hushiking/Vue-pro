<template>
  <div id="app">
    <input type="text" v-model="msg">
    <input type="text" :value="msg" @input="handleChange">
    {{msg}}
    <div :id="msg"></div>
    <todo-list>
      <!-- vue2.5之前的语法 -->
      <todo-item @delete="handleDel" v-for="item in list" :key="item.title" id="my" data-test="test" :title="item.title" :del="item.del">
        <span slot="pre-icon">前置图标</span>
        <span slot="suf-icon">后置图标</span>
      </todo-item>
      <!-- vue2.6 -->
      <todo-item @delete="handleDel" v-for="(item, index) in list" :key="index" id="my" data-test="test" :title="item.title" :del="item.del">
        <template v-slot:pre-icon="{value}">
          <span>前置图标 {{value}}</span>
        </template>
        <!-- <template v-slot:suf-icon>
          <span>后置图标</span>
        </template> -->
      </todo-item>
    </todo-list>
    <br>
    <base-checkbox v-model="val"></base-checkbox>{{val}}
    <br>
    <text-document v-bind.sync="doc"></text-document>{{doc.title}} - {{doc.content}}
  </div>
</template>

<script>
  // import TodoList from './components/TodoList.vue'
  import TodoItem from './components/TodoItem.vue'
  import BaseCheckbox from './components/BaseCheckbox.vue'
  import TextDocument from './components/TextDocument.vue'

  export default {
    name: 'app',
    components: {
      // TodoList,
      TodoItem,
      BaseCheckbox,
      TextDocument
    },
    data() {
      return {
        doc: {
          title: 'area',
          content: 'text'
        },
        val: true,
        msg: 'hello',
        list: [{
          title: 'zu1',
          del: false
        }, {
          title: 'zu2',
          del: true
        }, {
          title: 'zu3',
          del: true
        }]
      }
    },
    methods: {
      handleChange(e) {
        this.msg = e.target.value
      },
      handleCheck(val) {
        this.val = val
      },
      handleDel(val, e) {
        // eslint-disable-next-line
        console.log('handleDel', val, e)
      },
    }
  }
</script>