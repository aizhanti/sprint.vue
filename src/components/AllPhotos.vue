<template>
  <div>
    <!-- <img src="https://images.unsplash.com/photo-1494253109108-2e30c049369b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80"> -->
    <img
      :src="photo"
      width="400"
      height="200"
      @click="$emit('getphoto',photo)"
    />
  </div>
</template>

<script>
export default {
  name: "AllPhotos",
  props: ["photo", "getphoto"]
};
</script>
<style></style>
