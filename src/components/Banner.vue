<template>
  <div>
    <nav class="navbar navbar-light bg-dark align-middle rounded-lg p-3">
      <div class="float-left"><h2 class=" text-light mb-0">Not Slack</h2></div>
      <div class="mx-auto align-middle">
        <h2 class="text-light mb-0">
          <b-icon-chat-right-dots></b-icon-chat-right-dots>
        </h2>
      </div>
      <div class="float-right">
          <auth-modal/>
      </div>
    </nav>
    
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import AuthModal from "./AuthModal.vue";

@Component({ components: { AuthModal } })
export default class Banner extends Vue {

}
</script>
