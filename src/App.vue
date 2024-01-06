<template>
  <div class="app container-fluid py-3">
    <header class="row d-flex justify-content-center align-items-center mx-0 my-4">
      <h1 class="col-auto">Header</h1>
      <a class="col-auto" href="https://www.youtube.com/watch?v=geT5dQIaarU">Урок</a>
    </header>
    <dragAndDrop/>
  </div>


</template>
<script>
import dragAndDrop from './components/dragAndDrop.vue'
export default {
  components:{
    dragAndDrop
  },
}
</script>


<style scoped lang="scss">
.app{
  background: #d4dcc8;
  min-height: 100vh;
  header{
    background-color: yellowgreen;
    padding: 20px;
    border-radius: 10px;
    font-size: 20px;
    color: mediumblue;
    h1{
      font-size: inherit;
      margin: 0;
    }
    a{
      text-decoration: none;
      color: inherit;
      position: relative;
      border-radius: 10px;
      padding: 5px 45px 5px 10px;
      &:hover{
        background: #d4dcc8;
      }
      &:after {
        content: "";
        position: absolute;
        top: 7px;
        right: 7px;
        background: center / contain no-repeat url("assets/youtube.png");
        width: 30px;
        height: 30px;
      }

    }
  }
}
</style>
