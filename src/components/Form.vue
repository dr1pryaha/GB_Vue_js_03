<template>
  <div class="form"></div>
</template>

<script>
export default {
  name: "Form",
  // props: {
  //   msg: String,
  // },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.form {
  width: 1000px;
  height: 60vh;
  position: absolute;
  top: 200px;
  left: calc(50% - 500px);
  background-color: white;
  border: 1px solid cadetblue;
  border-radius: 9px;
}
</style>
