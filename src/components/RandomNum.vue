<template>
  <div id="app">
    <button @click="add">添加元素</button>
    <button @click="random">打乱顺序</button>
    <hr>
    <transition-group>
      <span v-for="item in numlist" :key="item">{{item}}</span>
    </transition-group>
  </div>
</template>

<script>
export default {
  name: 'RandomNum',
  data () {
    return {
      numlist: [1, 2, 3, 4, 5]
    }
  },
  methods: {
    add () {
      this.numlist.splice(this.getLocate(), 0, this.numlist.length + 1)
    },
    random () {
      this.numlist.sort(() => Math.random() - 0.5)
    // 另一种方法：this.numlist.sort(() => Math.random() < 0.5 ? 1 : -1)
    },
    getLocate () {
      return Math.floor(Math.random() * this.numlist.length)
    }
  }
}
</script>

<style lang = "scss">
    #app{
        span{
            display:inline-block;
            padding:0 20px;
            transition:all 1s;
        }
    }
</style>
