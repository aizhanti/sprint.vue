<template>
  <div>
     <img :src="selectedPhoto" height="600" width="800" />
  </div>
</template>

<script>
export default {
  name: "SinglePhoto",
  props: ["selectedPhoto"]
};
</script>

<style></style>
