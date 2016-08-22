<template>
  <div id="app">
    <hello :msgfromfather="youdie" v-on:child-msg='handle'></hello>
     <h1 v-text='title'></h1>
     <input v-model='newItem' v-on:keyup.enter='addNew'>
      <ul>
        <li v-for="item in items" v-on:click='toggleFinished(item)' v-bind:class="{finished:item.isFinished}"> {{item.label}}</li>
      </ul>
  </div>
  <div>
  	<component :is='vuenum' transition='fade' transition-mode="out-in"></component>
  	<button @click='fade'>切换组件</button>
  </div>
</template>

<script>
import Hello from './components/Hello';
import one from './components/one';
import two from './components/two'
export default {
    components:{
       Hello,
       one,
       two,
    },
    data:function(){
       return {
          title:'this is a todo list',
          items:[
              {
                label:'coding',
                isFinished:false
              },
               {
                label:'working',
                isFinished:true
              }
          ],
          newItem:'',
          youdie:'hello',
          vuenum:'one'
         
       }
    },
   /* events:{
    	 afather:function(f){
            console.log(f)
    	 }
    },*/
    methods:{
       toggleFinished:function(item){
         item.isFinished=!item.isFinished
       },
       addNew:function(){
          this.items.push({
              label:this.newItem,
              isFinished:false
          }),
          this.newItem=''

       },
       handle:function(a){
       	 console.log(a);
       },
       fade:function(){
       	 this.vuenum=(this.vuenum=='one')?'two':'one';
       }


    }
}
</script>

<style>
.finished{
   text-decoration: line-through;
}


html {
  height: 100%;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

#app {
  color: #2c3e50;
  margin-top: -100px;
  max-width: 600px;
  font-family: Source Sans Pro, Helvetica, sans-serif;
  text-align: center;
}

#app a {
  color: #42b983;
  text-decoration: none;
}

.logo {
  width: 100px;
  height: 100px
}

</style>
