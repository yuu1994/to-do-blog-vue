<template>
  <div class="filter">
    <div class="">
        <button @click="checkFilter('all')" :class="{check:check=='all'}">All</button>
    </div>
    <div class="">
        <button @click="checkFilter('ongoing')" :class="{check:check=='ongoing'}">Ongoing</button>
    </div>
    <div class="">
        <button @click="checkFilter('complete')" :class="{check:check=='complete'}">Completed</button>
    </div>
  </div>
</template>

<script>
export default {
    props : ['check'],
    methods : {
        checkFilter(value){
            this.$emit('checkfilter',value)
        }
    }
}
</script>

<style>
.filter {
    display: flex;
    justify-content: space-around;
    margin: 5px auto;
}
.filter div button {
    background-color: transparent;
    border-radius: 0;
    color: rgb(196, 190, 190);
    font-weight: 700;
    border-bottom: 2px solid transparent;
}
.check{
    border-bottom: 2px solid #6be293 !important;
}
</style>