<template>
    <div class="note-header">
        <h1>{{ title }}</h1>
        <search
          @search="search = $event"
          :value="search"
          placeholder="find your notes"
        />
        <div class="icons">
          <svg
            :class="{ active: grid }"
            @click="changeGrid(true)"
            style="cursor: pointer"
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <rect x="3" y="3" width="7" height="7"></rect>
            <rect x="14" y="3" width="7" height="7"></rect>
            <rect x="14" y="14" width="7" height="7"></rect>
            <rect x="3" y="14" width="7" height="7"></rect>
          </svg>
          <svg
            :class="{ active: !grid }"
            @click="changeGrid(false)"
            style="cursor: pointer"
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <line x1="8" y1="6" x2="21" y2="6"></line>
            <line x1="8" y1="12" x2="21" y2="12"></line>
            <line x1="8" y1="18" x2="21" y2="18"></line>
            <line x1="3" y1="6" x2="3" y2="6"></line>
            <line x1="3" y1="12" x2="3" y2="12"></line>
            <line x1="3" y1="18" x2="3" y2="18"></line>
          </svg>
        </div>
      </div>
</template>
<script>
import Search from "./Search.vue";

export default {
    components:{
        Search
    },
    props:{
        grid:{
            type:Boolean,
            required:true
        }
    },
    methods:{
        changeGrid(status){
            this.$emit("changeGrid",status);
        }
    }
}
</script>
<style scoped>

</style>