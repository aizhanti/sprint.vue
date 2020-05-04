<template>
  <div class="navbar">
    <h1 class="title">Vuestagram</h1>
    <a class="homeLink" href="">home</a>
    
    <upload />
    
  </div>
</template>

<script>

import Upload from "./Upload";    ////

export default {
  name: "Navbar",
  components : {        ///
    upload : Upload     ///
  },
  data: () => ({                      ///
    //navtitle: "This is the Navbar"  ///
  })                                  ///
};
</script>

<style>
  h1 {
    color: white;
  }
  .NavBackground {
    background-color: cadetblue;
  }

  .navbar {
  padding: 2rem;
  display: flex;
  justify-content: flex-end;
  background-color: #1c7e88;
}

.navbar-header {
  cursor: pointer;
  margin-right: auto;
}
  
.button {
  cursor: pointer;
}

input {
  position: absolute;
  left: -99999999px;
}

button {
  height: 2rem;
}

.homeLink{
  position:absolute;
  left:50px
}

.title{
  position:absolute;
  left: 380px;
  color: white;
}

</style>
