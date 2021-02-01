<template>
  <div class="container">
    <n-link to="/"><backward-arrow /></n-link>
    <h1 class="title">{{ this.$props.error.message }}</h1>
    <copyright />
  </div>
</template>

<script>
export default {
  props: ["error"],
  layout: "error",
};
</script>


<style scoped>
.container {
  padding: 1.5% 5%;
}
.title {
  font-size: 50px;
  text-align: center;
  margin-bottom: 20px;
  position: absolute;
  top: 50%;
  left: 50%;
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}

@media (max-width: 1200px) {
  .container {
    margin: 10% auto 0;
  }
}
@media (max-width: 512px) {
  .title {
    width: 100%;
    font-size: 40px;
    display: inline-block;
  }
  .container {
    padding: 10% 10%;
  }
}
</style>