<template>
    <div class="row">
      <div class="col">
  
        <!-- ПОЛЯ ДЛЯ ВВОДА -->
        <div class="left">
  
          <div class="boxleft mb-3 form-control">
  
            
            <!-- v-model позволяет связать данные с полями ввода для автоматического обновления значения данных, когда пользователь вводит информацию -->
            <div class="mb-3">
              <label for="exampleFormControlInput1" class="form-label">Укажите вашу профессию</label>
              <input v-model="profession" type="text" class="form-control" id="exampleFormControlInput1"
                placeholder="Например, врач">
            </div>
  
            <div class="mb-3">
              <label for="exampleFormControlInput1" class="form-label">Укажите ваш город</label>
              <input v-model="city" type="text" class="form-control" id="exampleFormControlInput1"
                placeholder="Например, Москва">
            </div>
  
            <div class="mb-3">
              <label for="formFile" class="form-label">Загрузите ваше фото</label>
              <input v-model="photo" class="form-control" type="text" id="formFile">
            </div>
  
            <div class="mb-3">
              <label for="exampleFormControlInput1" class="form-label">Укажите ваше ФИО</label>
              <input v-model="fio" type="text" class="form-control" id="exampleFormControlInput1"
                placeholder="Например, Иванов Иван Иванович">
            </div>
  
            <div class="mb-3">
              <label for="exampleFormControlInput1" class="form-label">Укажите ваш телефон</label>
              <input v-model="phone" type="text" @keyup="validatePhone" class="form-control" id="exampleFormControlInput1"
                placeholder="Например, +79005557766">
              <p>{{ validPhone }}</p>
            </div>
  
  
            <div class="mb-3">
              <label for="exampleFormControlInput1" class="form-label">Укажите ваш E-mail</label>
              <input v-model="mail" type="email" class="form-control" id="exampleFormControlInput1"
                placeholder="Например, ivanov@mail.ru">
            </div>
  
  
            <div class="mb-3">
              <label for="exampleFormControlInput1" class="form-label">Укажите вашу дату рождения</label>
              <input v-model="birthday" type="date" class="form-control" id="exampleFormControlInput1">
            </div>
  
            <div class="mb-3">
              <label for="exampleFormControlInput1" class="form-label">Укажите ваше образование</label>
              <select v-model="education" class="form-select" id="educationSelect">
                <option value="Среднее">Среднее</option>
                <option value="Среднее специальное">Среднее специальное</option>
                <option value="Неоконченное высшее">Неоконченное высшее</option>
                <option value="Высшее">Высшее</option>
              </select>
            </div>
  
            <!-- Поля для дополнительной информации об образовании -->
            <div v-if="education !== 'Среднее'">
              <div class="mb-3">
                <label for="educationInstitution" class="form-label">Учебное заведение</label>
                <input v-model="educationInstitution" type="text" class="form-control" id="educationInstitution">
              </div>
  
              <div class="mb-3">
                <label for="faculty" class="form-label">Факультет</label>
                <input v-model="faculty" type="text" class="form-control" id="faculty">
              </div>
  
              <div class="mb-3">
                <label for="specialization" class="form-label">Специализация</label>
                <input v-model="specialization" type="text" class="form-control" id="specialization">
              </div>
              <div class="mb-3">
                <label for="graduationYear" class="form-label">Год окончания</label>
                <input v-model="graduationYear" type="text" class="form-control" id="graduationYear">
              </div>
            </div>
  
            <div class="mb-3">
              <label for="exampleFormControlInput1" class="form-label">Укажите ваше предпочтение в зарплате</label>
              <input v-model="salary" type="text" class="form-control" id="exampleFormControlInput1"
                placeholder="Например, 1000000">
            </div>
  
            <div class="mb-3">
              <label for="exampleFormControlInput1" class="form-label">Укажите ваши ключевые навыки</label>
              <input v-model="skills" type="text" class="form-control" id="exampleFormControlInput1"
                placeholder="Например, ответственность">
            </div>
  
            <div class="mb-3">
              <label for="exampleFormControlInput1" class="form-label">Расскажите о себе</label>
              <input v-model="about" type="text" class="form-control" id="exampleFormControlInput1"
                placeholder="Что бы вы хотели еще рассказать">
            </div>
            <button @click="applyData" class="btn btn-primary">Применить</button>
          </div>
  
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        profession: 'Программист',
        city: 'Dubai',
        photo: 'https://proprikol.ru/wp-content/uploads/2020/02/kartinki-na-avatarku-dlya-parnej-i-muzhchin-1-1.jpg',
        fio: 'Иванов Иван Иванович',
        phone: '+79594893212',
        validPhone: '',
        mail: 'ivanchik@mail.ru',
        birthday: '2000-11-12',
        education: 'Высшее',
        salary: '90000',
        skills: 'Отвественность, обучаемость, пунктуальность',
        about: 'Люблю кушать и программировать. Нравиться путешествовать и узнавать что-то новое!',
        dataApplied: false
      };
    },
    methods: {
      validatePhone() {
        const phoneRegex = /^\+7\d{10}$/; // Регулярное выражение для проверки номера
        if (phoneRegex.test(this.phone)) {
          this.validPhone = 'Валидный номер';
        } else {
          this.validPhone = 'Невалидный номер';
        }
      },
      applyData() {
        this.$emit('applyData', {
          photo: this.photo,
          fio: this.fio,
          birthday: this.birthday,
          profession: this.profession,
          city: this.city,
          phone: this.phone,
          mail: this.mail,
          education: this.education,
          educationInstitution: this.educationInstitution,
          faculty: this.faculty,
          specialization: this.specialization,
          graduationYear: this.graduationYear,
          salary: this.salary,
          skills: this.skills,
          about: this.about,
        });
      }
    }
  };
  </script>
  
  <style scoped>
  .left {
    width: 30%;
    margin: 20px;
  }
  
  .form-control {
    margin-top: 10px;
  }
  </style>
  
  
  