<template>
  <div>
    <div class="form" v-if="show">
      <p><input placeholder="date" type="text" v-model="todo.date"></p>
      <p><input placeholder="title" type="text" v-model="todo.title"></p>
      <p><input placeholder="body" type="text" v-model="todo.body"></p>
      <p>
        <button @click="add">登録</button>
      </p>
    </div>
    <div class="cards">
      <div :key="i" class="card" v-for="(item, i) in items">
        <div class="icons">
          <p><img @click="edit(item, i)" alt="" src="./assets/edit.svg"/></p>
          <p><img @click="remove(i)" alt="" src="./assets/delete.svg"/></p>
        </div>
        <div>{{ item.title }}</div>
        <div>{{ item.body }}</div>
        <div class="date">{{ item.date }}</div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Card',
  props: ['show'],
  data() {
    return {
      todo: {
        index: undefined,
        title: '',
        date: '',
        body: '',
      },
      items: [],
    }
  },
  methods: {
    add() {
      if (this.todo.index >= 0) {
        this.items[this.todo.index] = this.todo
      } else {
        this.items.push(Object.assign({}, this.todo))
      }
      this.todo = Object.assign({})
    },
    remove(index) {
      this.items.splice(index, 1)
    },
    edit(todo, index) {
      this.todo = Object.assign({}, todo, {
        index,
      });
    }
  }
}
</script>
<style scoped>

.date {
  position: absolute;
  right: 10px;
  bottom: 5px;
}

p {
  margin: 0;
}

.cards {
  position: relative;
  display: flex;
  flex-wrap: wrap;

}

.cards > .card {
  margin-right: 20px;
}

.card {
  position: relative;
  width: 200px;
  height: 150px;
  background: #F8F2F2;
  padding: 8px;
  box-sizing: border-box;
}

.icons {
  display: flex;
  position: absolute;
  right: 5px;
  top: 10px;
  align-items: center;
}

.icons p {
  margin-right: 5px;
}
</style>