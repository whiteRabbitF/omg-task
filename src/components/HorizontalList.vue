<template>
  <div class="horizontal-list">
    <div v-for="(item, index) in items" :key="index" class="list-item"
         @mouseover="handleMouseOver(index)" @mouseleave="handleMouseLeave(index)">
      <div class="item">{{ item }}</div>
    </div>
  </div>
</template>

<script>
import { onMounted, onUnmounted, reactive } from 'vue';

export default {
  props: {
    items: {
      type: Array,
      required: true
    }
  },
  setup(props) {
    const items = reactive(props.items);
    let intervalId;

    onMounted(() => {
      intervalId = setInterval(() => {
        items.forEach((item, index) => {
          items[index] = generateRandomNumber();
        });
      }, 1000);
    });

    onUnmounted(() => {
      clearInterval(intervalId);
    });

    const generateRandomNumber = () => Math.floor(Math.random() * 100);

    const handleMouseOver = (index) => {
      //console.log(`Mouse over item at index ${index}`);
    };

    const handleMouseLeave = (index) => {
      //console.log(`Mouse leave item at index ${index}`);
    };

    return { handleMouseOver, handleMouseLeave };
  }
};
</script>

<style>
.horizontal-list {
  display: flex;
}

.list-item {
  margin-right: 10px;
}

.item {
  width: 100px;
  height: 100px;
  border: 1px solid black;
  border-radius: 10px;
  transition: all 0.3s ease;
}

.list-item:hover .item {
  transform: scale(0.8, 0.8);
}
</style>
