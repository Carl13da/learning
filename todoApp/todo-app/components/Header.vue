<template>
  <view class="header">
    <text class="title">{{ title }}</text>
  </view>
</template>

<script>
export default {
  props: ["title"]
};
</script>

<style>
.header {
  height: 100px;
  background-color: black;
  justify-content: center;
  align-items: center;
}
.title {
  color: aliceblue;
  font-size: 20px;
}
</style>