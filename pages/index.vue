<template>
  <div class="container">
    <div>
      <Logo class="logo" />
      <p class="title">
        书签管理
      </p>
    </div>
    <main>
      <section class="eidt">
        <AddInput/>
      </section>
    </main>
  </div>
</template>

<script>
import AddInput from '../components/AddInput'
export default {
  components:{
    AddInput
  }
}
</script>

<style lang="scss" scoped>
.container{
  /deep/ .logo{
    width: 50px;
    height:50px;
  }
  .title{
    font-size: 16px;
  }
}
</style>
