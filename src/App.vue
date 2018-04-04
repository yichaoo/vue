<template>
  <div id="app">
  
   <h1 v-text="title"></h1>
   <ul>
     <input v-model="newItem" v-on:keyup.enter="addNewItem" />
     <li v-for="item in items" v-bind:class="{finished:item.isFinished}" v-on:click="toggleFinish(item)">
       {{item.label}}
     </li>
   </ul>
  </div>
</template>

<script>
export default {
  name: "App",
  data: function() {
    return {
      title: "这是一个待办demo",
      items: [
        // { label: "coding", isFinished: true },
        // { label: "meetting", isFinished: true }
      ],
      newItem:""
    };
  },
  methods:{
    toggleFinish:function(item){
      item.isFinished=!item.isFinished;      
    },
    addNewItem:function(){
      this.items.push({ label: this.newItem, isFinished: false });
      this.newItem="";
    }
  }

};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.finished {
  text-decoration:underline;
}
</style>
