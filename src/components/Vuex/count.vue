<template>
  <div class="container">
    <h2 style="color: red;">count: {{ count }}</h2>

    <!-- 1. 增加 input 可以設定數值 model 綁定 num -->
    Set Number:
    <input type='number' v-model='num' style="width: 50px;"><br/>

    <!-- 3. 雙向綁定 num 到按鈕上顯示-->
    <!-- 傳 num 數值給 action -->
    <button @click="actionIncrease(num)">+{{ num }}</button>
    <button @click="actionDecrease(num)">-{{ num }}</button>

    <!-- 4. 新增歸零按鈕 -->
    <button @click="actionCountReset">歸零</button>
  </div>
</template>

<script>
// 引用 vuex
// mapActions 在 computed 中使用，提取 action 函式的方法，使用函式名稱
// mapGetters 在 methods 中使用，提取 getter 函式的方法，可以利用物件 key: value 方式取別名
import { mapGetters, mapActions } from 'vuex'

export default {
  // name: 'Firebase',
  data () {
    return {
      // 2. model num 預設值為: 1
      num: 1
    }
  },
  computed: {
    // ...mapGetters 為 ES7 寫法
    ...mapGetters({
      // getCount return value 將會存在別名為 count 的 data 上
      count: 'getCount'
    })
  },
  methods: {
    ...mapActions([
      'actionIncrease',
      'actionDecrease',

      // 5. 引入歸零 action
      'actionCountReset'
    ]),
    // 其他 method call action 的方法
    callAction () {
      // example
      // this.actionIncrease
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
