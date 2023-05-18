<template>
  <div class="list"  :class="{finished:list.finished}">
    <div class="flexing">
      <div class="" @click="showDetail = !showDetail">
        <h5>{{ list.title }}</h5>
      </div>
      <div class="icon">
        <span @click="deleteList"><i class="fa-solid fa-trash"></i></span>
        <router-link :to="{name:'edit', params:{id:list.id}}"><span><i class="fa-solid fa-pen-to-square"></i></span></router-link>
        <span @click="checkFinished" :class="{checked:list.finished}"><i class="fa-solid fa-check"></i></span>
      </div>
    </div>
    <p v-if="showDetail">{{ shortDetail }}</p>
  </div>
</template>

<script>
export default {
  props: ["list"],
  data() {
    return {
      showDetail: false,
      api : "http://localhost:3000/lists/"
    };
  },
  methods : {
    checkFinished(){
        let checkfinishedroute = this.api + this.list.id
        fetch(checkfinishedroute,{
            method : "PATCH",
            headers : {"Content-type" : "application/json"},
            body : JSON.stringify({
                finished : !this.list.finished
            })
        })
        .then(()=>{
            this.$emit('checkfinishedroute',this.list.id)
        })
        .catch((err)=>{
            console.log(err)
        })
    },
    deleteList(){
      let deleteRoute = this.api + this.list.id 
      fetch(deleteRoute,{
        method : "DELETE"
      })
      .then(()=>{
        this.$emit('deleteList',this.list.id)
      })
      .catch((err)=>{console.log(err)})
    }
  },
  computed: {
    shortDetail() {
      return this.list.detail.substring(0, 20) + "...";
    },
  },
};
</script>

<style>
.list {
  background-color: rgb(228, 228, 228);
  width: 70%;
  margin: 20px auto;
  border: none;
  border-radius: 15px;
  padding: 10px 30px;
  border-left: 5px solid red;
}
h5 {
  color: rgb(96, 96, 215);
  cursor: pointer;
}
.flexing {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
span {
  padding: 10px;
}
span i {
  font-size: 20px;
  cursor: pointer;
}
.finished {
    border-left: 5px solid rgb(37, 213, 37);
}
.icon a{
  text-decoration: none;
}
.checked {
  color: rgb(37, 213, 37);
}
</style>
