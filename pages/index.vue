<template>
  <div class="container">
    <div>
      <Logo class="logo" />
      <p class="title">
        书签管理
      </p>
    </div>
    <main>
      <header>
           <nuxt-link to="/edit">edit</nuxt-link>
      </header>
      <section class="index">
        <Table/>
      </section>
    </main>
    <p class="token">测试TOKEN:{{this.list.access_token}}</p>
  </div>
</template>

<script>
import Table from '../components/Table'
export default {
  async asyncData(context){
    const data = {
      email:'123@123.com',
      password:'123456'
    }
    const data2 = {
      uuid:'00843ef0-cb3a-11ea-ba1f-690a5b5467c6'
    }

    const [res1,res2] = await Promise.all([
        context.$axios.post('http://api2.xuewuzhijing.top/api/auth/login',data).then(res=>res),
        context.$axios.get('https://api.xuewuzhijing.top/admin/statusQr',{params:data2}).then(res=>res)
      ])

      return {
        list:res1.data,
        typeData:res2.data
      }
  },

  data:()=>({
    list:null,
    typeData:null
  }),
  components:{
    Table
  }
}
</script>

<style lang="scss" scoped>
.container{
  padding: 20px;
  /deep/ .logo{
    width: 50px;
    height:50px;
  }
  .title{
    font-size: 16px;
  }
  p.token{
    width: 500px;
    word-break: break-all;
  }
}
</style>
