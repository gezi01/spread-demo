<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div>
      <button @click="btn(0)">spread总</button>
      <button @click="btn(1)">time</button>
    </div>
    <spread v-if="show"></spread>
    <spread-time v-if="timeShow"></spread-time>
  </div>
</template>

<script>
  import Spread from './spread'
  import SpreadTime from './spread-time'
export default {
  name: 'HelloWorld',
  components:{
    Spread,
    SpreadTime
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      show:false,
      timeShow:false,
    }
  },
  methods:{
    btn(val){
      if(val === 0){
        this.show = !this.show
        this.timeShow = false
      } else {
        this.timeShow = !this.timeShow
        this.show = false
      }
    },

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  button{
    outline: none;
    width: 100px;
    height: 30px;
    background-color: #00AFF0;
    color: #fff;
    font-size: 16px;
    text-align: center;
    border: none;
    border-radius: 10px;
    float: left;
    margin-left: 20px;
  }
  .hello{
    display: flex;
    flex-direction: column;
  }
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
