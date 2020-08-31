<template>
  <!-- @ = v-onの省略形 -->
  <!-- .pervent = perventDefaultと同義 submitイベントでのリロードを中断 -->
  <form :class="classList" @submit.prevent="addList">
    <!-- v-modelで指定したdataと紐付け(双方向バインディング？) -->
    <input
      v-model="title"
      type="text"
      class="text-input"
      placeholder="Add new list"
      @focusin="startEditing"
      @focusout="finishEditing"
    />
    <button type="submit" class="add-button" v-if="isEditing || titleExists">Add</button>
  </form>
</template>

<script>
export default {
  data: function () {
    return {
      title: "",
      isEditing: false,
    };
  },
  computed: {
    classList() {
      const classList = ["addlist"];
      if (this.isEditing) {
        classList.push("active");
      }
      if (this.titleExists) {
        classList.push("addable");
      }
      return classList;
    },
    titleExists() {
      return this.title.length > 0;
    },
  },
  methods: {
    // actionをdispatchしてtitleを空に
    addList: function () {
      this.$store.dispatch("addlist", { title: this.title });
      this.title = "";
    },
    startEditing: function () {
      this.isEditing = true;
    },
    finishEditing: function () {
      this.isEditing = false;
    },
  },
};
</script>