<script setup lang="ts">
import axios from 'axios'
import {onMounted, ref, watch} from 'vue'
import Header from './components/Header.vue'
import Sidenav from './components/Sidenav.vue'
import Card from './components/Card.vue'
import Button from './components/Button.vue'

const cars = ref()
const num_car = ref(0)
const per_page = ref(20)
const total = ref(0)
const current_page = ref(1)
const pages = ref(0)
const search = ref('')

const fetchData = async () => {
  const search_query = ref('?')
  if (search.value != '') {
    search_query.value += `search=${search.value}&`;
  }
  if (per_page.value != total.value) {
    search_query.value += `per_page=${per_page.value}&`;
  }
  if (current_page.value != 1) {
    search_query.value += `page=${current_page.value}&`;
  }
  const data = await axios(`https://api.caiman-app.de/api/cars-test${search_query.value}`)
  cars.value = data.data.data;
  total.value = data.data.meta.total;
  pages.value = data.data.meta.last_page;
  current_page.value = data.data.meta.current_page;
  num_car.value = data.data.data.length;
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  });
}

onMounted(async () => {
  await fetchData()
})

const changePerPage = (event: any) => {
  per_page.value = event.target.value;
  current_page.value = 1;
}

const inputSearch = (event: any) => {
  search.value = event.target.value;
  current_page.value = 1;
}

const previousPage = () => {
  if (current_page.value > 1) {
    current_page.value -= 1;
  }
}

const nextPage = () => {
  if (current_page.value < pages.value) {
    current_page.value += 1;
  }
}

watch(search, fetchData)
watch(per_page, fetchData)
watch(current_page, fetchData)
</script>

<template>
  <div class="wrapper">
    <Sidenav></Sidenav>
    <div class="main">
      <Header :total="total"></Header>
      <div class="main__filters">
        <div class="filters">
            <input class="body_font text_dark-grey" :value="search" @input="inputSearch" placeholder="Search VIN" />
            <div>
                <span class="body_font text_black">Select vehicles per page:</span>
                <select  class="body_font text_black" :value="per_page" @change="changePerPage">
                    <option v-for="num in total" :key="num" :value="num">{{num}}</option>
                </select>
            </div>
        </div>
        <Button><span class="button2_font text_white">ADD VEHICLE</span></Button>
    </div>
      <div class="main__container">
        <Card
          v-for="car in cars"
          :key="car.id"
          :name="car.vehicle_name"
          :vin="car.vin"
          :url="car.preview"
          :uploads="car.uploads"
        >
        </Card>
      </div>
      <footer>
        <div class="text_dark-grey">Showing {{ num_car }} out of {{ total }} </div>
        <div class="pages">
          <img class="page_switch" @click="previousPage" src="./assets/icons/chevron_left.svg" alt="previous">
          <div class="page text_dark-grey" id="current">{{ current_page }}</div>
          <span class="of text_dark-grey">of</span>
          <div class="page text_light-grey">{{ pages }}</div>
          <img class="page_switch" @click="nextPage" id="right" src="./assets/icons/chevron_left.svg" alt="next">
        </div>
      </footer>
    </div>
    
  </div>
</template>

<style scoped>
.wrapper {
  display: grid;
  grid-template-columns: 256px 1fr;
  height: 100vh;
}
.main__filters {
    margin: 36px 32px 0 30px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.filters {
    display: flex;
    gap: 32px;
}
input {
    height: 42px;
    width: 354px;
    box-sizing: border-box;
    padding: 9px 16px;
    border-radius: 8px;
    border: 1px solid #E4E4E4;
    cursor: pointer;
}
select {
    height: 42px;
    width: 82px;
    margin-left: 16px;
    border-radius: 8px;
    border: 1px solid #E4E4E4;
    padding: 9px 16px;
    appearance: none;
    background: url(./assets/icons/arrow_down.svg) no-repeat right;
    background-position-x: calc(100% - 16px);
    cursor: pointer;
}
.main__container {
  margin: 32px;
  display: grid;
  grid-template-columns: repeat(auto-fill, 354px);
  gap: 30px;
}
footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0 30px 45px 30px;
}
.pages {
  display: flex;
  gap: 12px;
  align-items: center;
}
.page_switch {
  cursor: pointer;
}
.page {
  width: 32px;
  height: 32px;
  border: 1px solid #E4E4E4;
  border-radius: 6px;
  text-align: center;
  align-content: center;
}
.of {
  font-family: "DMSans-Regular";
  font-size: 13px;
  line-height: 24px;
}
#right {
  rotate: 180deg;
}
</style>
