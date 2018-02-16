<template>
  <div id="app" class="container">
    <form>
      <h1>Work experiences</h1>
      <div class="work-experiences">

        <div class="form-row" v-for="(experience, index) in workExperiences" :key="index">
          <div class="form-group col-md-6">
            <label>Company</label>
            <input v-model="experience.company" :name="`workExperiences[${index}][company]`" type="text" class="form-control" placeholder="Company">
          </div>
          <div class="form-group col-md-6">
            <label>Title</label>
            <input v-model="experience.title" :name="`workExperiences[${index}][title]`" type="text" class="form-control" placeholder="Title">
          </div>
        </div>
      </div>

      <div class="form-group">
        <button @click="addExperience" type="button" class="btn btn-secondary">Add experience</button>
      </div>
      
      <hr>

      <div class="form-group">
        <button @click="submit" type="button" class="btn btn-primary">Submit</button>
      </div>
    </form>
  </div>
</template>

<script>

export default {
  name: "App",
  
  data: () => ({
    workExperiences: [
      {
        company: "Foxconn",
        title: "Engineer"
      },
      {
        company: "Cherri Tech",
        title: "Software Engineer"
      }
    ]
  }),

  methods: {
    addExperience () {
      this.workExperiences.push({
        company: '',
        title: ''
      })
    },

    submit () {
      const data = {
        workExperiences: this.workExperiences
      }
      alert(JSON.stringify(data, null, 2))
    }
  }
};
</script>

<style>
.work-experiences > div {
  margin: 20px 0;
  padding-bottom: 10px;
}
.work-experiences > div:not(:last-child) {
  border-bottom: 1px solid rgb(206, 212, 218);
}
</style>
