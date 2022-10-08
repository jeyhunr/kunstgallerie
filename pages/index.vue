<template>
  <div class="index-page">
    <div class="buttons">
      <h1>Willkommen</h1>
      <LinkButton link="/kunstgallerie" title="Aufgabe" />
      <LinkButton link="/api" title="API" />
    </div>
  </div>
</template>

<script>
import LinkButton from "@/components/buttons/link-button.vue";

export default {
  name: "IndexPage",
  components: {
    LinkButton,
  },
};
</script>

<style>
.index-page {
  height: 100%;
  width: 100%;
  position: relative;
}
.buttons {
  position: absolute;
  left: 50%;
  transform: translate(-50%, 50%);
}
.buttons > h1 {
  text-align: center;
}

@media only screen and (max-width: 768px) {
  .buttons > button {
    margin-bottom: 5px;
  }
  .buttons > h1 {
    text-align: left;
  }
}
</style>
