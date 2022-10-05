

<template>
  <div>
    <input @click="onClick" class="button" type="submit" :value="label" />
  </div>
</template>

<script>
export default {
  name: "Button",
  props: {
    label: String,
  },
  methods: {
    onClick(id) {
      this.$emit("onClick", id);
    },
  },
};
</script>
<style scoped>
div {
  display: flex;
  justify-content: center;
  align-items: center;
}
.button {
  margin-top: 5px;
  border-radius: 5px;
  font-size: 18px;
  height: 40px;
  min-width: 280px;
  cursor: pointer;
  color: white;
  background-color: dodgerblue;
}
</style>
