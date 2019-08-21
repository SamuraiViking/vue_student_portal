<template>
  <div class="home">
    <div>
      <h1>Profile</h1>
      <div> {{ student_profile.first_name }} </div>
      <div> {{ student_profile.last_name }} </div>
      <div> {{ student_profile.email }} </div>
      <div> {{ student_profile.phone_number }} </div>
    </div>
    <div>
      <h1>Capstone</h1>
      <div> {{ student_capstones.name }} </div>
      <div> {{ student_capstones.description }} </div>
      <div> {{ student_capstones.url }} </div>
      <div> {{ student_capstones.screenshot }} </div>
    </div>
    <div>
      <h1>Experiences</h1>
      <div> {{ student_experiences.start_date }} </div>
      <div> {{ student_experiences.end_date }} </div>
      <div> {{ student_experiences.job_title }} </div>
      <div> {{ student_experiences.company_name }} </div>
      <div> {{ student_experiences.details }} </div>
    </div>
    <div>
      <h1>Skills</h1>
      <div v-for="skill in student_skills">
        <div> {{ skill.name }}</div>
      </div>
    </div>
    <div>
      <h1>Education</h1>
      <div> {{ student_education.start_date }} </div>
      <div> {{ student_education.end_date }} </div>
      <div> {{ student_education.degree }} </div>
      <div> {{ student_education.university }} </div>
      <div> {{ student_education.details }} </div>
    </div>
  </div>
</template>

<style>
</style>

<script>
import axios from 'axios'
export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      student_profile: '',
      student_capstones: '',
      student_experiences: '',
      student_skills: '',
      student_education: ''
    };
  },
  created: function() {
    axios.get("/api/students").then(response => {
      this.student_profile = response.data.profile;
      this.student_capstones = response.data.capstones[0];
      this.student_experiences = response.data.experiences[0];
      this.student_skills = response.data.skills;
      this.student_education = response.data.educations[0];
    });
  },
  methods: {
  }
};
</script>