<template>
  <footer>
    <p>
      Made with &lt;3 by
      <a href="https://thegoat.ir" alt="The Goat" target="_blank">The Goat</a>
    </p>
    <p id="android">
      There is an Android app of this website available as well, and can be
      downloaded from
      <a
        href="https://releases.mahdyar.me/whois/android/whois-latest.apk"
        target="_blank"
        >here</a
      >.
    </p>
  </footer>
</template>
<style scoped>
footer {
  width: 85%;
  position: absolute;
  display: block;
  text-align: center;
  color: #59405d;
  left: 50%;
  transform: translate(-50%, 0);
  bottom: 2rem;
}
a {
  color: inherit;
}
#android {
  margin-top: 5px;
  font-size: 14px;
  color: #555555;
  opacity: 0.8;
  display: none;
}
@media (max-width: 1200px) {
  #android {
    display: block;
  }
}
</style>
