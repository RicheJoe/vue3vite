<template>
  <div>{{ v2 }}</div>
</template>

<script>
export default {
  props: {
    v2: {
      type: String,
      default: () => 'rootV2',
    },
  },
};
</script>

<style></style>
