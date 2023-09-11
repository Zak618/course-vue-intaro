<template>
  <div class="row">
    <div class="col">
      <div class="left">

        <div class="boxleft mb-3 form-control">

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
            <input v-model="phone" type="text" class="form-control" id="exampleFormControlInput1"
              placeholder="Например, +79005557766">
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
            <input v-model="education" type="text" class="form-control" id="exampleFormControlInput1"
              placeholder="Например, Москва">
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
        </div>

      </div>
    </div>


    <div class="right">
      <div class="boxright mb-3 form-control">

        <div class="mb-3 fs-2">
          <p>Ваше резюме: </p>
        </div>

        <div class="mb-3">
          <img :src="photo" class="photo img-fluid" alt="Ваша фотография">
        </div>

        <div class="form-control">
          <div class="mb-3 fs-5">
            <p class="fs-5">Ваше ФИО: </p>
            <p class="fs-6">{{ fio }}</p>
          </div>
        </div>

        <div class="form-control">
          <div class="mb-3 fs-5">
            <p class="fs-5">Ваша дата рождения: </p>
            <p class="fs-6">{{ birthday }}</p>
          </div>
        </div>

        <div class="form-control">
          <div class="mb-3 fs-5">
            <p class="fs-5">Ваша профессия: </p>
            <p class="fs-6">{{ profession }}</p>
          </div>
        </div>

        <div class="form-control">
          <div class="mb-3 fs-5">
            <p class="fs-5">Ваш город: </p>
            <p class="fs-6">{{ city }}</p>
          </div>
        </div>
        <div class="form-control">
          <div class="mb-3 fs-5">
            <p class="fs-5">Ваш номер телефона: </p>
            <p class="fs-6">{{ phone }}</p>
          </div>
        </div>

        <div class="form-control">
          <div class="mb-3 fs-5">
            <p class="fs-5">Ваша почта: </p>
            <p class="fs-6">{{ mail }}</p>
          </div>
        </div>

        <div class="form-control">
          <div class="mb-3 fs-5">
            <p class="fs-5">Ваше образование: </p>
            <p class="fs-6">{{ education }}</p>
          </div>
        </div>
        <div class="form-control">
          <div class="mb-3 fs-5">
            <p class="fs-5">Желаемая зарплата: </p>
            <p class="fs-6">{{ salary }}</p>
          </div>
        </div>

        <div class="form-control">
          <div class="mb-3 fs-5">
            <p class="fs-5">Ключевые навыки: </p>
            <p class="fs-6">{{ skills }}</p>
          </div>
        </div>

        <div class="form-control">
          <div class="mb-3 fs-5">
            <p class="fs-5">О себе: </p>
            <p class="fs-6">{{ about }}</p>
          </div>
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
      mail: 'ivanchik@mail.ru',
      birthday: '2000-11-12',
      education: 'Высшее',
      salary: '90000',
      skills: 'Отвественность, обучаемость, пунктуальность',
      about: 'Люблю кушать и программировать. Нравиться путешествовать и узнавать что-то новое!'
    }
  }
}

</script>

<style lang="css" scoped>
.left {
  width: 70%;
  margin: 20px;
}

.right {
  margin: 20px;
  width: 50%;
}

.photo {
  width: 30%;
  height: 30%;
  border-radius: 50px;
}

.form-control {
  margin-top: 10px;
}</style>