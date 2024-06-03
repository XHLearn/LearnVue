<script setup>
import { mounted, ref } from 'vue'

const awesome = ref(true)

function toggle() {
  awesome.value = !awesome.value;
};

mounted(){
  this.$eventBus.$on('keydown', this.handleKeyDown);
};

</script>

<template @keydown.alt.s="toggle">
  <button @click="toggle" @keydown.alt.q="toggle">Toggle</button>
  <h1 v-if="awesome">Vue is awesome!</h1>
  <h1 v-else>Oh nso 😢</h1>
</template>