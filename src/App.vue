<template>
  <div id="app">
    <InputMap/>
    <div class="sort">
      <p>{{ dateList }}</p>
      <button @click.prevent="sortDate">Отсортировать даты</button>
    </div>
    <div class="massive">
      <p>{{ arrayFilter }}</p>
      <button @click.prevent="filterArray">Преобразовать массив</button>
    </div>
    <div class="rework">
      <p>{{ testArray }}</p>
      <button @click.prevent="reworkArray">Преобразовать массив в одномерный</button>
    </div>
  </div>
</template>

<script>
import InputMap from './components/InputMap.vue'

export default {
  name: 'App',
  components: {
    InputMap
  },
  data(){
    return{
      dateList: [{date: '10.01.2017'}, {date: '05.11.2016'}, {date: '11.12.2002'}],
      arrayFilter: [1, 1, 2, 2, 1, 2, 5, 6, 'hi', 2, 'say', 'hi', 1],
      testArray: [1, [2, [3, [4,5]]]]
    }
  },  
  methods:{
    sortDate(){
      this.dateList.sort(function(a, b) {
        let firstDate = new Date(a.date),
            secondDate = new Date(b.date);
        if (firstDate < secondDate) return -1;
        if (firstDate > secondDate) return 1;
        return 0;
      });
    },
    filterArray(){
      this.arrayFilter = [... new Set(this.arrayFilter)]
    },
    reworkArray(){
      this.testArray = this.testArray.flat(Infinity).filter(val => val != null);
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
