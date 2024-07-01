<template>
    <form class="card card-w30" @click.prevent="submit">
      <div class="form-control">
        <label for="type">Тип блока</label>
        <select id="type" v-model="typeForm">
          <option value="title">Заголовок</option>
          <option value="subtitle">Подзаголовок</option>
          <option value="avatar">Аватар</option>
          <option value="text">Текст</option>
        </select>
      </div>

      <div class="form-control">
        <label for="value">Значение</label>
        <textarea id="value" rows="3" v-model="textForm"></textarea>
      </div>

      <button :disabled="disabledBtn" type= "submit" class="btn primary" @click="$emit('submitInfo',typeForm,textForm), textForm='', typeForm='title'" >Добавить</button>
    </form>
</template>
<script>
export default {
    data(){
        return{
            typeForm:'title',
            textForm:'',
            
        }
    },
    computed:{
        disabledBtn(){
            return this.textForm.length>3?false:true
        }
    }
}
</script>