<template>
  <div class="app">
    <input type="text" v-model="name">
    <input type="checkbox" v-model="accept">Tôi đồng ý
    <p>{{ name }}</p>
    <button @click="isShow = !isShow">an/hien</button>
    <div v-show="isShow">
      <h2>Lập trình viên</h2>
    </div>
    <h1 v-bind:class='id'>Lập trình viên</h1>

    <input type="text" :disabled="inputDisabled">
    <button @click="inputDisabled = ! inputDisabled">Mo/Khoa</button>

    <!-- v-bind:class -->
    <h2 :class="{select: selected}">Hello guys!</h2>
    <button @click="selected = !selected">Change color</button>
    <br>

    <!-- v-model -->
    <input type="text" v-model="changeName.name">
    

    <!-- Event handling -->
    <button v-on:click='changeName.name = "Name has change"'>Click</button>

    <!-- Prevent Default ngăn chặn -->
    <div>
      <input type="text" v-model="changeName.name">
      <button @click='changeName.name = "Name has change"'>Click</button>
      <button type="submit" @click.prevent="changeName.name = 'Name has change'">Submit</button>
    </div>

    <!-- Debounce vue: sau 1 thời gian ngắn thì thông tin mới hiên thị -->
    <!-- ref: gọi đến chính element đấy -->
    <!-- <input ref="changeName" type="text" v-model="name">
    this.$refs.changeName -->

    <!-- Conditional rendering
        v-show: hiển thị trên html và bị ẩn bởi css
        v-if: remove khỏi html
        v-else: trường hợp còn lại trong v-if -->

    <!-- List rendering -->
    <input type="text" v-model="newTask" placeholder="add new">
    <button @click="addTask()">Add new</button>
    <div v-for="(task, index) in tasks" :key="index">
      <input type="checkbox" v-model="task.done">
      <span :class="{done: task.done}">{{ task.content }}</span>
    </div>
    <Task v-for="(task, index) in tasks" :key="index" :taskData="tasks"/>
    <hr>
    <TagSelect/>
    <hr>

    <!-- Filters -->
    <h3>{{ total | comma}}</h3>
    <button @click="total += 20000">click</button>
  </div>
</template>

<script>
import Task from './components/Task.vue'
import TagSelect from './components/TagSelect.vue'
export default {
  data(){
    return {
      name: '',
      accept: false,
      isShow: true,
      id: 'show',
      inputDisabled: true,
      selected: true,
      changeName: {
        name: 'hiêu'
      },
      newTask: '',
      tasks: [
        {content: 'bơi', done: false},
        {content: 'chạy', done: false},
        {content: 'đua xe', done: false},
        {content: 'football', done: false}
      ],
      total: 1000000
    }
  },

  components: {
    Task,
    TagSelect
  },

  methods: {
    addTask(){
      this.tasks.push({content: this.newTask, done: false})
    }
  },

  watch: {
    newTask(){
      console.log('new taskk change');
    }
  },

  filters: {
    comma(money){
      return money.toFixed(2).replace(/\d(?=(\d{3})+\.)/g, '$&,');
    }
  }
}
</script>

<style>
.select {
  color: red;
}

.done {
  text-decoration: line-through;
}
</style>