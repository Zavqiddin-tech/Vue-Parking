<template>
  <div class="app">
    <div class="btn-group">
      <button
        @click="this.toggle = 'form'"
        class="btn"
        :class="{ active: toggle == 'form' }"
      >
        Form
      </button>
      <button
        @click="this.toggle = 'main'"
        class="btn"
        :class="{ active: toggle == 'main' }"
      >
        Bosh sahifa
      </button>
      <button
        @click="this.toggle = 'table'"
        class="btn"
        :class="{ active: toggle == 'table' }"
      >
        Table
      </button>
    </div>
    <div class="main">
      <div v-show="toggle == 'form'">
        <Form
          @zakaz="
            (val) => {
              newCars(val);
            }
          "
          v-bind:massiv="mainCars"
        />
      </div>
      <div v-show="toggle == 'main'">
        <div class="logo">Car <span>parking</span></div>
        <div class="cards">
          <div class="card">
            Bo'sh joy
            <div class="card-title">{{ boshJoy - mainCars.length }} ta</div>
          </div>
          <div class="card">
            Band joylar
            <div class="card-title">{{ mainCars.length }} ta</div>
          </div>
          <div class="card">
            Mashinalar soni
            <div class="card-title">{{ mainCars.length }} ta</div>
          </div>
        </div>
        <div class="stop" v-show="mainCars.length == 20">Bo'sh joy qolmadi</div>
      </div>
      <div v-show="toggle == 'table'">
        <Table v-bind:massiv="mainCars" />
      </div>
    </div>
  </div>
</template>

<script>
import Form from "./components/form.vue";
import Table from "./components/table.vue";
export default {
  components: {
    Form,
    Table,
  },
  data() {
    return {
      toggle: "main",
      boshJoy: 20,
      mainCars: [],
    };
  },
  methods: {
    newCars(cars) {
      this.mainCars.push(cars);
      localStorage.setItem('localCar', JSON.stringify(this.mainCars))
      this.mainCars = JSON.parse(localStorage.getItem('localCar'))
    },
    mounted() {
      this.mainCars = JSON.parse(localStorage.getItem('localCar'))
    },
  }, 

};
</script>

<style lang="scss">
@import "@/styles/main.scss";
</style>
