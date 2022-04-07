<template>
  <div class="container">
    <button @click="onClick" :style="{ background: color }" class="btn">
      {{ text }}
    </button>
  </div>
</template>

<script>
export default {
  name: "ButtonItem",
  props: {
    text: String,
    color: String,
  },
  methods: {
    onClick() {
      this.$emit("btn-click");
    },
  },
};
</script>

<style>
.btn {
  border: none;
  padding: 0.75rem 1rem;
  color: #fff;
  border-radius: 5px;
}
</style>
