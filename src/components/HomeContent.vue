<template>
    <div class="content">
        <film-list></film-list>
        <film-page :maxPage="maxPage"></film-page>
    </div>
</template>

<script>
    import FilmList from './FilmList'
    import FilmPage from './FilmPage'

    export default {
        name: "HomeContent"
        ,data(){
            return {
                maxPage: ''
                ,
            }
        }
        ,components:{
            FilmList
            ,FilmPage
        }
        ,async created(){
            this.$router.push({
                path:'/'
                ,query:{
                    page:0
                }
            })
            this.$root.$children[0].show = true;
            let {data:{count},data:{total}} = await this.$axios.get('/api/v2/movie/top250?count=20&&start=0');
            this.maxPage = Math.ceil(total/count);
        }
    }
</script>

<style scoped>
    .content{
        width: 1200px;
        margin: auto;
        background: lightblue;
    }
</style>
