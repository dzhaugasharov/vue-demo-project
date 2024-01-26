<script>

export default {
  data() {
    return {
      count: 0,
      users: [
        {
          name: 'User1',
          age: 23,
          books: 3
        },
        {
          name: 'User2',
          age: 15,
          books: 6
        },
        {
          name: 'User3',
          age: 40,
          books: 5
        }
      ],
      books: [
        'Book 1',
        'Book 2',
        'Book 3',
        'Book 4',
        'Book 5',
      ]
    }
  },
  methods: {
    add() {
      if (this.count >= 10) return;
      this.count++;
    },
    subtract() {
      if (this.count <= -10) return;
      this.count--;
    }
  }
}

</script>

<template>
  <main>
    <h3>Books</h3>
    <ul>
      <li v-for="(book, index) in books" :key="index">{{ book }}</li>
    </ul>

    <h3>Users</h3>
    <ol class="users-list">
      <li v-for="(user, index) in users" :key="index">
        {{ user.name }} has {{ user.books }} books
      </li>
    </ol>

    <div>
      <button @click="subtract()">убавить</button>
      <span class="couter">{{ count }}</span>
      <button @click="add()">добавить</button>
    </div>
    <div v-show="count >= 10">maximum</div>
    <div v-show="count <= -10">minimum</div>
    <div></div>
  </main>
</template>

<style scoped>
.users-list {
  margin: 12px 5px;
}
.couter {
  display: inline-block;
  margin: 2px 12px;
}
</style>
