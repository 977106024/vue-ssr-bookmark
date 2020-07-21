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
    <p>测试TOKEN:{{this.list.access_token}}</p>
  </div>
</template>

<script>
import AddInput from '../components/AddInput'
export default {
  async asyncData(context){
    const data = {
      email:'123@123.com',
      password:'123456'
    }
    const data2 = {}

    const [res1,res2] = await Promise.all([
        context.$axios.post('http://api2.xuewuzhijing.top/api/auth/login',data).then(res=>res),
        context.$axios.get('https://aip.baidubce.com/oauth/2.0/token?grant_type=client_credentials&client_id=f17IpDaOaBrKhSU1X4KEAIlT&client_secret=nEP7ix9bKMxGd23LmGW482sVXQY80G2a').then(res=>res)
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
