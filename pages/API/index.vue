<template>
    <div class="api-page">
        <MainHeader :title=title />
        <hr />
    </div>
</template>

<script>
import MainHeader from "@/components/headers/main-header.vue";
export default {
  components: {
    MainHeader,
  },
  data() {
    return {
      title: "API",
    };
  },
};
</script>