<template>
  <div class="container" v-cloak>
    <h1 class="title">Lookup...</h1>
    <input
      v-model="domainName"
      type="text"
      placeholder="E.g. example.com"
      required
      v-on:keyup.enter="$router.push(`/domain/${domainName}`);"
      autofocus
    />
    <n-link ref="submitButton" :to="`/domain/${domainName}`"><arrow /></n-link>
    <copyright />
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default {
  data() {
    return {
      domainName: "",
    };
  },
};
</script>
<style scoped>
input {
  display: block;
  width: 75%;
  height: 70px;
  margin: 75px auto;
  font-size: 30px;
  padding: 20px;
  border-top: none;
  border-left: none;
  border-right: none;
  color: #767676;
  outline: none;
}
@media (max-width: 512px) {
  input {
    font-size: 20px;
  }
}
</style>
