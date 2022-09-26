<template>
  <ul class="costs-list">
    <div class="costs-list__title">
      <span>#</span>
      <span>Date</span>
      <span>Category</span>
      <span>Value</span>
    </div>
    <li v-for="cost in list" :key="cost.id" class="costs-list__item">
      <span v-for="(item, idx) in cost" :key="idx" class="row">{{ item }}</span>
    </li>
  </ul>

  <!-- <table class="costs-list">
    <thead>
      <tr class="costs-list__title">
        <th>#</th>
        <th>Date</th>
        <th>Category</th>
        <th>Value</th>
      </tr>
    </thead>

    <tbody>
      <tr v-for="cost in list" :key="cost.id" class="costs-list__item">
        <td>{{ cost.id }}</td>
        <td>{{ cost.date }}</td>
        <td>{{ cost.category }}</td>
        <td>{{ cost.value }}</td> -->
  <!-- <td>
        <span 
          :class="[record.typeClass]"
          class="white-text badge"
        >{{ record.typeText }}</span>
      </td> -->
  <!-- <td>
        <button 
          v-tooltip="'Посмотреть запись'"
          class="btn-small btn" 
          @click="$router.push('/detail/' + record.id)"
        >
          <i class="material-icons">open_in_new</i>
        </button>
      </td> -->
  <!-- </tr>
    </tbody>
  </table> -->
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
    height: 50px;
    border-bottom: 1px solid #000;
    display: flex;
    justify-content: space-around;
    align-items: center;
  }

  &__title {
    font-weight: bold;
    display: flex;
    justify-content: space-around;
    align-items: center;
  }

  &__title span {
    flex-basis: 25%;
    padding: 8px 16px;
    text-align: center;
  }
}

.row {
  flex-basis: 25%;
  padding: 8px 16px;
  text-align: center;
}
</style>
