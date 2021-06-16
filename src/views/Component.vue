<template>
  <div id="app" class="hello">
    <h1>{{ msg }}</h1>
    <sugar-component v-for="(item, index) in seasonings" v-bind:name="item" :key='index'/>
    <!-- 
    <sugar-component name='SUGAR'/>
    <sugar-component name='SALT'/>
    <sugar-component name='PEPPER'/> 
    -->
  </div>
</template>


<script lang="ts">
import { Options, Vue } from "vue-class-component"
import SugarComponent from "@/components/SugarComponent.vue"; // @ is an alias to /src

export type DataType = {
  msg: string
  seasonings: string[]
}

@Options({
  components: {
    SugarComponent,
  },
})
export default class ComponentPage extends Vue {
  data(): DataType{
    return {
      msg: 'Component Page',
      seasonings: ['Sugar', 'Chilli Pepper', 'Salt', 'Vanilla']
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
