<template>
  <div class="form-wrapper">
    <div class="title">Подтверждение аккаунта</div>
    <p class="description">
      Для подтверждения вашего аккаунта вам нужно заполнить все поля,
      подтвердить почтовый ящик и телефон, а также загрузить сканы ваших
      документов.
    </p>
    <form-input :file="docPhoto" @changeHandler="handleDownloadFile" />
    <form-input :file="docReg" @changeHandler="handleDownloadFile" />
  </div>
</template>

<script>
import FormInput from "@/components/FormInput";
export default {
  name: "app-form",
  components: {
    FormInput,
  },
  data() {
    return {
      docPhoto: {
        file: "",
        fieldName: "docPhoto",
        downloading: false,
        inputId: "file_input_photo",
        label: "Загрузить скан страницы с фотографией",
        downloadSuccess: "",
      },
      docReg: {
        file: "",
        fieldName: "docReg",
        downloading: false,
        inputId: "file_input_reg",
        label: "Загрузить скан страницы с регистрацией",
        downloadSuccess: "",
      },
    };
  },
  methods: {
    handleDownloadFile(field, downloadedFile) {
      this[field].file = downloadedFile.name;
      this[field].downloading = true;
      this[field].downloadSuccess = false;
      setTimeout(() => {
        this[field].downloading = false;
        this[field].downloadSuccess = true;
      }, 1000);
    },
  },
};
</script>

<style lang="scss">
.form-wrapper {
  width: 540px;
  margin: 0 auto;
  text-align: left;
}

.title {
  font-size: 22px;
  margin-bottom: 20px;
}

.description {
  font-size: 13px;
  color: #666;
}

.upload-container {
  position: relative;
  display: flex;
  align-items: center;
  width: 100%;
  height: 80px;

  .img {
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    left: 0;
    background: #fff;
    padding: 10px;
    width: 36px;
    height: 36px;
  }
}
</style>