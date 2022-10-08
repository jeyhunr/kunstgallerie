<template>
  <button>
    <nuxt-link v-if="link" :to="link" class="link-button">{{ title }}</nuxt-link>
    <span v-else class="link-button">{{ title }}</span>
  </button>
</template>

<script>
export default {
  props: ["link", "title"],
  name: "link-button"
};
</script>

<style>
button {
  padding: 10px 24px 8px;
  width: 167px;
  height: 37px;
  background: #05b7f1;
  border-radius: 100px;
  border:none;
  transition: 0.2s;
}
button:hover {
  box-shadow: 0 1rem 3rem rgba(0,0,0,.175);
  background: rgb(109,32,145);
  cursor: pointer;
  transition: 0.2s;
}
button > .link-button {
  width: 119px;
  height: 19px;
  text-decoration: none;
  font-family: "Rubik";
  font-style: normal;
  font-weight: 600;
  font-size: 15.802px;
  line-height: 115%;
  text-align: center;
  color: #ffffff;
}
</style>
