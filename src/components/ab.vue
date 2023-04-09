<template>
    <div id="app">
      <select class="select" >
        <option v-for="course in courses" :key="course" value="">{{ title }}</option>
      </select>
    
    <ul v-if="posts && posts.length">
      <li v-for="post of posts" :key="post">
        <p><strong>{{post.title}}</strong></p>
        <p>{{post.body}}</p>
      </li>
    </ul>

    <select class="select" name="" id="">
      <option v-for="post of posts" :key="post" value="">{{ post.title }}</option>
    </select>

    <ul v-if="errors && errors.length">
      <li v-for="error of errors" v-bind:key="error">
        {{error.message}}
      </li>
    </ul>
  
    <div>
      <select class="select" >
        <option v-for="post of posts" :key="post" value="">{{ post.name }}</option>
      </select>
      <label class="typo__label">Tagging</label>
         <Multiselect  class="multi"
                      v-model="value"
                      placeholder="city name?"
                      label="city" track-by="city_ascii"
                      :options="options"
                      :multiple="true"
                      :taggable="true"
                      >
        </Multiselect>
    </div>
        <div class="wrapper">
          <Multiselect  class="multi"  
                        v-model="value"
                        :options="options"
                        :multiple="true"
                        group-values="libs"
                        group-label="language"
                        :group-select="true"
                        placeholder="Type to search"
                        track-by="name"
                        label="name"
                        >
          </Multiselect>
          
          <button class="btn">Lưu</button>
        </div>
        <Toast/>
  <div>
  <ul>
    <li v-for="(value, key) in averageRent" :key="value">
      The average rent in {{ key }} is ${{ value }}
    </li>
  </ul>
  <p v-html="someString"></p>
  <label><input type="radio" v-model="value" value="one">One</label>
  <label><input type="radio" v-model="value" value="two">Two</label>
  <label><input type="radio" v-model="value" value="three">Three</label>
  
   Reduce 
  <p>Sum of numbers: {{ numberTotal }}</p>

   Watch 
  <p>{{ count }}</p>
  <button @click="count++">click</button>

   Props
   <ComponentA></ComponentA> 

   Todos list 
  <div id="todo-list-example">
    <input
      v-model="newTodoText"
      v-on:keyup.enter="addNewTodo"
      placeholder="Thêm việc cần làm"
    >
    <p>{{newTodoText}}</p>
    <ul>
      <li
        is="todo-item"
        v-for="(todo, index) in todos"
        :key="todo.id"
        :title="todo.title"
        @:remove="todos.splice(index, 1)"
      ></li>
    </ul>
    </div>    
  </div>
</div>
</template>

// <script>
// import { ref } from 'vue'
// import axios from 'axios'
// export default {
//   name: 'app',
//   data () {
//     return {
//       mess: '',
//       info: null,
//       courses: []
//     }
//   },
//   mounted () {
//     axios.get('https://jsonplaceholder.typicode.com/posts')
//       .then(response => {
//         this.response = response.data.data
//         console.log(response);
//       })
//   },
//   methods: {

//   },
//   setup(){
//     var courses = 'https://jsonplaceholder.typicode.com/posts'
//     fetch(courses)
//       .then(function(respone){
//         return respone.json()
//       })
//       .then(function(courses){
//         return courses.title
//       })
//     const courses = ref([
//         {
//           id: 1,
//           title: 'Titile 1'
//         },
//         {
//           id: 2,
//           title: 'Titile 2'
//         },
//         {
//           id: 3,
//           title: 'Titile 3'
//         },
//         {
//           id: 4,
//           title: 'Titile 4'
//         },
//     ])
//   }
// }
// import axios from 'axios';
// import Toast from './components/Toast.vue'
// import Multiselect from 'vue-multiselect'

// export default {
//   components: {
//     Toast,
//     Multiselect
//   },

//   data() {
//     return {
//       dataJsonCountryFull: [
//         {
//           id: 0,
//           name: '',
//           country_id: 0,
//           country_name: ''
//         }
//       ],
//       value: [],
//       options: [
//                 {
//           language: 'Javascript',
//           libs: [
//             { name: 'Vue.js', category: 'Front-end' },
//             { name: 'Adonis', category: 'Backend' }
//           ]
//         },
//         {
//           language: 'Ruby',
//           libs: [
//             { name: 'Rails', category: 'Backend' },
//             { name: 'Sinatra', category: 'Backend' }
//           ]
//         },
//         {
//           language: 'Other',
//           libs: [
//             { name: 'Laravel', category: 'Backend' },
//             { name: 'Phoenix', category: 'Backend' }
//           ]
//         }
//       ],
      
//     }
//   },

//   created(){
//     this.dataJsonCountryFull = this.country
//   },

//   methods: {
//     addTag (newTag) {
//       const tag = {
//         name: newTag,
//         code: newTag.substring(0, 2) + Math.floor((Math.random() * 10000000))
//       }
//       this.options.push(tag)
//       this.value.push(tag)
//     },
//   },

//   watch: {
//     count(newValue, oldValue){
//       console.log('count change');
//     }
//   },

//   computed: {
//     numberTotal(){
//       return this.numbers.reduce((total, number) => total + number)
//     }
//   },


  
//   created() {
//     axios.get(`https://jsonplaceholder.typicode.com/users`)
//     .then(response => {
//       this.posts = response.data
//     })
//     .catch(e => {
//       this.errors.push(e)
//     })
//   }
// }
// </script>

// <style>
.select {
  width: 50%;
  height: 50px;
}

.multi {
  width: 50%;
}

.wrapper {
  position: relative;
  width: 70%;
  background: paleturquoise;
}

button {
  position: absolute;
  right: 0;
  width: 60px;
  height: 40px;
  background: blue;
  border: none;
  border-radius: 10px;
  color: #fff;
  font-weight: 600;
  cursor: pointer;
}

button:hover {
  opacity: 0.8;
}
</style>
