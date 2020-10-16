<template>
  <footer>
    <p>
      Made with &lt;3 by
      <a href="https://mahdyar.me" alt="mahdyar" target="_blank">Mahdyar</a>
    </p>
    <p id="android">
      This website is available for android as well and can be downloaded from
      <a href="https://mhdyr.ir/whois-1-1" target="_blank">here</a>.
    </p>
  </footer>
</template>
<style scoped>
footer {
  display: block;
  width: 100%;
  text-align: center;
  bottom: 50px;
  margin-top: 375px;
  color: #59405d;
}
a {
  color: inherit;
}
#android {
  margin-top: 5px;
  font-size: 14px;
  color: #555555;
  opacity: 0.8;
}
@media (max-width: 512px) {
  footer {
    margin-top: 285px;
  }
}
</style>