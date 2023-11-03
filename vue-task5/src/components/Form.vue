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
            <label for="cityInput" class="form-label">Укажите ваш город</label>
            <input v-model="city" @input="fetchCitySuggestions" type="text" class="form-control" id="cityInput"
              placeholder="Начните вводить город">
          </div>

          <!-- Добавляем выпадающий список с подсказками -->
          <ul v-if="citySuggestions.length" class="list-group">
            <li class="list-group-item" v-for="suggestion in citySuggestions" :key="suggestion.id"
              @click="selectCitySuggestion(suggestion)">{{ suggestion.title }}</li>
          </ul>




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

          <button @click="addEducation" class="btn btn-secondary">Указать еще одно место обучения</button>

          <div v-for="(educationBlock, index) in educationBlocks" :key="index">

          <div class="mb-3">
            <label for="educationSelect" class="form-label">Укажите ваше образование</label>
            <select v-model="educationBlock.education" class="form-select" id="educationSelect">
              <option value="Среднее">Среднее</option>
              <option value="Среднее специальное">Среднее специальное</option>
              <option value="Неоконченное высшее">Неоконченное высшее</option>
              <option value="Высшее">Высшее</option>
            </select>
          </div>
        
          <!-- Поля для дополнительной информации об образовании -->
          <div v-if="educationBlock.education !== 'Среднее'">
            <div class="mb-3">
              <label for="educationInstitution" class="form-label">Учебное заведение</label>
              <input v-model="educationInstitution" @input="fetchUniversitySuggestions" type="text" class="form-control"
                id="educationInstitution">
            </div>

            <ul v-if="universitySuggestions.length" class="list-group">
              <li class="list-group-item" v-for="suggestion in universitySuggestions" :key="suggestion.id"
                @click="selectUniversitySuggestion(suggestion)">{{ suggestion.title }}</li>
            </ul>


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

          <button @click="removeEducation(index)" class="btn btn-danger">Удалить</button>
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
          <div class="mb-3">
            <label for="statusSelect" class="form-label">Выберите статус</label>
            <select v-model="status" class="form-select" id="statusSelect">
              <option value="Новый">Новый</option>
              <option value="Назначено собеседование">Назначено собеседование</option>
              <option value="Принят">Принят</option>
              <option value="Отказ">Отказ</option>
            </select>
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
      educationBlocks: [{ education: 'Высшее' }],
      salary: '90000',
      skills: 'Отвественность, обучаемость, пунктуальность',
      about: 'Люблю кушать и программировать. Нравиться путешествовать и узнавать что-то новое!',
      dataApplied: false,
      status: 'Новый',
      citySuggestions: [], // Массив подсказок городов
      selectedCitySuggestion: '', // Выбранная подсказка
      universitySuggestions: [], // Массив подсказок университетов
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
        educationBlocks: this.educationBlocks,
        educationInstitution: this.educationInstitution,
        faculty: this.faculty,
        specialization: this.specialization,
        graduationYear: this.graduationYear,
        salary: this.salary,
        skills: this.skills,
        about: this.about,
        status: this.status,
      });
    },
    async fetchCitySuggestions() {
      if (this.city.length < 3) {
        // Если введено менее 3 символов, не делаем запрос к API
        this.citySuggestions = [];
        return;
      }

      try {
        const apiKey = 'vk1.a.ZbP5wN4uJNxwLZC1l5YIvlMN36hQo5U6KnkmBR6IqmsjxAj0QAjlBLf1wCgdvypKtDS1Mqs3tozauQANS46SnoMnrwEQddZOdexvt-BwsF8warEKtkwaDwjS8Jb8LGTIEgnVJKJ687AGKpMLn7bWH8E04dl8CVmZcmBkEOjtnlcoaxoIlB-SsLD8vf3X46rvWTYTl6_x1drLf-tfv86Cdw';
        const callbackName = 'handleCitySuggestions'; // Уникальное имя обратного вызова

        // Создайте элемент скрипта для выполнения JSONP-запроса
        const script = document.createElement('script');
        script.src = `https://api.vk.com/method/database.getCities?q=${this.city}&country_id=1&v=5.131&access_token=${apiKey}&callback=${callbackName}`;

        // Определите глобальную функцию для обработки ответа
        window[callbackName] = (data) => {
          // Обработайте полученные данные
          if (data.response) {
            // Извлекаем массив подсказок из ответа API
            this.citySuggestions = data.response.items;
          }
        };

        document.body.appendChild(script);
      } catch (error) {
        console.error('Ошибка при запросе подсказок городов:', error);
        this.citySuggestions = [];
      }

    },
    async fetchUniversitySuggestions() {
      if (this.educationInstitution.length < 3) {
        // Если введено менее 3 символов, не делаем запрос к API
        this.universitySuggestions = [];
        return;
      }

      try {
        const apiKey = 'vk1.a.ZbP5wN4uJNxwLZC1l5YIvlMN36hQo5U6KnkmBR6IqmsjxAj0QAjlBLf1wCgdvypKtDS1Mqs3tozauQANS46SnoMnrwEQddZOdexvt-BwsF8warEKtkwaDwjS8Jb8LGTIEgnVJKJ687AGKpMLn7bWH8E04dl8CVmZcmBkEOjtnlcoaxoIlB-SsLD8vf3X46rvWTYTl6_x1drLf-tfv86Cdw';
        const callbackName = 'handleUniversitySuggestions'; // Уникальное имя обратного вызова

        // Создайте элемент скрипта для выполнения JSONP-запроса
        const script = document.createElement('script');
        script.src = `https://api.vk.com/method/database.getUniversities?q=${this.educationInstitution}&country_id=1&v=5.131&access_token=${apiKey}&callback=${callbackName}`;

        // Определите глобальную функцию для обработки ответа
        window[callbackName] = (data) => {
          // Обработайте полученные данные
          if (data.response) {
            // Извлекаем массив подсказок из ответа API
            this.universitySuggestions = data.response.items;
          }
        };

        document.body.appendChild(script);
      } catch (error) {
        console.error('Ошибка при запросе подсказок университетов:', error);
        this.universitySuggestions = [];
      }
    },

    selectCitySuggestion(suggestion) {
      // Обработка выбранной подсказки
      this.city = suggestion.title;
      this.citySuggestions = []; // Очищаем список подсказок
    },
    selectUniversitySuggestion(suggestion) {
      // Обработка выбранной подсказки
      this.educationInstitution = suggestion.title;
      this.universitySuggestions = []; // Очищаем список подсказок
    },
    addEducation() {
      this.educationBlocks.push({ education: 'Высшее' });
    },

    // Функция для удаления блока образования по индексу
    removeEducation(index) {
      this.educationBlocks.splice(index, 1);
    },

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
  
  
  