<template>
  <div class="container" style="padding: 20px">
    <h3>İçerikler</h3>
    <div
      v-for="content of contents"
      :key="content.id"
      class="card"
      style="width: 100%; margin: 15px 0px"
    >
      <div class="card-body">
        <h5 class="card-title">{{ content.title }}</h5>
        <p class="card-text">
          {{ content.content.slice(0, 25) }}
        </p>
        <!--<button
          v-on:click="removeElement(content.id)"
          class="btn btn-danger btn-sm btn-block"
        >
          SİL
        </button> -->
        <button
          @click="deleteContent(content.id)"
          class="btn btn-danger btn-sm btn-block"
        >
          SİL
        </button>
        <NuxtLink
          :to="`/content/${content.id}`"
          class="btn btn-primary btn-sm btn-block"
          >GÜNCELLE</NuxtLink
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      contents: [],
      deleteContentLoading: false
    };
  },
  methods: {
    // removeElement: function (id) {
    //     this.contents = this.contents.filter(e => e.id != id);
    // },
    deleteContent(contentId){
        this.deleteContentLoading = true;
        this.$axios.$delete(`http://localhost:5000/contents/${contentId}`).finally(() =>{
            this.deleteContentLoading = false
        })
    }
  },
  async fetch() {
    this.contents = await fetch("http://localhost:5000/contents").then((res) =>
      res.json()
    );
  },
};
</script>

<style>
</style>