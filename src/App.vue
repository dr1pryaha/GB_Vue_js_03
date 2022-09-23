<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <AddButton @showPopup="popupToggle"></AddButton>
    <List :list="costsList"></List>
    <Form
      :addCost="costsList"
      @closePopup="popupToggle"
      v-if="isPopupActive"
    ></Form>
  </div>
</template>

<script>
import AddButton from "./components/AddButton.vue";
import Form from "./components/Form.vue";
import List from "./components/List.vue";

export default {
  name: "App",
  components: {
    AddButton,
    Form,
    List,
  },
  data() {
    return {
      costsList: [],
      isPopupActive: false,
    };
  },

  methods: {
    fetchData() {
      return [
        { id: 1, date: "20.09.2022", category: "food", value: 1582 },
        { id: 2, date: "15.09.2022", category: "transport", value: 245 },
        { id: 3, date: "22.09.2022", category: "healthcare", value: 780 },
      ];
    },
    popupToggle() {
      this.isPopupActive = !this.isPopupActive;
    },
  },

  created() {
    this.costsList = this.fetchData();
    console.log(this.costsList);
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
