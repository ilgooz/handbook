<template>
  <div class="trello-board">
    <blockquote class="trello-board-compact">
      <a :href="url">{{title}}</a>
    </blockquote>
  </div>
</template>

<script>
export default {
  props: {
    url: String,
    title: String,
  },
  mounted () {
    TrelloBoards.load()
  }
}
</script>


<style scoped>
.trello-board {
  margin: .5em;
}
</style>
