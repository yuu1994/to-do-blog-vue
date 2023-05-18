<template>
  <header>
    <div class="align">
        <h2>To Do Blog</h2>
    </div>
    <div class="nav">
        <router-link :to="{name:'home'}">Home</router-link>
        <router-link :to="{name:'create'}">Create</router-link>
    </div>
  </header>
</template>

<script>
export default {

}
</script>

<style>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
h2 {
    color: rgb(196, 190, 190);
    font-size: 100px;
    font-weight: 800;
    font-family: 'Mogra', cursive;
}
.nav a {
    color: rgb(94, 88, 88);
    text-decoration: none;
    margin: 0 20px;
    padding: 10px;
    font-weight: 700;
}
.nav a.router-link-active {
    color: rgb(196, 190, 190);
    border-bottom: 2px solid #6be293;
}
</style>