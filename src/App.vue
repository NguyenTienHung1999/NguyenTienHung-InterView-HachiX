<template>
  <div id="app">
    <div class="date-time">
      <input type="date" placeholder="StartTime" />
      <input type="date" placeholder="EndTime" />
    </div>
    <span></span>
    <div class="search">
      <input
        type="text"
        v-model="searchQuery"
        placeholder="Search content..."
      />
    </div>

    <div class="buttoon">
      <h2>Content</h2>
      <input type="checkbox" v-model="getAllSelected" />
      <label>Select All</label>
      <div v-for="task in filteredResources" :key="task">
        <input type="checkbox" v-model="seleted" :value="task.id" />
        <label>{{ task.content }}</label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      searchQuery: "",
      isCheckAll: false,
      tasks: [
        { id: 1, content: "đi học", done: false },
        { id: 2, content: "thể dục", done: false },
        { id: 3, content: "nấu cơm", done: false },
        { id: 4, content: "học php", done: false },
        { id: 5, content: "dọn nhà", done: false },
        { id: 6, content: "rửa chén", done: false },
        { id: 7, content: "giặt quần áo", done: false },
        { id: 8, content: "đánh cầu lông", done: false },
      ],
      seleted: [],
      allSelected: false,
      tasksContent: [],
    };
  },
  methods: {
    // getAllSelected: {
    //   get: function () {
    //     return this.tasks ? this.seleted.length == this.tasks.length : false;
    //   },
    //   set: function (value) {
    //     var seleted = [];
    //     if (value) {
    //       this.tasks.forEach(function (task) {
    //         seleted.push(task.id);
    //       });
    //     }
    //     this.seleted = seleted;
    //   },
    // },
  },
  computed: {
    filteredResources() {
      if (this.searchQuery) {
        return this.tasks.filter((item) => {
          return item.content
            .toLowerCase()
            .includes(this.searchQuery.toLowerCase());
        });
      } else {
        return this.tasks;
      }
    },
    getAllSelected: {
      get: function () {
        return this.tasks ? this.seleted.length == this.tasks.length : false;
      },
      set: function (value) {
        var seleted = [];
        if (value) {
          this.tasks.forEach(function (task) {
            seleted.push(task.id);
          });
        }
        this.seleted = seleted;
      },
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 61px;
}
</style>
