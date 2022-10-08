<template>
  <div class="kunstgallerie-page">
    <div class="outer-container">
      <div class="inner-container">
        <MainHeader :title="title" />
        <hr />
        <MainCardList
          :posts="fetchedPosts"
          :loadEightPosts="loadEightPosts"
          :loadTwentyPosts="loadTwentyPosts"
          :countOfPosts="countOfPosts"
        />
      </div>
    </div>
  </div>
</template>

<script>
import MainHeader from "@/components/headers/main-header.vue";
import MainCardList from "@/components/card-lists/main-card-list.vue";

export default {
  components: {
    MainHeader,
    MainCardList,
  },
  data() {
    return {
      title: "Kunstgallerie",
      fetchedPosts: [],
      countOfPosts: 8,
    };
  },
  async created() {
    const getPosts = await this.getPosts(this.countOfPosts);
  },
  methods: {
    async loadEightPosts() {
      this.countOfPosts += 8;
      const getPosts = await this.getPosts(this.countOfPosts);
    },
    async loadTwentyPosts() {
      this.countOfPosts += 20;
      const getPosts = await this.getPosts(this.countOfPosts);
    },
    async getPosts(countOfPosts) {
      const api =
        "https://jsonplaceholder.typicode.com/photos?_start=0&_limit=" +
        this.countOfPosts;
      const response = await fetch(api);
      const posts = await response.json();
      this.fetchedPosts = posts;
    },
  },
};
</script>

<style scoped>
.kunstgallerie-page {
  width: 100%;
}
.outer-container {
  padding: 0px 0px 70px;
  position: relative;
  width: 100%;
  background: #ffffff;
}
.inner-container {
  display: flex;
  flex-direction: column;
  padding: 0px;
  width: 100%;
}
hr {
  height: 1px;
  border: none;
  width: 100%;
  background: #d9d9d9;
}
</style>
