<template>
  <form class="form-container" @submit.prevent="onSubmit" @change="onSubmit">
    <h3>Высота и ширина стены:</h3>
    <label for="wallHeight">Высота Стены:</label>
    <input id="wallHeight" v-model="wallHeight" type="number" />
    <br />
    <label for="wallWidth">Ширина Стеры:</label>
    <input id="wallWidth" v-model="wallWidth" type="number" />
    <br />
    <input class="button" type="submit" value="Submit" />
  </form>
</template>

<script>
export default {
  name: "Logo",
  props: {
    wallData: Object,
  },
  data() {
    return {
      wallHeight: this.wallData.wallHeight,
      wallWidth: this.wallData.wallWidth,
    };
  },
  methods: {
    onSubmit() {
      this.$emit("updateData", {
        wallHeight: this.wallHeight,
        wallWidth: this.wallWidth,
      });
    },
  },
};
</script>
<style scoped>
h3 {
  font-size: 20px;
  margin: 20px;
}

input {
  width: 100%;
  height: 30px;
  margin-bottom: 10px;
}

label {
  font-size: 20px;
  margin-bottom: 5px;
}

.button {
  background-color: #39495c;
  border-radius: 5px;
  font-size: 18px;
  height: 40px;
  color: white;
  width: 100%;
  box-shadow: inset 0 -0.6em 1em -0.35em rgba(0, 0, 0, 0.17),
    inset 0 0.6em 2em -0.3em rgba(255, 255, 255, 0.15),
    inset 0 0 0em 0.05em rgba(255, 255, 255, 0.12);
  text-align: center;
  cursor: pointer;
}

.form-container {
  display: flex;
  flex-direction: column;
  width: 50%;
  padding: 20px;
  margin-right: 10px;
  background-color: white;
  border-radius: 20px 5px 5px 5px;
  border: 2px solid lightskyblue;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
}
</style>
