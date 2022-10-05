

<template>
  <div class="form-container">
    <form @submit.prevent="onSubmit">
      <h3>Дверные проёмы:</h3>
      <label for="doorHeight">Высота:</label>
      <input id="doorHeight" v-model="doorHeight" type="number" />
      <br />
      <label for="doorWidth">Ширина:</label>
      <input id="doorWidth" v-model="doorWidth" type="number" />
      <br />
      <input class="button" type="submit" value="Submit" />
    </form>
    <ol v-if="doorsArr.length">
      <li v-for="{ id, width, height } in doorsArr" :key="id">
        <div>дверь {{ width }} x {{ height }}</div>
        <button @click="deleteDoor(id)">удалить</button>
      </li>
    </ol>
  </div>
</template>

<script>
import { nanoid } from "nanoid";
export default {
  name: "DorWayForm",
  props: {
    doorsArr: Array,
  },
  data() {
    return {
      doorHeight: 900,
      doorWidth: 600,
    };
  },
  methods: {
    onSubmit() {
      this.$emit("newDoor", {
        id: nanoid(10),
        height: this.doorHeight,
        width: this.doorWidth,
        area: this.doorHeight * this.doorWidth,
      });
    },
    deleteDoor(id) {
      this.$emit("deleteDoor", id);
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

li {
  display: flex;
  justify-content: space-around;
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
  /* justify-content: center; */
  /* align-items: center; */
  width: 50%;
  padding: 20px;
  margin-left: 10px;
  background-color: white;
  border-radius: 5px 20px 5px 5px;
  border: 2px solid lightskyblue;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
}
</style>
