<template>
  <div class="container" v-cloak>
    <h1 class="title">Lookup...</h1>
    <input
      v-model="domainName"
      type="text"
      placeholder="E.g. example.com"
      required
      v-on:keyup.enter="$router.push(`/domain/${domainName}`)"
      autofocus
    />
    <n-link ref="submitButton" :to="`/domain/${domainName}`"><arrow /></n-link>
    <copyright />
  </div>
</template>

<script lang="ts">
const psl = require('psl');
export default {
  data() {
    return {
      domainName: "",
    };
  },
  watch: {
    domainName: function(newDomainName:string) {
      try {
        const url = new URL(newDomainName);
        if (url.hostname) 
          this.domainName = psl.parse(url.hostname).domain;
      } catch(e){
        // do nothing
      }
    }
  }
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
@media (max-width: 1200px) {
  .container {
    margin: 7rem auto 0;
  }
}
@media (max-height: 512px) {
  input {
    font-size: 20px;
    width: 85%;
  }
  .container {
    margin: 1rem auto 0;
  }
}
</style>
