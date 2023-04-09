<template>
  <div class="list">
    <div v-for="(language, index) in languages" 
        :key="index"
        @click="language.selected = !language.selected"
        :class="{active: language.selected}">
        <span>{{language.name}}</span>
    </div>
  </div>
</template>

<script>
export default {
    data(){
        return {
            languages: [
                {name: 'php', selected: false},
                {name: 'ruby', selected: false},
                {name: 'java', selected: false},
                {name: 'vuejs', selected: false},
                {name: 'javascript', selected: false},
                {name: 'phyton', selected: false},
            ]
        }
    }
}
</script>

<style scoped>
.list div {
    display: inline-block;
    border: 1px solid #ebebeb;
    padding: 4px 15px;
    margin-right: 5px;
    border-radius: 4px;
    cursor: pointer;
}

.active {
    background: rgb(101, 101, 238);
    color: #fff;
}
</style>