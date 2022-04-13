<template>
  <div style="height: 28px; border: 1px solid red;margin: 5px;">
    {{ item.id }}--{{ item.value }}
  </div>
</template>

<script>
export default {
  props: {
    item: Object,
  },
};
</script>

<style></style>
