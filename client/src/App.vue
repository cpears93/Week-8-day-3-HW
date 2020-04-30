<template>
  <div id="app">
    <div class="flex">
      <dog-cat-form />
    </div>
    <div class="flex">
      <button @click="show='dogs'">Show Dogs</button>
      <button @click="show='cats'">Show Cats</button>
    </div>

    <div class="flex container">

        <dog-list v-if="show === 'dogs'" :dogs="dogs" />
        <cat-list v-if="show === 'cats'" :cats="cats" />
    </div>

  </div>
</template>

<script>
import DogCatForm from '@/components/DogCatForm';
import DogList from '@/components/DogList';
import CatList from '@/components/CatList';

import { eventBus } from './main';

export default {
  name: 'app',
  data () {
    return {
      dogs: [],
      cats: [],
      show: ""
    }
  },
  methods: {
    fetchData(){
      fetch("http://localhost:3000/api/dogs")
      .then(response => response.json())
      .then(dogs => this.dogs = dogs);

      fetch("http://localhost:3000/api/cats")
      .then(response => response.json())
      .then(cats => this.cats = cats);
    }
  },
  mounted() {
    this.fetchData();

    eventBus.$on("refresh-data", (type) => {
      console.log(type);
      this.show = type;
      this.fetchData()
    });
  },
  components: {
    'dog-cat-form': DogCatForm,
    'dog-list': DogList,
    'cat-list': CatList
  }
}
</script>

<style>

.flex-row {
  justify-content: space-between;
  flex-direction: row;
}

button {
  color: #494949 !important;
  text-transform: uppercase;
  text-decoration: none;
  background: #ffffff;
  padding: 20px;
  border: 4px solid #494949 !important;
  display: inline-block;
  transition: all 0.4s ease 0s;
  margin: 5px;
}

button:hover {
  color: #ffffff !important;
  background: #1abc9c;
  border-color: #1abc9c !important;
  transition: all 0.4s ease 0s;
}
</style>
