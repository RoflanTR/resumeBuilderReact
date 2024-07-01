<template>
  <div class="container column">
    <app-form-vue @submitInfo="submitForm"></app-form-vue>
    <app-resume :resume="resume"></app-resume>
  </div>
  <app-comment></app-comment>
</template>

<script>
import AppFormVue from "./components/AppForm.vue";
import AppResume from "./components/AppResume.vue";
import AppComment from "./components/AppComment.vue";
export default {
  data() {
    return {
      resume:[],
      
    };
  },
  methods:{
    submitForm(typeForm,textForm){
      this.resume.push({type:typeForm,text:textForm})
      console.log(this.resume)
    }
    
  },
  components: { AppFormVue,AppResume,AppComment },
};
</script>


