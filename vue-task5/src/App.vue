<template>
  <div id="app">
    <Form @applyData="applyFormData" v-if="!dataApplied" />
    <Resume :dataApplied="dataApplied" :photo="photo" :fio="fio" :birthday="birthday" :profession="profession"
      :city="city" :phone="phone" :mail="mail" :education="education" :educationInstitution="educationInstitution"
      :faculty="faculty" :specialization="specialization" :graduationYear="graduationYear" :salary="salary"
      :skills="skills" :about="about" :status="status" :educationBlocks="educationBlocks"/>
  </div>
</template>

<script>
import Form from './components/Form.vue';
import Resume from './components/Resume.vue';

export default {
  components: {
    Form,
    Resume,
  },
  data() {
    return {
      dataApplied: false,
      // Данные, которые будут переданы в Resume.vue
      photo: '',
      fio: '',
      birthday: '',
      profession: '',
      city: '',
      phone: '',
      mail: '',
      education: '',
      educationInstitution: '',
      faculty: '',
      specialization: '',
      graduationYear: '',
      salary: '',
      skills: '',
      about: '',
      status: '',
      educationBlocks: '',
    };
  },
  methods: {
    applyFormData(formData) {
      // Обновление данных при событии "Применить" в Form.vue
      this.dataApplied = true;
      this.photo = formData.photo;
      this.fio = formData.fio;
      this.birthday = formData.birthday;
      this.profession = formData.profession;
      this.city = formData.city;
      this.phone = formData.phone;
      this.mail = formData.mail;
      this.education = formData.education;
      this.educationInstitution = formData.educationInstitution;
      this.faculty = formData.faculty;
      this.specialization = formData.specialization;
      this.graduationYear = formData.graduationYear;
      this.salary = formData.salary;
      this.skills = formData.skills;
      this.about = formData.about;
      this.status = formData.status;
      this.educationBlocks = formData.educationBlocks;
    },
  },
};
</script>
