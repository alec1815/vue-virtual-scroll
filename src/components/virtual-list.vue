<template>
  <div ref="viewport" class="viewport" @scroll="handleScroll">
    <div ref="scrollBar" class="scroll-bar"></div>
    <div
      class="scroll-list"
      :style="{ transform: `translate3d(0,${offset}px,0)` }"
    >
      <div v-for="item in visibleData" :key="item.id">
        <slot :item="item"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    size: {
      default: 30,
      type: Number,
    },
    remain: {
      default: 14,
      type: Number,
    },
    items: {
      type: Array,
    },
  },
  data() {
    return {
      start: 0,
      end: this.remain,
      offset: 0,
    };
  },
  computed: {
    visibleData() {
      return this.items.slice(this.start, this.end);
    },
  },
  mounted() {
    console.log(this.$refs.viewport, this.$refs.scrollBar);
    this.$refs.viewport.style.height = `${this.size * this.remain}px`;
    this.$refs.scrollBar.style.height = `${this.size * this.items.length}px`;
  },
  methods: {
    handleScroll() {
      let scrollTop = this.$refs.viewport.scrollTop;
      this.start = Math.floor(scrollTop / this.size);
      this.end = this.start + this.remain;
      this.offset = this.start * this.size;
    },
  },
};
</script>

<style>
.viewport {
  overflow-y: scroll;
  position: relative;
}
.scroll-list {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
}
</style>
