<template>
  <div class="brews">
    <h2>Brew Search</h2>
    <section>
      <form @submit.prevent="submitted">
        <input v-model="val" type="text" />
        <button>Submit</button>
      </form>
    </section>
    <div v-if="error">
      <h2>erorr!! {{ error }}</h2>
    </div>
    <div v-if="fetching"><h2>Fetching Data!</h2></div>
    <div class="search-results" v-for="brewery in list" :key="brewery.id">
      <ul>
        <li><span class="title">Id:</span> <span class="brew">{{ brewery.id }}</span></li>
        <li><span class="title">Modes:</span> <span class="brew">{{ brewery.mode}}</span></li>
      </ul>
    </div>
  </div>
</template>

<script>
import useBrewList from "../composition/use-brew-list";


import {createComponent} from '@vue/composition-api';
export default createComponent({
  setup() {
    const { submitted, list, val, error, fetching } = useBrewList();
    return {
      val,
      list,
      submitted,
      error,
      fetching
    };
  }
});
</script>

<style scoped>
.search-results {
  display: flex;
  width: 600px;
  text-align: left;
}
.brews {
  max-width: 1024px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin: 0 auto;
}
ul {
  list-style-type: none;
  width: 100%;
}
li {
  display: flex;
  justify-content: space-between;
}
.brew {
  font-weight: bold;
}

</style>
