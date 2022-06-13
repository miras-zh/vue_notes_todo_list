<template>
  <div id="nav">
    <div class="container">
      <Message v-if="message" :message="message" />
      <h2>To Do</h2>
      <NewNote :note="note" @addNote="addNote" />
      <BlockSearch :grid="grid" @changeGrid="changeGrid" />
      <Notes :notes="notesFilter" :grid="grid" @removeNote="removeNote" />
    </div>
  </div>
</template>

<script>
import Message from "./components/Message.vue";
import NewNote from "./components/NewNote.vue";
import Notes from "@/components/Notes.vue";
import BlockSearch from "./components/BlockSearch.vue";

export default {
  components: { Message, NewNote, Notes, BlockSearch },
  data() {
    return {
      title: "Notes App ",
      search: "",
      message: null,
      grid: true,
      note: {
        title: "",
        description: "",
      },
      notes: [
        {
          title: "first Note",
          description: "Lorem asd lamlm sdf  gfd dfg 516",
          date: "23-12-22",
        },
        {
          title: "second Note",
          description: "T o d o asd lamlm sdf  gfd dfg 516",
          date: "24-12-22",
        },
        {
          title: "third Note",
          description: "Lorem asd lamlm sdf  gfd dfg 516",
          date: "25-12-22",
        },
        {
          title: "four Note",
          description: "Lorem asd lamlm sdf  gfd dfg 516",
          date: "220-12-22",
        },
      ],
    };
  },
  methods: {
    addNote() {
      console.log("add note>", this.note);
      let { title, description } = this.note;
      this.notes.push({
        title,
        description,
        date: new Date(),
      });
      this.note = {
        title: "",
        description: "",
      };
    },
    changeGrid(val) {
      this.grid = val;
    },
    removeNote(index) {
      this.notes.splice(index, 1);
    },
  },
  computed: {
    notesFilter() {
      let array = this.notes;
      let search = this.search;
      if (!search) return array;
      search = search.trim().toLowerCase();
      // filter
      array = array.filter((item) => {
        if (item.title.toLowerCase().indexOf(search) !== -1) {
          return item;
        }
      });
      // Error
      return array;
    },
  },
};
</script>

<style lang="scss">
.active {
  color: #3761ff !important;
}

.container {
  max-width: 800px;
  margin: 0 auto;
}
.create-note {
  width: 500px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
}

button {
  cursor: pointer;
}
</style>
