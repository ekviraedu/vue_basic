<template>
<!--
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  -->
  <!--
    Exercise 1
  -->
  <h1>{{ message }}</h1>

  <!--
    Exercise 2
    Bind to a method/function.
    The @click syntax is short for v-on:click.
  -->
  
  <button @click="reverseMessage">Reverse Message</button>

  <!--
    Exercise 3
    Append character to message
  -->
  <br>
   <br>
  <button @click="message += '%'">Append "%"</button>

  <!--
    Exercise 4
    Show an alert box on clicking a link
  -->
   <br>
   <br>
   <a href="https://www.espncricinfo.com/" @click.prevent="alertBox">
   Click this link to show an alert box
   </a>

  <!--
    Exercise 5
  -->
  <p>
    <span :title="message">
      Hover over this text to view the title.
    </span>
  </p>

  <!--
    Exercise 6
  class bindings have special support for objects and arrays
  in addition to plain strings
  -->
  <p :class="{ red: isRed }" @click="toggleRed">
    RED TEXT. Click text to toggle the color.
  </p>

  <!-- style bindings also support object and arrays -->
  <p :style="{ color }" @click="toggleColor">
    GREEN TEXT. Click text to toggle between green and yellow.
  </p>

  <!--
    Exercise 7
  -->
  <button @click="showList = !showList">Toggle List</button>
  <button @click="listNums.push(listNums.length + 1)">Push Number</button>
  <button @click="listNums.pop()">Pop Number</button>
  <button @click="listNums.reverse()">Reverse List</button>

  <ul v-if="show && listNums.length">
    <li v-for="item in listNums" :key=item>
      {{ item }}
    </li>
  </ul>
  <p v-else-if="listNums.length">List is not empty, but hidden.</p>
  <p v-else>List is empty.</p>

  <!--
    Exercise 8
  -->

  <h2>Text Input</h2>
  <input v-model="text"> {{ text }}

  <h2>Checkbox</h2>
  <input type="checkbox" id="checkbox" v-model="checked">
  <label for="checkbox">Checked: {{ checked }}</label>

  <!--
    multiple checkboxes can bind to the same
    array v-model value
  -->
  <h2>Multi Checkbox</h2>
  <input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
  <label for="jack">Jack</label>
  <input type="checkbox" id="john" value="John" v-model="checkedNames">
  <label for="john">John</label>
  <input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
  <label for="mike">Mike</label>
  <p>Checked names: <pre>{{ checkedNames }}</pre></p>

  <h2>Radio</h2>
  <input type="radio" id="one" value="One" v-model="picked">
  <label for="one">One</label>
  <br>
  <input type="radio" id="two" value="Two" v-model="picked">
  <label for="two">Two</label>
  <br>
  <span>Picked: {{ picked }}</span>

  <h2>Select</h2>
  <select v-model="selected">
    <option disabled value="">Please select one</option>
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
  <span>Selected: {{ selected }}</span>

  <h2>Multi Select</h2>
  <select v-model="multiSelected" multiple style="width:100px">
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
  <span>Selected: {{ multiSelected }}</span>

</template>

<style>
.red {
  color: red;
}
</style>

<script>
//import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  //components: {
  //  HelloWorld
  //},
  // Exercise 1: Add your message to the bottom of the default page 
  data() { 
    return {
      message: 'QWERTY',
      // Exercise 5
      isRed: true,
      color: 'green',
      // Exercise 7
      showList: true,
      listNums: [1,2,3,4,5],

      // Exercise 8
      text: 'Edit me',
      checked: true,
      checkedNames: ['Jack'],
      picked: 'One',
      selected: 'A',
      multiSelected: ['A']
    }
  },

  methods: {
    // Exercise 2
    reverseMessage(){
      this.message = this.message.split("").reverse().join("")
    },

    // Exercise 4
    alertBox(){
      alert('Warning. The link you clicked in not safe for browsing.')
    },

    // Exercise 6
    toggleRed(){
      this.isRed = !this.isRed
    },

    toggleColor(){
      this.color = this.color === 'green' ? 'yellow' : 'green'
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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
