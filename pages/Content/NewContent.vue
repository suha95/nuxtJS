<template>
  <div class="container" style="padding: 50px 0">
    <h3>İçerik Ekle</h3>
    <div class="form">
      <form
        accept-charset="UTF-8"
        v-on:submit.prevent="onSubmit()"
        method="POST"
      >
        <div class="form-group">
          <label>Başlık</label>
          <input
            type="text"
            v-model="title"
            class="form-control"
            placeholder="Başlığı Giriniz."
          />
        </div>
        <div class="form-group">
          <label>İçerik</label>
          <input
            type="text"
            v-model="content"
            class="form-control"
            placeholder="İçeriği Giriniz."
          />
        </div>
        <div class="form-check" style="margin-bottom: 20px">
          <input type="checkbox" class="form-check-inpukt" v-model="active" />
          <label class="form-check-label" for="exampleCheck1">Aktif</label>
        </div>
        <div v-if="isSuccess" class="p-3 mb-2 bg-success text-white">
            İçerik Başarı ile Kaydedildi.
        </div>
        <button type="submit" class="btn btn-success btn-sm btn-block">
          KAYDET
        </button>
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  props: {
    msg: String,
  },
  data() {
    return {
      loading: true,
      title: "",
      content: "",
      active: false,
      isSuccess: false
    };
  },
  methods: {
    onSubmit() {
      let data = {
        title: this.title,
        content: this.content,
        active: this.active
      };
      axios
        .post("http://localhost:5000/contents", data, {
          headers: {
            Accept: "application/json",
          },
        })
        .then(
          (response) => {
            this.isSuccess = response.data.success ? true : false;
          },
          (response) => {
            // Error
          }
        );
    },
  },
};
</script>

<style>
</style>