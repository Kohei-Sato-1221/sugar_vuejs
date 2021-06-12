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
    <hr/>
    <div>データを直接出力</div>
    <div class="data">{{ $data }}</div>
    <hr/>
    <div>
      <div>ループで出力する</div>
      <ul id="loop">
        <li v-for="(item, key) in $data" :key='key'>
          {{ key }} : {{ item}}
        </li>
      </ul>      
    </div>
    <hr/>
    <br/>
    <br/>
    <div class="v-bind-sample">
      <img src="@/assets/logo.png"/>
      <img v-bind:src="logoPath"/>
      <hr/>
      <a href="https://google.co.jp">Direct</a><br/>
      <a v-bind:href="url">Use B-bind</a>
      <hr />
      <div>
        <p align="right">Direct right</p>
        <p v-bind:align="alignLeft">InDirect Left</p>
      </div>
      <div>
        <p 
          v-bind:style="{color:color, fontSize:fontSize, backgroundColor:backgroundColor}"
        >
          v-bind specifying Style
        </p>
        <p v-bind:class="myClass">
          v-bind specifying Class
        </p>
      </div>
    </div>
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
      favoriteFoods: favoriteFoods,
      logoPath: require('@/assets/logo.png'),
      url: "https://google.co.jp",
      alignLeft: 'left',
      color: 'gray',
      fontSize: '20px',
      backgroundColor: 'yellow',
      myClass: 'my-class'
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

.my-class {
  background-color: #42b983;
}
</style>
