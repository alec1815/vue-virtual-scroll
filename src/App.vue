<template>
  <div id="app">
    <virtual-list :size="30" :remain="14" :items="items">
      <list-item slot-scope="{ item }" :item="item"></list-item>
    </virtual-list>
  </div>
</template>

<script>
import VirtualList from "@/components/virtual-list.vue";
import ListItem from "@/components/list-item.vue";
const items = [];
for (let i = 0; i < 10000; i++) {
  items.push({
    id: i,
    value: `内容：${i}`,
  });
}
export default {
  name: "App",
  components: {
    VirtualList,
    ListItem,
  },
  data() {
    return {
      items,
    };
  },
};
</script>

<style lang="scss"></style>
