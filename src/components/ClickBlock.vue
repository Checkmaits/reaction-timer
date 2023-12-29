<template>
  <div @click="handleClick" :class="{ hidden: !show }" class="click-block bg-primary shadow"></div>
</template>

<script>
export default {
  name: "ClickBlock",
  props: ["delay"],
  data() {
    return {
      show: false,
      startTime: null,
    };
  },
  methods: {
    handleClick() {
      const endTime = Date.now();
      const time = endTime - this.startTime;
      this.$emit("handleClick", time);
    },
  },
  mounted() {
    setTimeout(() => {
      // move block
      const block = document.querySelector(".click-block");
      const x = Math.floor(Math.random() * 91);
      const y = Math.floor(Math.random() * 91);
      block.style.top = y + "%";
      block.style.left = x + "%";

      // show block
      this.show = true;

      // start timer
      this.startTime = Date.now();
    }, this.delay);
  },
};
</script>

<style scoped>
.click-block {
  position: absolute;
  width: 90px;
  height: 90px;
  border-radius: 50%;
}

.click-block:hover {
  cursor: pointer;
}

.click-block:active {
  transform: scale(0.9);
}

.hidden {
  display: none;
}
</style>
```
