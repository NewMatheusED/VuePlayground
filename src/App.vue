<template>
  <div class="container">
    <h1>Playground for Vue.js</h1>

  <div class="btnCounter">
    <button class="btn" v-on:click="increaseCounter">Seu contador está em: {{counter}}</button>
    <button class="btn" v-on:click="resetCounter">Reset Counter</button>
  </div>

  <hr />

  <form>
    <textarea name="todo" id="todo" v-model="message"></textarea>
    <button class="btn" type="button" v-on:click="addTodo">Add Todo</button>
    <div class="todoList" v-for="(message, index) in messages">
      <ul>
        <li>{{message}}</li>
        <a href="#" v-on:click.prevent="deletar(index)">Excluir</a>
        <hr>
      </ul> 
    </div>
  </form>

  </div>
</template>



<script>
  export default {
    name: 'App',
    data() {
      return {
        counter: 0,
        messages: []
      }
    },
    methods: {
      increaseCounter() {
        this.counter++;
      },

      resetCounter() {
        if(this.counter === 0) {
          alert('O contador já está em 0');
        } else {
          this.counter = 0;
        }
      },

      addTodo() {
        if(this.messages === '') {
          alert("Por favor, preencha o campo");
        } else {
          this.messages.push(this.message);
          this.message = '';
        }
      },

      deletar(index) {
        this.messages.splice(index, 1);
      }
    }
  }

</script>



<style>

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Roboto', sans-serif;
  }

  .container {
    margin: 0 auto;
    padding: 2%;
    text-align: center;
  }

  hr {
    width: 100%;
    border: 1px solid #ccc;
    margin: 20px auto;
  }

  .container h1 {
    font-size: 2em;
    margin-bottom: 1em;
  }

  .btn {
    margin: 0.5em;
    padding: 0.5em;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 1em;
    font-weight: bold;
    cursor: pointer;
    transition: all .3s;
  }

  .btn:hover {
    background-color: #ccc;
  }

  textarea {
    width: 100%;
    height: 100px;
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 10px;
    font-size: 1em;
    font-weight: bold;
    resize: none;
    text-align: center;
  }

  .todoList {
    margin: 1em 0;
  }

  .todoList ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .todoList ul li {
    padding: 0.5em;
    font-size: 1em;
    font-weight: bold;
  }

  .todoList ul a {
    color: rgb(223, 70, 70);
    text-decoration: none;
    border: 1px solid rgb(223, 70, 70);
    padding: .2em .5em;
    border-radius: 15px;
    transition: all .3s;
  }

  .todoList ul a:hover {
    color: #000;
    background-color: rgb(223, 70, 70);
  }
</style> 