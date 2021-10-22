<template>
  <div :style="`background-color: ${bgcl}`" class="separator"></div>
</template>

<script>
export default {
  props: {
    bgcl: {
      type: String,
      default: 'black',
    },
  },
};
</script>

<style lang="scss">
.separator {
  width: 100%;
  height: 1px;
}
</style>
