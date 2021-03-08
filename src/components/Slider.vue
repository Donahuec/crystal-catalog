<template>
  <div>
    <div v-for="number in [currentNumber]" :key="number" transition="fade">
      <img
        :src="
          'http://site.local:8081/api/assets/crystal-catalog/' +
          imageIds[Math.abs(currentNumber) % imageIds.length]
        "
        class="responsive"
      />
    </div>
    <p class="text-center"><a @click="prev()">Previous</a> || <a @click="next()">Next</a></p>
  </div>
</template>

<script>
export default {
  name: "Slider",
  props: {
    imageIds: Array,
  },
  data() {
    return {
      currentNumber: 0,
      timer: null,
    };
  },
  methods: {
    next: function () {
      this.currentNumber += 1;
    },
    prev: function () {
      this.currentNumber -= 1;
    },
  },
};
</script>

<style>
.fade-transition {
  transition: all 0.8s ease;
  overflow: hidden;
  visibility: visible;
  opacity: 1;
  position: absolute;
}
.fade-enter,
.fade-leave {
  opacity: 0;
  visibility: hidden;
}
</style>
