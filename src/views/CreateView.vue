<template>
  <form @submit.prevent="createList">
    <div class="">
      <label>Title</label>
      <input type="text" v-model="title" required/>
    </div>

    <div class="">
      <label>Detail</label>
      <textarea type="text" v-model="detail" required/>
    </div>

    <button>Create</button>
  </form>
</template>

<script>
export default {
    data(){
        return {
            title : "",
            detail : "",
            api : 'http://localhost:3000/lists/'
        }
    },
    methods : {
        createList(){
            fetch(this.api,{
                method : "POST",
                headers : {"Content-type" : "application/json"},
                body : JSON.stringify({
                    title : this.title,
                    detail : this.detail,
                    finished : false
                })
            })
            .then(()=>{
                this.$router.push('/')
            })
            .catch((err)=>{
                console.log(err)
            })
        }
    }
};
</script>

<style>
form {
  width: 700px;
  padding: 0 50px;
  color :rgb(196, 190, 190);
  margin: 0 auto;
}
label {
  display: block;
  margin: 6px auto;
  text-transform: capitalize;
  letter-spacing: 1px;
  font-size: 1.2rem;
  font-weight: 700;
}
input ,textarea {
  width: 100%;
  background-color: transparent;
  border: transparent;
  border-bottom: 2px solid #9e1b9c;
  margin: 6px auto;
  height: 40px;
  color: #6f086e;
  font-weight: 800;
}
button {
  display: block;
  margin: 10px auto;
  padding: 8px 16px;
  background-color: #600d5f;
  color: white;
  border: none;
  border-radius: 10px;
}
button:hover {
  background-color: #9e1b9c;
}
</style>
