<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input v-model.lazy="myName" placeholder="your name">
    <p>My name is {{myName}}.</p>
    <br/>
    <textarea v-model="textmsg"></textarea> 
    <p>Number of characters is {{textmsg.length}}.</p>
    <br/>
    <div class="check-list">
      <label><input type="checkbox" value="red" v-model="myChecks">Red</label><br/>
      <label><input type="checkbox" value="blue" v-model="myChecks">Blue</label><br/>
      <label><input type="checkbox" value="green" v-model="myChecks">Green</label><br/>
     {{ myChecks.length === 0 ? 'No item selected' : 'Selected are ' + myChecks }}.
    </div>
    <br/>
    <div>
      <label><input type="checkbox" v-model="myAgree">I agree.</label><br/>
      <button v-bind:disabled="myAgree==false">Submit</button>
    </div>
    <br/>
    <div>
      <label><input type="radio" value="male" v-model="sex">Male</label><br/>
      <label><input type="radio" value="female" v-model="sex">Female</label><br/>
      I am {{sex}}.
    </div>
    <br/>
    <div>
      <p>What's today's dinner?</p>
      <select v-model="dinner">
        <option>Hitsumabushi</option>
        <option>Taiwanese soupless noodle</option>
        <option>Chicken wings</option>
      </select>
      <p>I'm looking forward to {{dinner}}!!</p>
    </div>
    <br/>
    <br/>
    <br/>
  </div>
</template>

<script lang="ts">
const favoriteFoods: string[] = ['ramen', 'sushi', 'spagetti']

export default {
  name: 'hello',
  data () {
    return {
      msg: 'Form page',
      myName: '',
      textmsg: '',
      myChecks: [],
      myAgree: false,
      sex:'',
      dinner:'',
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
