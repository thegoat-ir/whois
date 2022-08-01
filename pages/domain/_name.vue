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
  data() {
    return {
      info: {},
      apiToken: process.env.apiToken,
    };
  },
  activated() {
    if (this.$fetchState.timestamp <= Date.now() - 30000) {
      this.$fetch();
    }
  },
  async fetch() {
    if (this.$route.params.name !== undefined) {
      this.info = await this.$http.$get(
        `https://api.thegoat.ir/whois/lookup?token=${this.apiToken}&domain=${this.$route.params.name}`
      );
    }
  },
  head() {
    return {
      title: this.$route.params.name,
      meta: [
        {
          hid: "og:title",
          name: "og:title",
          content: `${this.$route.params.name} whois lookup | thegoat.ir`,
        },
        {
          hid: "og:description",
          name: "og:description",
          content: `${this.$route.params.name} whois lookup information.`,
        },
      ],
    };
  },
  validate({ params, query, store }) {
    if (params.name == null) return false;
    else if (
      /^[a-zA-Z0-9][a-zA-Z0-9-]{1,61}[a-zA-Z0-9]\.[a-zA-Z]{2,}$/.test(
        params.name
      )
    )
      return true;
    else throw new Error("You should enter a valid domain name");
  },
};
</script>

<style scoped>
.container {
  margin: 5% auto;
  padding: 1.5% 5%;
}
.title {
  font-size: 50px;
  text-align: center;
  margin-bottom: 20px;
}
.info {
  color: #59405d;
  padding: 1% 15%;
  height: 65vh;
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

@media (max-width: 1200px) {
  .info {
    height: 65vh;
  }
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
  .info {
    padding: 0;
    height: 60vh;
  }
  .container {
    padding: 10% 10%;
  }
}
</style>
