<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div id="tween-max">
      <p>number is ... {{ animeNumber }}</p>
      <input v-model.number="myNumber" type="number">
    </div>
    <br/>
    <p> left.... {{restSec}} </p>
    <button v-on:click="startTimer">Start</button>
    <br/>
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
    <br/>
    <div id="computed">
      <input v-model.number="price" type="number">円<br/>
      <div>Tax included price: <div v-bind:style="{color:computedColor}">{{sum}} 円 </div></div>
    </div>
    <br/>
    <div id="monitor">
      <textarea v-model="inputText"></textarea>
      <p>forbidden words: {{ forbiddenWord }} </p>
    </div> 
  </div>
</template>


<script lang="ts">
import { Vue } from "vue-class-component"
import { TweenMax } from "gsap"

const line = (): void => {
  alert('Good!')
}

export type DataType = {
  msg: string
  count: number
  visible: false
  myArray: string[]
  prefecture: string
  price: number
  forbiddenWord: string
  inputText: string
  restSec: number
  timerObj: any
  myNumber: number
  tweenedNumber: number
}


export default new Vue({
  data(): DataType{
    return {
      msg: 'Operation Page',
      count:0,
      visible: false,
      myArray: ["Saitama", "Kanagawa", "Tokyo"],
      prefecture: '',
      price: 0,
      forbiddenWord: '死',
      inputText:'',
      restSec: 10,
      timerObj: null,
      myNumber: 0,
      tweenedNumber: 0,
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
    },
    startTimer(): void {
      this.restSec = 10
      this.timeObj = setInterval(() => { this.restSec--}, 1000)
    }
  },

  computed: {
    sum(): number {
      return this.price * 1.1
    },
    computedColor(): string {
      if(this.price > 100000) {
        return "red"
      }
      if(this.price > 50000) {
        return "blue"
      }
      if(this.price > 10000) {
        return "green"
      }
      return "black"
    },
    animeNumber(): any{
      return this.tweenedNumber.toFixed(0)
    }
  },

  watch: {
    inputText(): void {
      console.log('watch:inputText ' + this.inputText)
      const pos = this.inputText.indexOf(this.forbiddenWord)
      if(pos >=0){
        alert('you cannot use ' + this.forbiddenWord)
        this.inputText = ''
      }
    },
    restSec(): void {
      if(this.restSec === 0) {
        alert('Time is Up!!')
        clearInterval(this.timerObj)
        this.timerObj = null
      }
    },
    myNumber(): void {
      TweenMax.to(this.$data, 1, {tweenedNumber: this.myNumber})
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
