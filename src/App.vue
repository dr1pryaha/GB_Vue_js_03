<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <h1>My Personal Costs</h1>
    <AddButton @showPopup="popupToggle"></AddButton>
    <List :list="paginatedData"></List>
    <Form
      :costsList="costsList"
      @closePopup="popupToggle"
      v-if="isPopupActive"
    ></Form>
    <Pagination
      :costsList="costsList"
      :pageCount="pageCount"
      :perPage="perPage"
      :currentPage="currentPage"
      @onPageChange="onPageChange"
    ></Pagination>
  </div>
</template>

<script>
import AddButton from "./components/AddButton.vue";
import Form from "./components/Form.vue";
import List from "./components/List.vue";
import Pagination from "./components/Pagination.vue";

export default {
  name: "App",
  components: {
    AddButton,
    Form,
    List,
    Pagination,
  },
  data() {
    return {
      costsList: [],
      isPopupActive: false,
      currentPage: 1,
      perPage: 5,
    };
  },

  methods: {
    fetchData() {
      return [
        { id: 1, date: "20.09.2022", category: "food", value: 1582 },
        { id: 2, date: "15.09.2022", category: "transport", value: 245 },
        { id: 3, date: "22.09.2022", category: "healthcare", value: 780 },
        { id: 4, date: "22.09.2022", category: "healthcare", value: 780 },
        { id: 5, date: "22.09.2022", category: "healthcare", value: 780 },
        { id: 6, date: "22.09.2022", category: "healthcare", value: 780 },
        { id: 7, date: "22.09.2022", category: "healthcare", value: 780 },
        { id: 8, date: "22.09.2022", category: "healthcare", value: 780 },
        { id: 9, date: "22.09.2022", category: "healthcare", value: 780 },
        { id: 10, date: "22.09.2022", category: "healthcare", value: 780 },
      ];
    },
    popupToggle() {
      this.isPopupActive = !this.isPopupActive;
    },
    onPageChange(page) {
      console.log(page);
      this.currentPage = page;
    },
  },

  computed: {
    pageCount() {
      let l = this.costsList.length,
        s = this.perPage;
      return Math.ceil(l / s);
    },
    paginatedData() {
      const start = (this.currentPage - 1) * this.perPage,
        end = start + this.perPage;
      return this.costsList.slice(start, end);
    },
  },

  created() {
    this.costsList = this.fetchData();
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
