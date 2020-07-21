<template>
    <div class="edit">
        <header>
            <nuxt-link to="/">返回</nuxt-link>
        </header>
        <AddInput/>
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
    .edit{
        padding:20px;
        padding-top: 50px;
    }
</style>