<template>
  <h5>message work - {{ message }}</h5>
</template>

<script>
export default {
  props: {
    message: {
      type: String,
      required: false,
    },
  },
};
</script>