<template>
  <div id="app">
   
    <HelloWorld post-title="hello!"  my-say="Hello!" :imperfectNumber="42" :ids="[234, 266, 273]" v-on:counter="countPlus"/>
    <HelloWorld  post-title="hello!"  my-say="Hello!" :imperfectNumber="42" :ids="[234, 266, 273]"  v-on:counter="countPlus"/>
    <span>Message:{{messsage}}</span><br>
    Join: <span v-html="channel"></span>
    <br>
    <button v-bind:disabled="isButtonDisabled">Button</button> <br>
    <button @click= "demo(count++)">click</button>
    <br>
    <button  @click= "demo1(counter++)">click me</button>
    <p> {{isVisible?"show":"hide"}}</p>
    <p v-if="seen"> Ban se thay toi </p>
    <button v-on:click = "demo2">Demo2</button>
    <form action="" method="get" v-on:submit.prevent="onSubmit">
      <button @click="onSubmit">Add</button>
    </form>
    <P>Original message: "{{text}}"</P>
    <p>Computed reverse message: "{{reversedText}}"</p>
    <p>{{fullName}}</p>
    Kilometers: <input type="text" v-model="kilometers">
    Meters: <input type="text" v-model="meters">
    <p v-bind:class="classObject">class binding</p>
    <p v-bind:class="[isActive ? activeClass : '', errorClass]">Array syntax</p>
    <h1 v-bind:style="{color:activeColor}">style inline object</h1>
    <h1 v-bind:style="[baseStyles]">style inline object</h1>
    <h1 v-if="ok">yes</h1>
    <h1 v-else>No</h1>
    <h1 v-if="type===1">1</h1>
    <h1 v-else-if="type===2">2</h1>
    <h1 v-else> not 1 or 2</h1>
    <h1 v-show="ok">Ok!</h1>
    <li v-for="item in object ">
      {{ item }}
  </li>
  <button v-on:click="greet">Greet</button> <br>
  <input v-model="message1" placeholder="edit me">
  <p>Message is: {{ message1}}</p>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "app",
  data() {
    return {
      a: 1,
      messsage: "hello",
      channel: "<b>the party</b>",
      isButtonDisabled: true,
      count: 0,
      isVisible: true,
      counter: 1,
      type: 1,
      seen: true,
      text: "alo",
      firstName: "Foo",
      lastName: "Bar",
      kilometers: 0,
      activeClass: "active",
      errorClass: "text-danger",
      isActive: true,
      message1:"alo",
      ok: true,
      meters: 0,
      classObject: {
        active: true,
        "text-danger": false
      },
      activeColor: "green",
      baseStyles: {
        color: "green"
      },
      object: {
        firstName: "John",
        lastName: "Doe",
        age: 30
      },
       name: 'Vue.js'
    };
  },
  watch: {
    firstName: function(val) {
      this.fullName = val + "" + this.lastName;
    },
    lastName: function() {
      this.fullName = this.firstName + "" + val;
    },
    kilometers: function(val) {
      this.kilometers = val;
      this.meters = val * 1000;
    },
    meters: function(val) {
      this.meters = val;
      this.kilometers = val / 1000;
    }
  },
  methods: {
    demo() {
      if (this.count % 2 == 0) {
        this.isButtonDisabled = true;
        this.seen = true;
      } else {
        this.isButtonDisabled = false;
        this.seen = false;
      }
    },
    countPlus: function() {
      this.count +=1
    },
    demo1() {
      if (this.counter % 2 === 0) {
        this.isVisible = false;
      } else {
        this.isVisible = true;
      }
    },
    demo2() {
      alert("day la demo");
    },
    onSubmit() {
      alert("ok");
    },
     greet: function (event) {
      // `this` inside methods points to the Vue instance
      alert('Hello ' + this.name + '!')
      // `event` is the native DOM event
      if (event) {
        alert(event.target.tagName)
      }
    },
  
  },
  computed: {
    reversedText: function() {
      return this.text
        .split("")
        .reverse()
        .join("");
    },
    fullName: function() {
      return this.firstName + "" + this.lastName;
    }
    //   fullName: {
    //   // getter
    //   get: function () {
    //     return this.firstName + ' ' + this.lastName
    //   },
    //   // setter
    //   set: function (newValue) {
    //     var names = newValue.split(' ')
    //     this.firstName = names[0]
    //     this.lastName = names[names.length - 1]
    //   }
    // }
  },
  created: function() {
    console.log("a is:" + this.a);
  },
  components: {
    HelloWorld
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
.active {
  color: blue;
}
/* .text-danger{
  color:red
} */
</style>
