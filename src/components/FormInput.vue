<template>
  <div class="upload-container">
    <div class="img">
      <Loading v-if="file.downloading" />
      <img
        v-else-if="file.downloadSuccess"
        class="upload-image"
        src="../assets/ok.svg"
      />
      <img v-else class="upload-image" src="../assets/upload.svg" />
    </div>
    <div class="input-field">
      <input
        :id="file.inputId"
        type="file"
        :name="file.inputId"
        :ref="file.inputId"
        @change="onChangeHanlder"
      />
      <label v-if="!file.downloading" :for="file.inputId">
        {{ file.file ? file.file : file.label }}
      </label>
      <label v-else> ... </label>
    </div>
  </div>
</template>
<script>
import Loading from "@/components/Loading";

export default {
  name: "input-field",
  props: ["file"],
  components: {
    Loading,
  },
  methods: {
    onChangeHanlder() {
      const downloadedFile = this.$refs[this.file.inputId].files[0];
      this.$emit("changeHandler", this.file.fieldName, downloadedFile);
    },
  },
  computed: {
    fileName() {
      return this.file.file;
    },
  },
};
</script>

<style lang="scss">
.input-field {
  width: 100%;

  div {
    position: relative;
    z-index: 10;
  }

  input[type="file"] {
    width: 0.1px;
    height: 0.1px;
    opacity: 0;
    position: absolute;
    z-index: -10;

    &:focus {
      outline: none;
    }
  }
}

label {
  display: block;
  padding: 20px;
  padding-left: 90px;
  cursor: pointer;
  text-overflow: ellipsis;
  overflow: hidden;
  width: 100%;
  white-space: nowrap;
}
</style>