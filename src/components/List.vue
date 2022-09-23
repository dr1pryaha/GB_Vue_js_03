<template>
  <div class="costs-list">
    <div v-for="cost in list" :key="cost.id" class="costs-list__item">
      <span v-for="(item, idx) in cost" :key="idx">{{ item }}</span>
    </div>
  </div>
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
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  &__item {
    height: 60px;
    border-bottom: 1px solid #000;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
}
</style>
