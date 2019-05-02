<template>
      <div id="app">
          <home :title="title" v-if="show"></home>
          <!--<home-content></home-content>-->
          <router-view></router-view>
      </div>
</template>

<script>
    import Home from './components/Home'
    export default {
        name: 'App',
        data(){
            return{
                title:''
                ,show:true
            }
        }
        , components:{
            Home
        }
        ,async created(){
        let {data:{title}} = await this.$axios.get('/api/v2/movie/top250?count=20&&start=0');
        this.title = title;
        // console.log(subjects)
    }

    }
</script>

<style>
    *{
        margin:0;
        padding: 0;
    }
    body{
        background: #000;
    }
</style>
