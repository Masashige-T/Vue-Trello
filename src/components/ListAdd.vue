<template>
  <!-- @ = v-onの省略形 -->
  <!-- .pervent = perventDefaultと同義 submitイベントでのリロードを中断 -->
  <form class="addlist" @submit.prevent="addList">
    <!-- v-modelで指定したdataと紐付け(双方向バインディング？) -->
    <input v-model="title" type="text" class="text-input" placeholder="Add new list" />
    <button type="submit" class="add-button">Add</button>
  </form>
</template>

<script>
export default {
  data: function () {
    return {
      title: "",
    };
  },
  methods: {
    // actionをdispatchしてtitleを空に
    addList: function () {
      this.$store.dispatch("addlist", { title: this.title });
      this.title = "";
    },
  },
};
</script>