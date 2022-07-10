<script setup lang="ts">
import { Gender, Popularity, Length, names, Name } from '@/data'

interface OptionsState {
  gender: Gender;
  popularity: Popularity;
  length: Length;
}



const options: OptionsState = reactive<OptionsState>(
  {
    gender: Gender.GIRL,
    length: Length.ALL,
    popularity: Popularity.UNIQUE,
  }
)

const selectednNames = ref<Name[]>([])


const computedSelectedNames = () => {
  const fitlerNames = names
  .filter((name) => name.gender === options.gender)
  .filter((name) => name.popularity = options.popularity)
  .filter((name)=>{
    if(options.length === Length.ALL) return true
    else return name.length === options.length  
  })

  selectednNames.value = fitlerNames



}

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
        <button class="option option-left" :class="options.gender === Gender.BOY && 'option-active'"
          @click="options.gender = Gender.BOY">
          {{ Gender.BOY }}
        </button>
        <button class="option" :class="options.gender === Gender.UNISEX && 'option-active'"
          @click="options.gender = Gender.UNISEX">
          {{ Gender.UNISEX }}
        </button>
        <button class="option option-right" :class="options.gender === Gender.GIRL && 'option-active'"
          @click="options.gender = Gender.GIRL">
          {{ Gender.GIRL }}
        </button>
      </div>
    </div>
    <div class="option-container">
      <h4>2)Choose the name's popularity</h4>
      <div class="option-buttons">
        <button class="option option-left" :class="options.popularity === Popularity.TRENDY && 'option-active'"
          @click="options.popularity = Popularity.TRENDY">
          {{ Popularity.TRENDY }}
        </button>
        <button class="option option-right" :class="options.popularity === Popularity.UNIQUE && 'option-active'"
          @click="options.popularity = Popularity.UNIQUE">
          {{ Popularity.UNIQUE }}
        </button>
      </div>
    </div>
    <div class="option-container">
      <h4>3)Choose the name's length</h4>
      <div class="option-buttons">
        <button class="option option-left" :class="options.length === Length.LONG && 'option-active'"
          @click="options.length = Length.LONG">
          {{ Length.LONG }}
        </button>
        <button class="option" :class="options.length === Length.ALL && 'option-active'"
          @click="options.length = Length.ALL">
          {{ Length.ALL }}
        </button>
        <button class="option option-right" :class="options.length === Length.SHORT && 'option-active'"
          @click="options.length = Length.SHORT">
          {{ Length.SHORT }}
        </button>
      </div>
    </div>

    <button class="primary" @click="computedSelectedNames">Find Names</button>

    {{  selectednNames  }}
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

