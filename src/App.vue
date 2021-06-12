<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1 v-text="msg"></h1>
    <p v-html="htmlMsg"></p>
    <p v-text="htmlMsg"></p>
    <br/>
    <div>{{ 'current age is ' + age}} </div>
    <div>{{ 'in 10 years,  it\'ll be ' + (age + 10)}} </div>
    <div>{{ favoriteFoods }} </div>
    <br/>
    <div class="data">{{ $data }}</div>
    <ul id="example-1">
      <li v-for="(item, key) in $data" :key='key'>
        {{ item }} : {{ key}}
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
const favoriteFoods: string[] = ['ramen', 'sushi', 'spagetti']

export default {
  name: 'hello',
  data () {
    return {
      msg: 'This is sugar project!!!',
      htmlMsg: '<h2>html message!</h2>',
      age: 33,
      favoriteFoods: favoriteFoods
    }
  }
}
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
</style>
