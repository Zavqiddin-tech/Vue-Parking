<template>
  <div class="form">
    <div class="form-wrapper">
        <span>Moshina modeli</span>
      <select v-model="car.model">
        <option v-for="moshina of moshinalar" :value="moshina">
          {{ moshina }}
        </option>
      </select>
    </div>
    <div class="form-wrapper">
        <span>Moshina nomi</span>
      <input v-model="car.name" type="text"/>
    </div>
    <div class="form-wrapper">
        <span>Qachongacha qolishi</span>
        <input v-model="car.date" type="date" >
    </div>
    <button @click="addCar()" class="form-btn">Kiritish</button>
</div>
</template>
<script>
export default {
  props: ['massiv'],
  data() {
    return {
      moshinalar: [
        "Chevrolet",
        "BMV",
        "Mercedes",
        "Hyundai",
        "Kia",
        "Wolsvagin",
      ],
      car: {},
    };
  },
  methods: {
    addCar() {
      if(this.car.model && this.car.name && this.car.date) {
        if(this.massiv.length == 20) {
          alert('Joylar to`lgan uzr ⛔')
          return false
        }
        else {
          let time  = new Date()
          this.car.time = time
          this.$emit('zakaz', this.car)
          console.log(this.car);
          this.car = {}
        }
      } else {
        alert('Iltimos maydonlarni to`ldiring 🤨')
      }
    }
  }
};
</script>
<style>
    @import '@/styles/form.scss'
</style>
