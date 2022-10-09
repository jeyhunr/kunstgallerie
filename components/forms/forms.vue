<template>
  <form @submit.prevent="submit" :event="event" :action="action" :method="method" class="form">
    <slot></slot>
  </form>
</template>

<script>
export default {
  name: "Form",
  components: {},
  props: ["method", "action", "event"],
  methods: {
    submit() {
      this.$emit(this.$props['event']);
    },
  },
};
</script>

<style>
.form {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}
.w-100 {
  width: 100%;
  text-align: center;
}
</style>
