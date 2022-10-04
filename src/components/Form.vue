<template>
  <div class="form">
    <div @click="closeBtnClick" class="closeModal"></div>
    <input
      v-model="category"
      :class="{ error: !this.category }"
      class="form-input description"
      type="text"
      placeholder="Payment Description"
    />

    <input
      v-model="value"
      :class="{ error: !this.value }"
      class="form-input amount"
      type="text"
      placeholder="Payment Amount"
    />

    <input
      v-model="date"
      :class="{ error: !this.date }"
      class="form-input date"
      type="text"
      placeholder="Payment Date"
    />

    <div @click="submitData" class="btn">ADD +</div>
  </div>
</template>

<script>
export default {
  name: "Form",
  props: {
    costsList: Array,
  },

  data() {
    return {
      category: "",
      value: "",
      date: "",
      error: false,
    };
  },

  methods: {
    closeBtnClick() {
      this.$emit("closePopup");
    },

    getId() {
      return (
        this.costsList.map(({ id }) => id).sort((a, b) => a - b)[
          this.costsList.length - 1
        ] + 1
      );
    },

    submitData() {
      if (this.category && this.date && this.value) {
        this.$emit("costsList");
        this.costsList.push({
          id: this.getId(),
          date: this.date,
          category: this.category,
          value: this.value,
        });
        this.category = "";
        this.value = "";
        this.date = "";
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.form {
  width: 400px;
  height: 300px;
  position: absolute;
  top: 300px;
  left: calc(55% - 300px);
  background-color: white;
  border: 1px solid cadetblue;
  border-radius: 9px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;

  &-input {
    width: 80%;
    height: 40px;
    border: none;
    border-bottom: 1px solid cadetblue;
    padding: 0;
    margin: 10px 0;
    outline: none;
  }
}

.error {
  border-bottom: 1px solid red;
}

.closeModal {
  position: absolute;
  top: 30px;
  right: 20px;
  width: 24px;
  height: 24px;
  opacity: 0.2;
  cursor: pointer;
  transition: opacity ease 0.5s;

  &:hover {
    opacity: 1;
  }
}

.closeModal::before,
.closeModal::after {
  content: "";
  position: absolute;
  top: 10px;
  display: block;
  width: 24px;
  height: 3px;
  background: #000;
}

.closeModal::before {
  transform: rotate(45deg);
}

.closeModal::after {
  transform: rotate(-45deg);
}

.btn {
  margin-top: 20px;
  margin-left: 55%;
  background-color: cadetblue;
  border: 1px solid cadetblue;
  border-radius: 3px;
  color: white;
  padding: 7px 25px;
  display: inline-block;
  cursor: pointer;
  transition: 0.3s;

  &:hover {
    background-color: transparent;
    color: cadetblue;
  }
}
</style>
