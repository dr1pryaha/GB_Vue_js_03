<template>
  <ul class="costs-list">
    <div class="costs-list__title">
      <span>#</span>
      <span>Date</span>
      <span>Category</span>
      <span>Value</span>
    </div>
    <li v-for="cost in list" :key="cost.id" class="costs-list__item">
      <span v-for="(item, idx) in cost" :key="idx">{{ item }}</span>
    </li>
  </ul>
</template>

<script>
export default {
  name: "List",
  props: {
    list: Array,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.costs-list {
  width: 600px;
  margin: 50px auto;
  display: flex;
  flex-direction: column;

  &__item {
    height: 60px;
    border-bottom: 1px solid #000;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  &__title {
    font-weight: bold;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
}
</style>
