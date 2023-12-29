<template>
  <div class="app__wrapper bg-light py-4">
    <div class="app__container py-4">
      <header>
        <div class="text-center">
          <h1 class="fw-bold mb-0">reaction timer</h1>
          <p class="text-secondary mb-0">test your reaction skills</p>
        </div>
      </header>
      <main>
        <ClickBlock v-if="playing" :delay="delay" @handleClick="handleBlockClick" />
        <div v-else class="text-center">
          <div v-if="time">
            <Results :time="time" />
          </div>
          <button @click="play" class="btn btn-primary">{{ time ? "play again" : "play" }}</button>
        </div>
      </main>
      <footer>
        <div class="text-center">
          <p class="text-secondary mb-0">made by brock mowry</p>
        </div>
      </footer>
    </div>
  </div>
</template>

<script>
import ClickBlock from "./components/ClickBlock.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: { ClickBlock, Results },
  data() {
    return {
      playing: false,
      delay: null,
      time: null,
    };
  },
  methods: {
    play() {
      this.playing = true;
      this.delay = 1000 + Math.floor(Math.random() * 2001);
    },
    handleBlockClick(time) {
      this.playing = false;
      this.time = time;
    },
  },
};
</script>

<style scoped>
.app__wrapper {
  width: 100vw;
  height: 100vh;
  display: grid;
  place-items: center;
}

.app__container {
  width: 500px;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
</style>
