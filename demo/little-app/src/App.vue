<template>
  <div id="app">
        {{msg}}
        <div>
            <input type="text" v-model="info">
            <button @click="handleClick">Add</button>
            <ul>
                <!-- <li v-for="item in list">{{item}}</li> -->
                <!-- <todo-item v-for="item in list" :key="item" :item="item"></todo-item> -->
                <todo-item v-for="item in list" :key="item" :item="item">
                  <!-- 2.5 引用插槽写法 - 具名插槽 -->
                  <!-- <span slot="todoItem" style="font-size: 20px">{{item}}</span> -->
                  <!-- 2.6 引用插槽写法 - 具名插槽 -->
                  <template v-slot:todoItem>
                    <span style="font-size: 20px">{{item}}</span>                    
                  </template>
                  <!-- 引用插槽写法 - 作用域插槽 -->
                  <template v-solt:item="todoItemProps">
                    <span :style="{fontSize: '20px', color: todoItemProps.checked ? 'origin' : 'green'}"></span>
                  </template>
                </todo-item>
            </ul>
        </div>
	</div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TodoItem from './components/TodoItem.vue'

export default {
  data() {
    return {
        msg: 'Hello Vue!',
        info: '',
        list: [],
    }
  },
  methods: {
    handleClick() {
      var strLength = this.info.replace(/ /g, "").length;
      // alert(strLength);
      // alert(this.info);
      if(typeof this.info == "undefined" || this.info == "" || this.info == null || strLength == 0) {
          alert("信息：" + this.info);
      } else {
          console.log(this.info);
          this.list.push(this.info);
          this.info = '';
      }
    }
  },
  components: {
    HelloWorld,
    TodoItem
  }
}
</script>

<style>
/* #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
