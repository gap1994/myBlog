<template>
  <div class="container">
    <h1>404 Not Found</h1>
    <span>Oops ! The page is not here</span>
    <div><a href="/">back to home</a></div>
  </div>
</template>

<style scoped>
.container{
  position: absolute;
  width: 40%;
  top: 20%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
}

@media only screen and (max-width: 767px) {
  .container{
    width: 80%;
  }
}
@media only screen and (min-width: 768px) {
  .container{
    width: 80%;
  }
}
</style>

