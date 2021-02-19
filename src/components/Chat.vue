<template>
  <div>
    <feed />
    <message />
  </div>
</template>

<script lang="ts">

import { Component, Vue } from "vue-property-decorator";
import Feed from "./Feed.vue";
import Message from "./Message.vue";



@Component({
  components: {
    Feed,
    Message,
  },
})
export default class Chat extends Vue {}
</script>
