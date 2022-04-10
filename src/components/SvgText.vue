<template>
  <div class="msg-text-container">
    <div class="text-wrap">
      {{text}}
      <svg-icon :iconClass="icon" class="icon-pos" v-if="isNeedIcon"></svg-icon>
    </div>
  </div>
</template>

<script>
export default {
    props: {
        text: {
            type: String,
            require: true,
        },
        icon: {
            type: String,
        },
        isNeedIcon: {
            type: Boolean,
            default: true,
        },
    },
};
</script>

<style>
.msg-text-container {
    margin: 10px 0;
}
.text-wrap {
    display: inline-block;
    padding: 10px 40px;
    border-radius: 40px;
    background-color: rgb(135, 176, 196);
    color: #fff;
    font-size: 24px;
    position: relative;
}
.icon-pos {
    position: absolute;
    right: -16px;
    top: 3px;
    background-color: #fff;
    z-index: 100;
    border-radius: 50%;
}
</style>