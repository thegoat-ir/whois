<template>
  <div>
    <nuxt keep-alive />
  </div>
</template>

<style>
html {
  font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI",
    Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

.container {
  padding: 250px 250px 0;
}
.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 75px;
  color: #59405d;
  letter-spacing: 1px;
}
@media (max-width: 1300px) {
  .container {
    padding: 150px 150px 0;
  }
}
@media (max-width: 512px) {
  .container {
    padding: 150px 50px 0;
  }
  .title {
    font-size: 50px;
    text-align: center;
  }
}
</style>
