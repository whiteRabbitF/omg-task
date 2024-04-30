<template>
  <div class="vertical-list">
    <div v-for="(item, index) in items" :key="index" class="list-item">
      <HorizontalList :items="item.subItems" />
    </div>
  </div>
</template>

<script>
import { reactive } from 'vue';
import HorizontalList from './HorizontalList.vue';

export default {
  components: {
    HorizontalList
  },
  setup() {
    const items = reactive(generateRandomItems());

    function generateRandomItems() {
      const numItems = Math.floor(Math.random() * 100) + 1;
      const items = [];
      for (let i = 0; i < numItems; i++) {
        const subItems = generateRandomSubItems();
        items.push({ subItems });
      }
      return items;
    }

    function generateRandomSubItems() {
      const numSubItems = Math.floor(Math.random() * 10) + 1;
      const subItems = [];
      for (let i = 0; i < numSubItems; i++) {
        subItems.push(Math.floor(Math.random() * 100));
      }
      return subItems;
    }

    return { items };
  }
};
</script>

<style>
.vertical-list {
  display: flex;
  flex-direction: column;
}

.list-item {
  margin-bottom: 20px;
}
</style>
