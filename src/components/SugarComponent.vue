<template>
  <p class="sugar-component">
    {{name}} count:{{count}} <button v-on:click="addOne">Add</button>
  </p>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";

@Options({
  props: {
    name: String,
  },
})
export default class SugarComponent extends Vue {
  name!: string
  count = 0

  addOne(){
    this.count++
  }
}
</script>