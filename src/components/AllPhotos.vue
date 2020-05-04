<template>
  <div>
    <!-- <img src="https://images.unsplash.com/photo-1494253109108-2e30c049369b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80"> -->
    <img :src="{photos[0]}" />
  </div>
</template>

<script>
export default {
  name: "AllPhotos",
  props: ["photos"]
};
</script>
<style></style>
