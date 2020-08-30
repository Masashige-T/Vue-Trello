<template>
  <!-- @ = v-onの省略形 -->
  <!-- .pervent = perventDefaultと同義 submitイベントでのリロードを中断 -->
  <form class="addlist" @submit.prevent="addlist">
    <!-- v-modelで指定したdataと紐付け(双方向バインディング？) -->
    <input v-model="title" type="text" class="text-input" placeholder="Add new list" />
    <button type="submit" class="add-button">Add</button>
  </form>
</template>

<script>
export default {
  data: () => {
    return {
      title: "",
    };
  },
  methods: {
    // actionをdispatchしてtitleを空に
    addList: () => {
      this.$store.dispatch("addList", { title: this.title });
      this.title = "";
    },
  },
};
</script>