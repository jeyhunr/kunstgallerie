<template>
  <div class="main-header">
    <h1>{{ title }}</h1>
  </div>
</template>

<script>
export default {
  props: ["title"],
  name: "main-header",
};
</script>

<style>
.main-header {
  height: 134px;
  padding: 60px 0px 0px 182px;
}
.main-header > h1 {
  margin: 0px;
  font-weight: 600;
  font-size: 64px;
  line-height: 115%;
  color: #000000;
}
@media only screen and (max-width: 1200px) {
  .main-header {
    padding-left: 0px;
}
}
</style>
