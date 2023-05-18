<template>
  <form @submit.prevent="editList">
    <div class="">
      <label>Title</label>
      <input type="text" v-model="title" />
    </div>

    <div class="">
      <label>Detail</label>
      <textarea type="text" v-model="detail" />
    </div>

    <button>Create</button>
  </form>
</template>

<script>
export default {
    props : ['id'],
    data(){
        return {
            title : '',
            detail : '',
            api : 'http://localhost:3000/lists/'
        }
    },
    methods :{
        editList(){
            fetch(this.api + this.id,{
                method : "PATCH",
                headers : {"Content-type" : "application/json"},
                body : JSON.stringify({
                    title : this.title,
                    detail : this.detail
                })
            })
            .then(()=>{
                this.$router.push('/')
            })
            .catch((err)=>{console.log(err)})
        }
    },
    mounted(){
        fetch(this.api+this.id)
        .then((res)=>{
            return res.json()
        })
        .then((data)=>{
            this.title = data.title
            this.detail = data.detail
        })
        .catch((err)=>{console.log(err)})
    }
}
</script>

<style>

</style>