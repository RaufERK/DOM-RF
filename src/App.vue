<template>
  <div class="main">
    <div class="content-container">
      <h1>Калькулятор ПГП</h1>
      <div class="forms-container">
        <WallForm
          @updateData="updateWall"
          :wallData="{ wallHeight, wallWidth }"
        />
        <DorWayForm
          @new-door="newDoor"
          @deleteDoor="deleteDoor"
          :doorsArr="doors"
        />
      </div>
      <DisplayAndCalc :allData="{ wallHeight, wallWidth, doors }" />
    </div>
  </div>
</template>

<script>
import WallForm from "./components/WallForm.vue";
import DorWayForm from "./components/DorWayForm.vue";
import DisplayAndCalc from "./components/DisplayAndCalc.vue";

export default {
  name: "App",
  components: {
    WallForm,
    DisplayAndCalc,
    DorWayForm,
  },
  data() {
    return {
      wallHeight: 10000,
      wallWidth: 6000,
      doors: [],
    };
  },
  methods: {
    updateWall({ wallHeight, wallWidth }) {
      this.wallHeight = wallHeight;
      this.wallWidth = wallWidth;
    },
    newDoor(doorArea) {
      this.doors.push(doorArea);
    },
    deleteDoor(deleteId) {
      this.doors = this.doors.filter(({ id }) => deleteId !== id);
    },
  },
  computed: {
    numberOfPlates() {
      return Math.random();
    },
    wallWeight() {
      return Math.random();
    },
  },
};
</script>

<style>
h1 {
  font-weight: 900;
  text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.25);
}
.main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100w;
}
.content-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.forms-container {
  display: flex;
  justify-content: center;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin: -10px;
  padding: -10px;
  background-color: cyan;
}
</style>
