<template>
  <div>
    <header>my Trello</header>
    <main>
      <p class="info-line">All: 0 tasks</p>
      <div class="list-index">
        <List
          v-for="(item, index) in lists"
          :key="item.id"
          :title="item.title"
          :listIndex="index"
        />
      </div>
      <ListAdd />
    </main>
  </div>
</template>

<script>
import ListAdd from "./ListAdd"
import List from "./List"
import { mapState } from "vuex"

export default {
  components: {
    ListAdd,
    List,
  },
  computed: {
    ...mapState(["lists"]),
  },
}
</script>
