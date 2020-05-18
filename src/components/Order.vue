<template>
  <div id="main">
    <OrderForm @submit="addTodo" />
    <h3 v-if="sortedorder.length > 0">Votre Commande:</h3>
    <ul>
      <list-item
        v-for="(todo, i) in sortedorder"
        :key="i"
        :todo="todo"
        @delete="deleteTodo(i)"
      />
    </ul>

    <h3 v-if="completed.length > 0">Done</h3>
    <ul>
      <list-item
        v-for="(todo, i) in completed"
        :key="i"
        :todo="todo"
        :isCompleted="true"
        @delete="deleteTodo({ i, isCompleted: true })"
      />
    </ul>
  </div>
</template>

<script>
import OrderForm from '../components/OrderForm';
import ListItem from '../components/ListItem';

export default {
  name: 'Order',
  components: {
    OrderForm,
    ListItem,
  },
  data() {
    return {
      order: [],
      completed: [],
    };
  },
  computed: {
    sortedorder() {
      return this.order.sort((a, b) => a.nombredebiere - b.nombredebiere);
    },
  },
  methods: {
    addTodo(todo) {
      this.order.push(todo);
      this.$emit('update:updatedOrder', this.order);
    },
    deleteTodo({ i, isCompleted }) {
      if (isCompleted) {
        this.completed.splice(i, 1);
      } else {
        this.order.splice(i, 1);
      }
    },
    completeTodo(index) {
      this.completed.push(this.order.splice(index, 1)[0]);
    },
  },
};
</script>

<style scoped>
h1 {
  text-align: center;
  margin: 40px 0;
}

ul {
  margin: 0;
  padding: 0;
}
</style>
