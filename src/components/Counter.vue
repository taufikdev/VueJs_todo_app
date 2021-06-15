<template>
  <div class="container">
    <div class="jumbotron mt-5" id="circle">
       <span>tasks count: <b>{{number}}</b></span>
    </div>
  </div>
</template>

<script>
export default {
  props: ['number']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#circle {
    font-family:Verdana, Geneva, Tahoma, sans-serif;
    font-size: 10px;
    font-weight: 900;
    width: 100px;
    height: 60px;
    background: rgba(22, 153, 214, 0.664);
    -moz-border-radius: 50px;
    -webkit-border-radius: 50px;
    border-radius: 40px;
    box-shadow: 1px 1px #d6d5d5;
    text-align: center;
    color:beige;
    padding-top: 2.2em;
}
</style>
