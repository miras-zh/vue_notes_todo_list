<template>
  <div class="new-note">
    <input type="text" v-model="note.title" />
    <textarea
      class="description"
      name=""
      id=""
      cols="30"
      rows="10"
      v-model="note.description"
    ></textarea>
    <button class="btn btnPrimary" @click="addNote()">add note</button>
  </div>
</template>

<script>
export default {
  props: {
    note: {
      type: Object,
      required: true,
    },
  },
  methods: {
    addNote() {
      this.$emit("addNote", this.note);
    },
  },
};
</script>

<style lang="scss">
.new-note {
  display: flex;
  flex-direction: column;
  width: 100%;
  min-width: 300px;
  max-width: 700px;
  margin: 0 auto;
}

.description {
  width: 100%;
  margin: 20px 0;
  border-radius: 35px;
  padding: 24px;
  font-size: 22px;
  height: 130px;
}

.btn {
  width: 100px;
  height: 40px;
  border-radius: 22px;
  border: none;
  background: #7d8377;
  color: white;
  font-size: 18px;
}
</style>
