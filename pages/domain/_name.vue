<template>
  <div class="container">
    <n-link to="/"><backward-arrow /></n-link>
    <h1 class="title">{{ $route.params.name }}</h1>
    <div class="info">
      <div v-if="$fetchState.pending">
        <content-placeholders>
          <content-placeholders-text :lines="15" />
        </content-placeholders>
      </div>
      <div v-else-if="$fetchState.error">
        <p>Error while fetching info: {{ $fetchState.error.message }}</p>
      </div>
      <div v-else>
        <ul v-for="(item, index) in info" :key="index">
          <li>{{ index }}</li>
          <li>{{ item }}</li>
        </ul>
      </div>
    </div>
    <copyright />
  </div>
</template>

<script>
export default {
  watch: {
    "$route.query": "$fetch",
  },
  data() {
    return {
      info: {},
    };
  },
  async fetch() {
    if (this.$route.params.name !== undefined) {
      this.info = await this.$http.$get(
        `https://api.mahdyar.me/whois/lookup?token=401d047add076e4b7e29423e7db623c0&domain=${this.$route.params.name}`
      );
    }
  },
  head() {
    return { title: this.$route.params.name };
  },
};
</script>

<style scoped>
.container {
  padding: 100px;
}
.title {
  font-size: 50px;
  text-align: center;
  margin-bottom: 20px;
}
.info {
  color: #59405d;
  padding: 10px 120px;
  height: 70vh;
  overflow-y: auto;
}
.info ul {
  margin-bottom: 10px;
  list-style: none;
}
.info li:first-child {
  font-size: 20px;
  font-weight: bold;
}
@media (max-width: 1300px) {
  .info{
    height: 65vh;
  }
}
@media (max-width: 512px) {
  .container{
    padding: 50px;
  }
  .title{
    width: 100%;
    font-size: 40px;
    display: inline-block;
  }
  .info{
    padding: 0;
    height: 65vh;
  }
  
}
</style>