<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button v-on:click='clickme'>ClickMe</button>
    <button class='btn btn-danger' @click='father'>hello</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      // note: changing this line won't causes changes
      // with hot-reload because the reloaded component
      // preserves its current state and we are modifying
      // its initial state.
      msg: 'hello from component a'
    }
  },
  props:['msgfromfather'],
  methods:{
     clickme:function(){
        console.log(this.msgfromfather)
     },
     father:function(){
        this.$dispatch('child-msg','vue')
     }
  }

}
</script>
 
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import '//cdn.bootcss.com/bootstrap/3.3.6/css/bootstrap.css';
h1 {
  color: #42b983;
}
button{
   width: 60px;
   height: 30px;
   border: none;
}
</style>
