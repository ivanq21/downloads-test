<template>
  <div class="lds-dual-ring"></div>
</template>

<script>
export default {
  name: "loading",
};
</script>
<style lang="scss">
.lds-dual-ring {
  display: inline-block;
  width: 100%;
  height: 100%;

  &::after {
    content: " ";
    display: block;
    width: 30px;
    height: 30px;
    border-radius: 50%;
    border: 3px solid #333;
    border-color: #333 transparent #333 transparent;
    animation: lds-dual-ring 1.2s linear infinite;
  }
}
@keyframes lds-dual-ring {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>