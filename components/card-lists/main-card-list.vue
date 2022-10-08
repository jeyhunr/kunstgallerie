<template>
  <div class="main-card-list">
    <p class="object-count">{{ countOfPosts }} Objekte geladen</p>
    <div class="list">
      <MainCard v-for="post in posts" :key="post.id" :post="post" />
    </div>
    <div class="more-buttons">
      <Button @click=loadMoreEight><span class="link-button">8 weitere laden</span></Button>
      <Button @click=loadMoreTwenty><span class="link-button">20 weitere laden</span></Button>
      <!-- <LinkButton title="8 weitere laden" @click="loadMoreEight" />
      <LinkButton title="20 weitere laden" @click="loadMoreTwenty" /> -->
    </div>
  </div>
</template>

<script>
import MainCard from "@/components/cards/main-card.vue";
import LinkButton from "@/components/buttons/link-button.vue";

export default {
  props: {
    posts: { required: true },
    loadEightPosts: { type: Function },
    loadTwentyPosts: { type: Function },
    countOfPosts: { type: Number },
  },

  name: "main-card-list",
  components: {
    MainCard,
    LinkButton,
  },
  data() {
    return {};
  },
  methods: {
    loadMoreEight() {
      this.loadEightPosts()
    },
    loadMoreTwenty() {
      this.loadTwentyPosts()
  
    }
  }
};
</script>

<style>
.list {
  display: flex;
  padding: 0px;
  gap: 10px;
  flex-wrap: wrap;
}
.object-count {
  font-weight: 400;
  font-size: 17px;
  line-height: 115%;
  margin-bottom: 60px;
}
.main-card-list {
  padding: 0px 0px 60px 182px;
  display: flex;
  flex-direction: column;
  position: relative;
}
.more-buttons {
  position: absolute;
  bottom: 0;
  width: 1258px;
  text-align: center;
}

@media only screen and (max-width: 1200px) {
  .more-buttons {
    width: auto;
  }
  .main-card-list {
    padding-left: 0;
  }
}
</style>
