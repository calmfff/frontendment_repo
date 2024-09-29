<template>
<div class="qr_code">
  <div class="qr_card">
    <img class="qr_img" src="../assets/img/image-qr-code.png" alt="">
    <div class="qr_title">
      Improve your front-end skills by building projects
    </div>
    <div class="qr_content">hese are just the design sizes. Ensure content is responsive and meets WCAG requirements by testing the full range of screen sizes from 320px to large screens.</div>
  </div>
</div>
  
</template>

<script setup>
</script>

<style lang="scss" scoped>
.qr_code{
  width: 100vw;
  height: 100vh;
  background-color: rgb(213,225,239);
  display: flex;
  align-items: center;
  justify-content: center;

  .qr_card{
    width: 20%;
    height: 50%;
    background-color: #FFF;
    margin:0 auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;
    border-radius: 8px;
    padding: 20px;

    .qr_img{
    width: 90%;
    height: 70%;
    border-radius: 8px;
    }

    .qr_title{
      font-weight: 900;
      text-align: center;
    }
    .qr_content{
      text-align: center;
      font-size: 15px;
      color: #ccc;
    }
  }
  
}
</style>
