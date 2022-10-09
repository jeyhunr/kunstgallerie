<template>
  <div class="form-input">
    <label class="form-input-label" :for="name">{{ label }}</label>
    <input
      :id="name"
      :type="type"
      :name="name"
      :placeholder="placeholder"
      :required="required"
      :value="value"
      class="form-input-field"
      @input="$emit('input', $event.target.value)"
    />
  </div>
</template>
<script>
export default {
  name: "TextInput",
  props: ["name", "type", "placeholder", "label", "required", "value"],
  methods: {},
};
</script>
<style>
.form-input {
  width: 25%;
  display: flex;
  flex-direction: column;
}
.form-input-field {
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  line-height: 1.5;
  color: #212529;
  background-color: #fff;
  border: 1px solid #ced4da;
  border-radius: 5px;
}
</style>
