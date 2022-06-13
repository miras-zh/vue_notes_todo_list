<template>
  <div class="wrapper__search">
    <div class="search">
      <div class="search-icon"></div>
    </div>
    <input
      type="text"
      class="search-input"
      :placeholder="placeholder"
      v-model="search"
    />
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      required: true,
    },
    placeholder: {
      type: String,
      default: "search",
    },
  },
  data(){
      return {
          search: this.value
      }
  },
  watch: {
      search(val) {
          this.$emit('search', val);
      }
  }
};
</script>

<style lang="scss">
svg {
  color: #e4e4e4;
}
/* Search */
.wrapper__search {
  position: relative;
}
.search {
  top: 0px;
  bottom: 0px;
  left: 0px;
  position: absolute;
}
.search-icon {
  height: 100%;
  padding-left: 16px;
  padding-right: 16px;
  align-items: center;
  display: flex;
}
input {
  padding: 16px 16px 16px 56px !important;
  margin-bottom: 0px;
  border-radius: 30px;
  color: #909399;
  font-size: 16px;
  min-width: 400px;
  height: auto;
}

// .search-input {
//   width: 100%;
//   height: 32px;
//   border-radius: 23px;
//   outline: none;
//   border: none;
//   padding-left: 15px;
// }
</style>