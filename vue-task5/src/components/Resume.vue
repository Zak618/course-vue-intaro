<template>
    <div class="right">
      <div class="boxright mb-3 form-control" v-if="dataApplied">
        <!-- ПОЛЯ ОТОБРАЖЕНИЯ -->
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
  
        <div class="form-control" v-for="(educationBlock, index) in educationBlocks" :key="index">
          <div class="mb-3 fs-5">
            <p class="fs-5">Ваше образование: </p>
            <p>Образование: {{ educationBlock.education }}</p>
          </div>
        </div>
  
        <div v-if="education !== 'Среднее'">
          <div class="form-control">
          <h2>Информация об образовании:</h2>
          <p>Учебное заведение: {{ educationInstitution }}</p>
          <p>Факультет: {{ faculty }}</p>
          <p>Специализация: {{ specialization }}</p>
          <p>Год окончания: {{ graduationYear }}</p>
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

        <div class="form-control">
          <div class="mb-3 fs-5">
            <p class="fs-5">Статус: </p>
            <p class="fs-6">{{ status }}</p>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: ['dataApplied', 'photo', 'fio', 'birthday', 'profession', 'city', 'phone', 'mail', 'education', 'educationInstitution', 'faculty', 'specialization', 'graduationYear', 'salary', 'skills', 'about', 'status', 'educationBlocks']
  };
  </script>
  
  <style scoped>
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
  }
  </style>
  