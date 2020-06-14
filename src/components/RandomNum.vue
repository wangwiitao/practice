<template>
  <div id="app">
    <button @click="add">添加元素</button>
    <button @click="random">打乱顺序</button>
    <hr>
    <transition-group>
      <span class = "line" v-for="item in numlist" :key="item">{{item}}</span>
    </transition-group>
    <hr>
    <button @click = "matrix">矩阵</button>
    <transition-group class = "matrix">
      <span v-for="value in cent" :key="value.index">{{value.item}}</span>
    </transition-group>
  </div>
</template>

<script>
export default {
  name: 'RandomNum',
  data () {
    return {
      numlist: [1, 2, 3, 4, 5],
      cent: new Array(100).fill(0).map((item, index) => ({ index, item: index % 10 }))
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
    },
    matrix () {
      this.cent.sort(() => Math.random() - 0.5)
    }
  }
}
</script>

<style lang = "scss">
    #app{
        .line{
            display:inline-block;
            padding:0 20px;
            transition:all 1s;
        }
        .matrix{
          width: 300px;
          height: 300px;
          border: 1px solid #ccc;
          display:flex;
          flex-wrap:wrap;
          span{
            display:inline-block;
            width: 30px;
            height: 30px;
            border: 1px solid #ccc;
            box-sizing: border-box;
            font-size: 18px;
            text-align:center;
            line-height: 30px;
            transition:all 1s;

          }
        }
    }
</style>
