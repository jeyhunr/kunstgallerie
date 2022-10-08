<template>
  <div class="footer">
    <h3>&copy; {{ year }} - {{ author }}</h3>
  </div>
</template>

<script>
export default {
  name: "Footer",
  data() {
    return {
      year: new Date().getFullYear(),
      author: "Jeyhun Rahimli",
    };
  },
};
</script>

<style>
.footer {
  position: absolute;
  bottom: 0;
  text-align: center;
  left: 50%;
  transform: translate(-50%, 0%);
}
</style>
