<template>
  <div>
    <label for="inputId">{{ label }}</label>
    <input id="inputId" v-model="valueState" @change="onChange" type="number" />
  </div>
</template>

<script>
export default {
  name: "InputNumber",
  props: {
    label: String,
    value: Number,
  },
  data() {
    return {
      valueState: this.value,
    };
  },
  methods: {
    onChange() {
      this.$emit("onChange", this.valueState);
    },
  },
};
</script>
<style scoped>
label {
  font-size: 20px;
  margin-bottom: 10px;
}

input {
  padding-left: 10px;
  width: 90%;
  height: 30px;
  margin-bottom: 20px;
  border: 3px solid lightskyblue;
  border-radius: 5px;
}
</style>
