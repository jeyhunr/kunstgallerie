<template>
  <div class="default-layout">
    <div class="main-container">
      <nuxt />
    </div>
    <Footer />
  </div>
</template>

<script>
import Footer from "@/components/footer.vue";
export default {
  name: "Default",
  comments: {
    Footer,
  },
  data() {
    return {};
  },
};
</script>

<style>
.default-layout {
  position: relative;
}
.main-container {
  max-width: 1440px;
  display: flex;
  flex-direction: row;
  padding: 0px 0px 60px;
  position: relative;
  background: #ffffff;
  margin-right: auto;
  margin-left: auto;
  height: 100%;
}
</style>
