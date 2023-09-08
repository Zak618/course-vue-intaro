<template>
  <div class="boxing bg-danger-subtle">
    <div class="boxnum form-control">
      <p class="fs-4 fw-bold">Футы в метры</p>
      <div class="box1">
        <p class="fs-6 fw-bold">Футы:</p>
        <input v-model="feet" @input="convertToMeters" class="form-control form-control-lg" type="text">
      </div>
      <div class="box2">
        <p class="fs-6 fw-bold">Метры:</p>
        <input v-model="meters" @input="convertToFeet" class="form-control form-control-lg" type="text">
      </div>

    </div>
  </div>


  <div class="boxing">
    <div class="boxnum form-control bg-primary-subtle">
      <p class="fs-4 fw-bold">Морские мили в километры</p>
      <div class="box1">
        <p class="fs-6 fw-bold">Мили:</p>
        <input v-model="miles" @input="convertToKilometers" class="form-control form-control-lg" type="text">
      </div>
      <div class="box2">
        <p class="fs-6 fw-bold">Километры:</p>
        <input v-model="kilometers" @input="convertToMiles" class="form-control form-control-lg" type="text">
      </div>

    </div>
  </div>

  <div class="boxing bg-danger-subtle">
    <div class="boxnum form-control">
      <p class="fs-4 fw-bold">Градусы в радианы</p>
      <div class="box1">
        <p class="fs-6 fw-bold">Градусы:</p>
        <input v-model="degrees" @input="convertToRadians" class="form-control form-control-lg" type="text">
      </div>
      <div class="box2">
        <p class="fs-6 fw-bold">Радианы:</p>
        <input v-model="radians" @input="convertToDegrees" class="form-control form-control-lg" type="text">
      </div>

    </div>
  </div>

  <div class="boxing">
    <div class="boxnum form-control bg-primary-subtle">
      <p class="fs-4 fw-bold">Температура по Цельсию в температуру по Фаренгейту</p>
      <div class="box1">
        <p class="fs-6 fw-bold">Температура по Цельсию:</p>
        <input v-model="celsius" @input="convertToFahrenheit" class="form-control form-control-lg" type="text">
      </div>
      <div class="box2">
        <p class="fs-6 fw-bold">Температура по Фаренгейту:</p>
        <input v-model="fahrenheit" @input="convertToCelsius" class="form-control form-control-lg" type="text">
      </div>

    </div>
  </div>
</template>

<script>
export default {
  // Создаем константы с исходными данными
  data() {
    return {
      feet: 0,
      meters: 0,
      Femeter: 3.28,
      miles: 0,
      kilometers: 0,
      Kilomiles: 1.61,
      degrees: 0,
      radians: 0,
      Degradians: 57.3,
      celsius: 0,
      fahrenheit: 0,
    }
  },

  methods: {
    convertToFeet() {
      this.feet = this.meters * this.Femeter;
    },

    convertToMeters() {
      this.meters = this.feet / this.Femeter;
    },

    convertToMiles() {
      this.miles = this.kilometers / this.Kilomiles;
    },

    convertToKilometers() {
      this.kilometers = this.miles * this.Kilomiles;
    },

    convertToDegrees() {
      this.degrees = this.radians * this.Degradians;
    },

    convertToRadians() {
      this.radians = this.degrees / this.Degradians;
    },

    convertToCelsius() {
      this.celsius = 5/9 * (this.fahrenheit - 32);
    },

    convertToFahrenheit() {
      this.fahrenheit = 1.8 * this.celsius + 32;
    },
  }
}

// Методы для перевода единиц измерения

</script>

<style lang="css" scoped>
.boxing {
  display: flex;
  justify-content: center;
}

.boxnum {
  width: 30%;
  margin: 20px;

}


.box2 {
  margin-top: 10px;
}
</style>