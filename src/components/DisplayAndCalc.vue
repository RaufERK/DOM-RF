
<template>
  <div class="card">
    <p>Всего блоков нужно: {{ totalBlocks }}</p>
    <p>Общий вес стены: {{ totalWeight }}</p>
  </div>
</template>


<script>
import { plate } from "../data/constants";
export default {
  name: "HelloWorld",
  props: {
    allData: Object,
  },
  data() {
    return {
      plateArea: plate.height * plate.width,
      wallHeight: this.allData.wallHeight,
      wallWidth: this.allData.wallWidth,
      doors: this.allData.doors,
    };
  },
  computed: {
    totalBlocks() {
      const { wallHeight, wallWidth, doors } = this;
      const totalDoorsArea = doors.reduce((acc, el) => acc + el.area, 0);
      return Math.ceil(
        (wallHeight * wallWidth - totalDoorsArea) / this.plateArea
      );
    },
    totalWeight() {
      return this.totalBlocks * plate.weight;
    },
  },
};
</script>

<style scoped>
.card {
  padding-top: 20px;
  padding-bottom: 20px;
  margin-top: 20px;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border-radius: 5px 5px 20px 20px;
  background-color: white;
  border: 2px solid lightskyblue;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
}
</style>
