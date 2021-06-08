<template>
  <div class="container">
    <div class="row">
      <div
        v-for="content of contents"
        :key="content.id"
        v-if="content.active == true"
        class="card"
        style="width: 18rem; margin: 15px 15px"
      >
        <div class="card-body">
          <h5 class="card-title">{{ content.title }}</h5>
          <p class="card-text">
            {{ content.content.slice(0, 25) }}
          </p>
          <NuxtLink
            :to="`/content/${content.id}`"
            class="btn btn-primary btn-sm btn-block"
            >İNCELE</NuxtLink
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      contents: [],
    };
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