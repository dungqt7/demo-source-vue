<template>
  <div class="hello">
     <h3>{{ postTitle }} {{imperfectNumber}} {{ids}}
        <slot></slot>
     </h3>
     <h1>{{dataSay}}</h1>
     <button v-on:click="numberPlus">{{count}}</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  methods: {
   numberPlus: function() {
     this.count += 1;
     this.$emit('counter')
   }
  },
  props:{
    postTitle:null,
    imperfectNumber: {
      type: Number,
      required: true,
    },
    ids: {
      type:Array
    },
   mySay:null,
  },
  data() {
    return {
        dataSay:this.mySay+"This is dataSay!",
        count:0
      }
  }
}
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
</style>
