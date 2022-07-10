<script setup lang="ts">
let myName: string = "Latith"


enum Gender {
  GIRL = 'Girl',
  BOY = 'Boy',
  UNISEX = "Unisex"
}

enum Lenght {
  LONG = 'Long',
  ALL = 'All',
  SHORT = "Short"
}

enum Popularity {
  TRENDY = 'Trendy',
  UNIQUE = 'Unique',

}

interface OptionsState {
  gender: Gender;
  popularity: Popularity;
  length: Lenght;
}



const options: OptionsState = reactive<OptionsState>(
  {
    gender: Gender.GIRL,
    length: Lenght.ALL,
    popularity: Popularity.UNIQUE,
  }
)



</script>

<template>
  <div class="container">
    <h1>Baby Name Generator </h1>
    <p>Choose your options and click the "Find Names" buttom below </p>
  </div>
  <div class="options-container">
    <div class="option-container">
      <h4>1)Choose a Gender</h4>
      <div class="option-buttons">
        <button class="option option-left" :class="options.gender === Gender.BOY && 'option-active'">
          {{ Gender.BOY }}
        </button>
        <button class="option" :class="options.gender === Gender.UNISEX && 'option-active'">
          {{ Gender.UNISEX }}
        </button>
        <button class="option option-right" :class="options.gender === Gender.GIRL && 'option-active'">
          {{ Gender.GIRL }}
        </button>
      </div>
    </div>
    <div class="option-container">
      <h4>2)Choose the name's popularity</h4>
      <div class="option-buttons">
        <button class="option option-left" :class="options.popularity === Popularity.TRENDY && 'option-active'">
          {{ Popularity.TRENDY }}
        </button>
        <button class="option option-right" :class="options.popularity === Popularity.UNIQUE && 'option-active'">
          {{ Popularity.UNIQUE }}
        </button>
      </div>
    </div>
    <div class="option-container">
      <h4>3)Choose the name's length</h4>
      <div class="option-buttons">
        <button class="option option-left" :class="options.length === Lenght.LONG && 'option-active'">
          {{ Lenght.LONG }}
        </button>
        <button class="option" :class="options.length === Lenght.ALL && 'option-active'">
          {{ Lenght.ALL }}
        </button>
        <button class="option option-right" :class="options.length === Lenght.SHORT && 'option-active'">
          {{ Lenght.SHORT }}
        </button>
      </div>
    </div>
  </div>
</template>
<style scoped>
.container {
  font-family: Arial, Helvetica, sans-serif;
  color: rgb(27, 60, 138);
  max-width: 50rem;
  margin: 0 auto;
  text-align: center;
}

h1 {
  font-size: 3rem;
}

.options-container {
  background-color: rgb(255, 238, 236);
  border-radius: 2rem;
  padding: 1rem;
  width: 95%;
  margin: 0 auto;
  margin-top: 4rem;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.primary {
  background-color: rgb(249, 87, 89);
  color: white;
  border-radius: 6.5rem;
  border: none;
  padding: 0.75rem 4rem;
  font-size: 1rem;
  margin-top: 1rem;
  cursor: pointer;
}

.cards-container {
  display: flex;
  margin-top: 3rem;
  flex-wrap: wrap;
}

.option {
  background-color: white;
  outline: 0.15rem solid rgb(249, 87, 89);
  border: none;
  padding: 0.75rem;
  width: 12rem;
  font-size: 1rem;
  color: rgb(27, 60, 138);
  cursor: pointer;
  font-weight: 200;
}

.option-left {
  border-radius: 1rem 0 0 1rem;

}

.option-right {
  border-radius: 0 1rem 1rem 0;
}

.option-active {
  background-color: rgb(249, 87, 89);
  color: white;
}
</style>

