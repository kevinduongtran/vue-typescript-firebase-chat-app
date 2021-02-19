<template>
    <div class="feed w-100 bg-dark rounded-lg text-success">
        Feed
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
@Component
export default class Feed extends Vue {}
</script>

<style lang="scss">
.feed {
  min-height: 300px;
}
</style>
