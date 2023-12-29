<template>
  <div class="mb-4">
    <span class="h1 fw-bold display-1">{{ time }}ms</span>
    <p class="text-secondary mb-0">{{ tagline.tag }}</p>
  </div>
</template>

<script>
export default {
  name: "Results",
  props: ["time"],
  computed: {
    tagline() {
      const tags = [
        {
          tag: "God-like reflexes?!",
          min: 0,
          max: 500,
        },
        {
          tag: "You're a ninja!",
          min: 501,
          max: 1000,
        },
        {
          tag: "You're a cat!",
          min: 1001,
          max: 1500,
        },
        {
          tag: "Okay, you can do better.",
          min: 1501,
          max: 3000,
        },
        {
          tag: "Come on, really?",
          min: 3001,
          max: 5000,
        },
        {
          tag: "Are you even alive?",
          min: 5001,
          max: Infinity,
        },
      ];

      return tags.find((tag) => this.time >= tag.min && this.time <= tag.max);
    },
  },
};
</script>
