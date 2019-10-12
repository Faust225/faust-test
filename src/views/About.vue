<template>
<!-- https://stackoverflow.com/questions/49517563/native-code-message-in-return-of-vuejs-method -->
    <ul>
      <li @click="getById">get ALL</li>
      <input placeholder="add new title" v-model="todoName" @keyup.enter="addTodo">
      <input placeholder="delete object by id" v-model="deleteEl" @keyup.enter="deleteById">
      <!-- <li v-for="(todo, index) in list" :key="index">{{ todo }}</li> -->
      <li v-for="todo of todos" :key="todo.id"> {{todo.title}}</li>
    </ul>
</template>
<script>
import data from "@/services/data.js" 
import axios from 'axios';

// export default {
//   data() {
//     return {
//       list: data.dataArray
//     }
//   }
// };

export default {
  data() {
    return {
      list: data.dataArray,
      todos: [],
      todoName: "",
      deleteEl: 1
    }
  },
    async created() {
    try {
      const res = await axios.get("http://localhost:3000/posts")

    // data == array 
    this.todos = res.data;

    // find data
      // let found = (res.data.find(obj => obj.id === 1))
      // this.todos = found;
      console.log(this.todos)
    } catch(e) {
      console.error(e)
    }
  },

  methods: {
    async addTodo() {
      // takes data from input
      const res = await axios.post(`http://localhost:3000/posts`, { title: this.todoName })

      this.todos = [...this.todos, res.data]
      this.todoName = ''
    },

    async deleteById() {
      const res = await axios.delete("http://localhost:3000/posts/1")
    },

    async getAll() {
      const res = await axios.get("http://localhost:3000/posts/")
      .then( res => {
        res.data.forEach( obj => {
          console.log(obj)
        })
      })
    },

      async getById() {
      const res = await axios.get("http://localhost:3000/posts/")
      .then( res => {
        this.todos = res.data.find(obj => obj.id === 2)
      })
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

input {
  display: block;
}
</style>
