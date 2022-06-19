<template>
  <div id="tab-bar">
    <slot></slot>
  </div>
</template>

<script>
</script>

<style>
  #tab-bar{
    display: flex;
    background-color: blanchedalmond;

    position: fixed;
    left: 0;
    right: 0;
    bottom: 0;

    box-shadow: 0px 0px 10px red;
  }

</style>
