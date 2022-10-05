<template>
  <div class="container">
    <h3>Дверные проёмы:</h3>
    <InputNumberVue
      @onChange="onHeightChange"
      :value="doorHeight"
      label="Высота двери:"
    />
    <InputNumberVue
      @onChange="onWidthChange"
      :value="doorWidth"
      label="Ширина двери:"
    />
    <Button @onClick.prevent="onSubmit" label="Ввод" />
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
import Button from "../shared/Button.vue";
import InputNumberVue from "../shared/Input.number.vue";
export default {
  name: "DorWayForm",
  components: { Button, InputNumberVue },
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
    onHeightChange(param) {
      this.doorHeight = param;
    },
    onWidthChange(param) {
      this.doorWidth = param;
    },
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

li {
  display: flex;
  justify-content: space-around;
  margin: 10px;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 50%;
  margin: 0 0 10px 10px;
  padding: 20px;
  background-color: white;
  border-radius: 5px 50px 5px 5px;
  border: 5px solid lightskyblue;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
}
</style>
