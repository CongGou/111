<template>
    <div class="filmslist">
        <ul>
            <!--<li v-for="subject in subjects">-->
                <!--<img class="img" :src="subject.images.small" alt="">-->
                <!--<p>{{subject.original_title}}</p>-->
                <!--<p>-->
                    <!--<span v-for="genre in subject.genres">-->
                        <!--{{genre}}-->
                    <!--</span>-->
                <!--</p>-->
            <!--</li>-->
            <router-link :to="{name:'SingleFilm',params:{id:subject.id}}" v-for="(subject,index) in subjects" tag="li" :key="index">
                <img class="img" :src="subject.images.small" alt="">
                <p>{{subject.original_title}}</p>
                <p>
                    <span v-for="genre in subject.genres">
                        {{genre}}
                    </span>
                </p>
            </router-link>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "FilmList"
        , data() {
            return {
                subjects:[]
            }
        }
        ,async created(){
            let {data:{subjects}} = await this.$axios.get('/api/v2/movie/top250?count=20&&start=0');
            this.subjects = subjects;
            // console.log(subjects)
        }
        , watch:{
           $route:{
               async handler(){
                   let {data:{subjects}} = await this.$axios.get('/api/v2/movie/top250?count=20&&start='+this.$route.query.page*20);
                   this.subjects = subjects;
               }
           }
        }

    }
</script>

<style scoped>
    .filmslist ul{
        list-style-type: none;
    }
    .filmslist ul li{
        float: left;
        width: 280px;
        margin: 10px 10px 10px 10px;
        background: #222;
        cursor: pointer;
    }
    .img{
        width: 280px;
        height: 390px;
    }
    .filmslist ul li h4{
        color: #ccc;
    }
    .filmslist ul li p{
        height: 22px;
        color: #666;
    }
</style>
