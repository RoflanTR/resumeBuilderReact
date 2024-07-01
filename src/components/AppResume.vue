<template>
    <div class="card card-w70">
      <h3 v-if="resume.length==0">Добавьте первый блок, чтобы увидеть результат</h3>
      <!-- <div v-for="item in resume" :key="item">
            <h1 v-if="item.type=='title'">{{ item.text }}</h1>
            <h2 v-if="item.type=='subtitle'">{{ item.text }}</h2>
            <p v-if="item.type=='text'">{{ item.text }}</p>
            <div  class="avatar" v-if="item.type=='avatar'">
            <img :src="item.text" alt="avatar"></div>
      </div> -->
      <template v-else>
        <component v-for="item in resume" :key="item"
        :is="'resume-' + item.type"
        :value="item.text"
        > 
        </component>
      </template>
    </div>
</template>
<script>

import ResumeText from './parts/ResumeText.vue';
import ResumeTitle from './parts/ResumeTitle.vue';
import ResumeSubtitle from './parts/ResumeSubtitle.vue';
import ResumeAvatar from './parts/ResumeAvatar.vue'
export default {
    props:{
        resume: Array,
    },
    components:{ ResumeTitle,ResumeSubtitle,ResumeText,ResumeAvatar}
}
</script>