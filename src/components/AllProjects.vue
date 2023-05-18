<template>
  <div class="search">
    <input type="text" v-model="search" placeholder="search"/>
  </div>
    <div class="">
        <FilterList @checkfilter="check = $event" :check="check"></FilterList>
    </div>
  <div class="" v-for="list in filterLists" :key="list.id">
    <SingleProject
      :list="list"
      @checkfinishedroute="checkfinishedroute"
      @deleteList="deleteList"
    ></SingleProject>
  </div>
</template>

<script>
import FilterList from './FilterList'
import SingleProject from "./SingleProject";
export default {
  components: {
    FilterList, SingleProject },
  data() {
    return {
      lists: [],
      search: "",
      check : "all"
    };
  },
  methods: {
    checkfinishedroute(id) {
      let finishedList = this.lists.find((list) => {
        return list.id == id;
      });
      finishedList.finished = !finishedList.finished;
    },
    deleteList(deleteId) {
      this.lists = this.lists.filter((list) => {
        return list.id != deleteId;
      });
    },
    // checkFilter(value){
    //     this.check = value
    //     console.log(this.check)
    // }
  },
  computed: {
    filterLists() {
      return this.lists.filter((list) => {
        if (this.search != "") {
          return list.title.includes(this.search);
        }
        if(this.check == 'complete'){
            return list.finished
        }
        if(this.check == 'ongoing'){
            return !list.finished
        }
        return list;
      });
    },
  },
  mounted() {
    fetch("http://localhost:3000/lists")
      .then((res) => {
        return res.json();
      })
      .then((data) => {
        this.lists = data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style>
.search {
    width: 20%;
}
.search input::placeholder{
    color: rgb(62, 61, 61);
    font-weight: 600;
}
.search input {
    border: 2px solid #9e1b9c;
    border-radius: 20px;
    padding: 5px 20px;
}
</style>
