<template>
    <div class="edit">
        <header>
            <nuxt-link to="/">返回</nuxt-link>
        </header>
        <AddInput @submit="submit"/>
    </div>
</template>

<script>
import AddInput from '../components/AddInput'
export default {
    methods:{
        submit(value){
            const data =  {...value}
            this.$axios.post('http://api2.xuewuzhijing.top/api/auth/login',data).then(res=>{
                console.log(res)
            })
        }
    },
    components:{
        AddInput
  }
}
</script>

<style lang="scss" scoped>
    .edit{
        padding:20px;
        padding-top: 50px;
    }
</style>