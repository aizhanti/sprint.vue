<template>
     <div>
      <button
        className="button"
        @click="chooseFiles()"
      >
        UPLOAD
        <input
          id="fileUpload"
          type="file"
          accept="image/gif, image/jpeg, image/png"
          @change="uploadImg"
        ></input>
      </button>
    </div>
</template>

<script>
import { saveObject } from "../../utils/index.js";

export default {
  name: "Upload",
  methods: {
    chooseFiles() {
        document.getElementById("fileUpload").click()
    },
    uploadImg(e) {
      saveObject(e.target.files[0]);
      alert("Image Uploaded Successfully");
   },
  }
};
</script>

<style></style>


