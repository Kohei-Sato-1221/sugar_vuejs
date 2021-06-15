<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button v-on:click="countUp">Click</button>
    <p>{{ count }}</p>
    <p v-if="visible">たくさんカウントアップされました！</p>
    <br/>
    <div id="array">
      <ul>
        <li v-for="(value, key) in myArray" v-bind:key="key">{{ value }}</li>
      </ul>
      <input v-model="prefecture" placeholder="prefacture">
      <button v-on:click="add">add</button>
    </div>
  </div>
</template>


<script lang="ts">
import { Vue } from "vue-class-component";

const line = () => {
  alert('Good!')
}

export type DataType = {
  msg: string
  count: number
  visible: false
  myArray: string[]
  prefecture: string
}


export default new Vue({
  data(): DataType{
    return {
      msg: 'Operation Page',
      count:0,
      visible: false,
      myArray: ["Saitama", "Kanagawa", "Tokyo"],
      prefecture: ''
    }
  },

  methods: {
    countUp(): void {
      const newCount = this.count++
      if (newCount > 5) {
        this.visible = true       
      }
      if (newCount < 1) {
        line()
      }
    },
    add(): void {
      if(this.prefecture){
        this.myArray.push(this.prefecture)
      }
    }
  }
})


</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.my-class {
  background-color: #42b983;
}
</style>
