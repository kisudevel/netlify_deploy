<script setup>
import { onBeforeMount, ref } from "vue";

const posts = ref(null);
onBeforeMount(() => {
  fetch(`${import.meta.env.VITE_API_URL}/posts`)
    .then((response) => response.json())
    .then((data) => {
      console.log(data);
      posts.value = data;
    })
    .catch((error) => {
      console.error("Error fetching data:", error);
    });
});
</script>
<template>
  <h1>About</h1>
  <pre>{{ posts }}</pre>
</template>
<style scoped></style>
