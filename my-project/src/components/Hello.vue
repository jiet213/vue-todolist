<template>
  <div class="hello">
    <button v-on:click="clickMe">Get data from father</button>
    <h1 v-html="title"></h1>
    <h3 v-text="title"></h3>
    <h4>{{title}}</h4>
    <input v-model="newItem" v-on:keyup.enter="addNewItem">
    <ul class="todo-list">
      <li v-for="item in items" v-bind:class="{finished : item.isFinished}" v-on:click="toggleFinish(item)">
        <label>{{item.label}}</label>
        <button class="destroy" v-on:click="removeItem(item)"></button>
      </li>
    </ul>
  </div>
</template>

<script>
import Store from '../store'
export default {
  name: 'hello',
  data:  function() {
    return {
      title: '<em>Tip:</em>This is a todoList demo',
      items:Store.fetch(),
      newItem: ''
    }
  },
  props: ['msgfromfather'],
  watch: {
    items: {
      handler: function(items) {
        Store.save(items);
      },
      deep: true
    }
  },
  methods: {
    toggleFinish: function(item) {

      item.isFinished = !item.isFinished;

    },
    addNewItem: function() {

      this.items.push({

        label: this.newItem,

        isFinished: false

      });

      this.newItem = '';

    },
    removeItem: function(item) {

      this.items.splice(this.items.indexOf(item), 1);

    },
    clickMe: function() {

      console.log(this.msgfromfather);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

.hello {
  width: 550px;
}

.todo-list li {
  position: relative;
  font-size: 24px;
}

.todo-list li label {
    word-break: break-all;
    padding: 15px 60px 15px 15px;
    display: block;
    line-height: 1.2;
    transition: color 0.4s;
}
.todo-list li .destroy {
    display: none;
    background: none;
    border: 0;
    position: absolute;
    top: 0;
    left: 85px;
    bottom: 0;
    width: 40px;
    height: 40px;
    margin: auto 0;
    font-size: 30px;
    color: #cc9a9a;
    margin-bottom: 11px;
    transition: color 0.2s ease-out;
}
.todo-list li .destroy:after {
    content: '×';
}
.todo-list li:hover .destroy {
    display: block;
}
.todo-list li .destroy:hover {
    color: #af5b5e;
}
.todo-list .finished {
  text-decoration: line-through;
}

a {
  color: #42b983;
}
</style>
