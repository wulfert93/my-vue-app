<template>
  <!-- <v-container> -->
    <v-app>
    <h1>{{message}}</h1>
    <input v-model="name" placeholder="vul je naam in: ">
    <input v-model="length" placeholder="vul lengte in: ">
    <p>Jouw lengte: {{length}} </p>
    <input v-model="weight" placeholder="vul gewicht in: " @keydown.enter="roundOne">
    <p>Jouw gewicht: {{weight}}</p>
    <!-- <p v-if="type===number">Jouw BMI: {{Math.round((weight / ((Math.pow(length/100, 2)))))}}</p> -->
    <p v-if="typeof this.bmis==number">Jouw BMI: {{bmis}}</p>
    <p v-else>Waardebon</p>
    <div id="button">
      <button v-on:click="addBmi">voeg toe</button>
    </div>
    <ul id="list">
      <li v-for="item in list" :key="item.id">
        {{item.name}}, {{item.bmi}}
        <div id="buttonRemove">
          <button v-on:click="removeBmi">haal weg</button>
        </div>
      </li>
    </ul>
    <List/>
    </v-app>
  <!-- </v-container> -->
</template>

<script>
import List from './List.vue';
  export default {
    props: [],
    name: 'Home',
    data: () => ({
      message: 'Vue BMI calculator',
      length: null,
      weight: null,
      list: [
        {
          name: 'willem',
          bmi: 0,
        },
        { 
          name: 'sarah',
          bmi: 0,
        }
      ],
      name: ''
    }),
    methods: {
      addBmi: function () {
        alert('banaan');
        // this.list.push(bmi: )
        this.list.push(
          {
            bmi: this.bmis,
            name: this.name
          }
        )
      },
      removeBmi: function(){
        alert('banaans');

      }},
    computed: {
      bmis:
        function () {
          return Math.round(this.weight / (Math.pow(this.length / 100, 2)));
      }
    }
      // roundOne () {
      // const roundOne = (n, d) => Math.round(n * Math.pow(10, d)) / Math.pow(10, d)
    }
</script>
