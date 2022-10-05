<template>
  <div class="container">
    <h3>Высота и ширина стены:</h3>
    <InputNumberVue
      @onChange="onHeightChange"
      :value="wallHeight"
      label="Высота Стены:"
    />
    <InputNumberVue
      @onChange="onWidthChange"
      :value="wallWidth"
      label="Ширина Стены:"
    />
    <Button @onClick.prevent="onSubmit" label="Ввод" />
  </div>
</template>

<script>
import Button from "../shared/Button.vue";
import InputNumberVue from "../shared/Input.number.vue";
export default {
  name: "WallForm",
  components: { Button, InputNumberVue },
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
    onHeightChange(param) {
      this.wallHeight = param;
    },
    onWidthChange(param) {
      this.wallWidth = param;
    },
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

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 50%;
  margin: 0 10px 10px 0;
  padding: 20px;
  background-color: white;
  border-radius: 50px 5px 5px 5px;
  border: 5px solid lightskyblue;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
}
</style>
