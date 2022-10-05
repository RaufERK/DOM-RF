
<template>
  <div class="container">
    <h3>
      Всего блоков нужно: <strong>{{ totalBlocks }}</strong>
    </h3>
    <h3>
      Общий вес стены: <strong>{{ totalWeight }}</strong>
    </h3>
  </div>
</template>


<script>
import { plate } from "../entities/constants";
export default {
  name: "HelloWorld",
  props: {
    wallHeight: Number,
    wallWidth: Number,
    doors: Array,
  },
  data() {
    return {
      plateArea: plate.height * plate.width,
    };
  },
  computed: {
    totalBlocks() {
      const { wallHeight, wallWidth } = this;
      return Math.ceil(
        (wallHeight * wallWidth - this.totalDoorsArea) / this.plateArea
      );
    },
    totalWeight() {
      return this.totalBlocks * plate.weight;
    },
    totalDoorsArea() {
      return this.doors.reduce((acc, el) => acc + el.area, 0);
    },
  },
};
</script>

<style scoped>
h3 {
  font-size: 20px;
  margin: 10px;
}
.container {
  padding-top: 20px;
  padding-bottom: 20px;
  margin: 10px;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border-radius: 5px 5px 50px 50px;
  background-color: white;
  border: 5px solid lightskyblue;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
}

.container:hover {
  box-shadow: 2px 2px 20px rgba(0, 0, 0, 0.2);
}
</style>
