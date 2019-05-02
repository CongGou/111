<template>
      <h1 class="title">
            {{title}}
      </h1>
</template>

<script>
    export default {

          data () {
            return {

            }
          }
          ,props:['title']
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h1{
        width: 1200px;
        margin: 0 auto 20px;
        border-bottom: 3px solid #2ad487;
        background-color: #222;
        color: #2ad487;
        line-height: 80px;
        text-indent: 20px;
    }

</style>
