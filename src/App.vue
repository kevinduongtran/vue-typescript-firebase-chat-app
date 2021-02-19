<template>
  <div id="app">
    <div class="container">
      <banner />
      <!-- <chat/> -->
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { BootstrapVue, IconsPlugin } from "bootstrap-vue";
import HelloWorld from "./components/HelloWorld.vue";
import Banner from "./components/Banner.vue";
import Chat from "./components/Chat.vue";

import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";
Vue.use(BootstrapVue);
Vue.use(IconsPlugin);

@Component({
  components: {
    HelloWorld,
    Banner,
    Chat,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
