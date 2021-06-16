<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <label><input type="checkbox" v-model="isOK">Switch</label>
    <transition>
      <p v-if="isOK">Animation</p>
    </transition>
  </div>
</template>


<script lang="ts">
import { Vue } from "vue-class-component"

export type DataType = {
  msg: string
  isOK: boolean
}


export default new Vue({
  data(): DataType{
    return {
      msg: 'CSS Page',
      isOK: false
    }
  },

  methods: {
  },
})
</script>


<style>

/* appearing, disappearing */
.v-enter-active, .v-leave-active {
  transition: 0.5s;
}

/* before appearing, after appearing*/
.v-enter, .v-leave-to {
  opacity: 0;
  transform: translateY(20px)
}

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
