<template>
  <div class="wrapper">
    <header class="header"></header>
    <main class="main">
      <div class="todo">
        <div class="container">
          <div class="todo__inner">
            <div class="todo__input">
              <input
              v-model="task"
              type="text" placeholder="Have to do">
              <input 
              v-model="taskDd"
              type="text" placeholder="Dead Line">
            </div>
            <div class="todo__submit">
              <button
              v-on:click="add()"
              >Закрепить</button>
            </div>
            <div>
              <div class="todo__posts">
                <div
                v-for="nt in taskElem"
                :key="nt.name"
                >
                  <div 
                  class="todo__posts-items">
                    <div class="posts-items__check">
                      <label for="" class="label-check">
                        <input type="checkbox" id="checkbox">
                      </label>
                    </div>
                    <div 
                    class="posts-items__do">
                      <div class="do__text">{{nt.name}}</div>
                      <div class="do__dd">
                        Dead-Line:{{nt.dd}}</div>
                    </div>
                  </div>
                  <div 
                  class="todo__posts-delete">
                  <button
                    v-on:click="noteDelete(nt)"
                  ><img src="@/assets/icons/trash-solid.svg" alt="icon"></button></div>
                </div>
            </div>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
    
  },

  data(){
    return{
      task:'',
      taskDd: '',
      taskElem:[],
    }
  },

  methods:{
    add(){
      var newTaskElem = {
        name: this.task, 
        dd:this.taskDd
      };
      this.taskElem.push(newTaskElem);
      this.task = '';
      this.taskDd = '';
    },
    noteDelete(noteToDelete){
      this.taskElem = this.taskElem.filter(nt => nt !== noteToDelete);
    }
  }
}
</script>

<style scooped>
body{
  background-color: #333;
  margin: 0;
  padding: 0;
  position: relative;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 60px;
}
.todo {
  position: absolute;
  left: 40%;
  top: 10%;
}
.container {}
.todo__inner {}
.todo__posts-delete{
  max-width: 60px;
  height: 60px;
  margin-left: 20px;
}
button:hover{
  box-shadow: 0px 0px 10px #fff;
  border: 0px solid #333;
}
.todo__posts-delete button {
  background-color: #fff;
  border-radius: 50%;
  border: 0px solid #fff;
  height: 100%;
  transition: .3s;
  cursor: pointer;
}
.todo__posts-delete button:hover{
  box-shadow: 0px 0px 10px #fff;
}
.todo__posts-delete button img{
  width: 50%;
}
.todo__input {
  display: flex;
  flex-direction: column;
}
.todo__submit{
  width: 100%;
  display: flex;
  justify-content: center;
}
.todo__submit button{
  font-size: 18px;
  width: 50%;
  height: 50px;
  margin-top: 30px;

  border-radius: 20px;
  border:1px solid #333;
  cursor: pointer;
}
.todo__input input{
  color: #fff;
  font-size: 18px;
  width: 500px;
  height: 50px;
  text-align: center;
  background: transparent;
  border: 0px solid #333;
  border-bottom: 2px solid #fff;
}
.todo__input input:first-child{
  margin-bottom: 20px;
}
.todo__posts {
  margin-top: 70px;
  display: flex;
  align-items: center;
  flex-direction: column;
}
.todo__posts div{
  display: flex;
  flex-direction: row;
}
.todo__posts-items {
  display: flex;
  align-items: center;
  background-color: #fff;
  border-radius: 20px;
  padding: 20px 0px;
  transition: .2s ease-in-out;
  margin-bottom: 20px;

  width: 450px;
}
.todo__posts-items:hover{
  box-shadow: 0px 0px 10px #fff;
}
.label-check{
  margin: 0px 1em 0px 10px;
}
.label-check input{
  width: 20px;
  height: 20px;
}

.post-items__check{
  width: 10%;
  margin: 0px 0px 0px 20px;
}
.posts-items__do {
  display: flex;
  justify-content: space-between;
  width: 90%;
}
.do__text {
  color:#333;
  font-size: 22px;
}
.do__dd {
  font-size: 12px;
  color: #a9a7a7;
  width: 100px;
}


</style>
