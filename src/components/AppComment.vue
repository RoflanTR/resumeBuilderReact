<template>
    <div class="container">
    <p>
      <button class="btn primary" @click="loadComment">Загрузить комментарии</button>
    </p>
    <div v-if="enableComment" class="card">
      <h2>Комментарии</h2>
      <ul class="list">
        <li class="list-item" v-for="com in comment" :key="com.id">
          <div >
            <p><strong>{{com.email}}</strong></p>
            <small
              >{{com.body}}.</small
            >
          </div>
        </li>
      </ul>
    </div>
    <div class="loader" v-if="enableLoader"></div>
  </div>
</template>
<script>
export default {
    data(){
        return{
            enableComment:false,
            comment:[],
            enableLoader:false
        }
    },
    methods:{
        async loadComment(){
            try {
                this.enableLoader=true
            this.enableComment=true
            const mas = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42',{
                method:'GET'
            })
            this.comment = await mas.json()
            console.log(this.comment)
            this.enableLoader=false
            } catch (error) {
                this.enableLoader=false
            }
        }
    }
}
</script>