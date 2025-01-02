<template>
    <h1>To do List</h1>
  <div class="container">
    <AddItem @data-item="dataItem"/>
    <br>

    <div class="row justify-content-center">

        <div class="col-12 col-md-12 col-sm-12 col-lg-4 mb-3">
          <div class="card ">
            <div class="card-body">
              <h5>To do</h5>
              <TodoItem :items="items" :category="0" title="waiting" @emit-item="handler" @delete-item="handlerDelete"/>
            </div>
          </div>
        </div>
   
    
        <div class="col-12 col-md-12 col-sm-12 col-lg-4 mb-3">
          <div class="card">
            <div class="card-body">
              <h5>Started</h5>
              <TodoItem :items="started" :category="1" title="in progress" @emit-item="handler" @delete-item="handlerDelete"/>
            </div>
          </div>
        </div>
    

        <div class="col-12 col-md-12 col-sm-12 col-lg-4 mb-3">
          <div class="card">
            <div class="card-body">
              <h5>Finished</h5>
              <TodoItem :items="finished" :category="2" title="done" @emit-item="handler" @delete-item="handlerDelete" />
            </div>
          </div>
        </div>
    </div>


  </div>

</template>

<script>

import AddItem from './components/AddItem.vue';
import TodoItem from './components/TodoItem.vue';

export default {
  name: 'App',
  components: {
    AddItem,
    TodoItem,
  },
  data(){
    return{
      items:[],
      started:[],
      finished:[],
    }
  },
  methods:{
    dataItem(item){
      this.items.push(item);
    },
    handler(index, category){
      switch(category){
        case 0:
          this.started.push(this.items[index]);
          this.items.splice(index, 1);
          break;
        case 1:
          this.finished.push(this.started[index]);
          this.started.splice(index, 1);
          break;
        case 2:
          this.finished.splice(index, 1);
          break;
          
      }
    },
    handlerDelete(index, category){
      switch(category){
        case 0:
          this.items.splice(index, 1);
          break;
        case 1:
          this.started.splice(index, 1);
          break;
        case 2:
          this.finished.splice(index, 1);
          break;
          
      }
    }

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
  margin-top: 60px;
}
</style>
