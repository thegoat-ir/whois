<template>
  <arrow />
</template>
<style scoped>
svg {
  -ms-transform: rotate(-180deg);
  -webkit-transform: rotate(-180deg);
  transform: rotate(-180deg);
  float: left !important;
  width: 40px !important;
  height: 40px !important;
}
@media (max-width: 512px) {
  svg {
    width: 20px !important;
    height: 20px !important;
    position: absolute;
    top: 35px;
    left: 30px;
  }
}
</style>