<template>
  <div id="app">
    <div class="t-header">
      <div class="t-header__con">
        <span>yandex</span>
      </div>
    </div>
    <div class="linecolor"></div>
    <div class="t-main">
      <div class="w05 fl">
        <translateform v-on:formSub="transText"></translateform>
      </div>
      <div class="w05 fl">
        <translateout v-text="finishText"></translateout>
      </div>
    </div>
  </div>
</template>

<script>
  import Translateform from './components/Translateform.vue'
  import Translateout from './components/Translateout.vue'
export default {
  name: 'app',
  components:{
    Translateform,
    Translateout
  },
  data:function (){
    return{
      finishText:''
    }
  },
  methods:{
    transText(text,type){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20171123T055432Z.02088faa962e2fe9.96c7293f7afb91ed734c2c0431331f458a2d9976&lang='+type+'&text='+text)
        .then((response)=>{
          this.finishText=response.data.text[0];
      })
    }
  }
}
</script>

<style lang="scss">
  html{
    height:100%;
  }
  body{
    height:100%;
    border:0;
    margin:0;
    padding: 0;
  }
  .w05{
    width: 50%;
  }
  .fl{
    float: left;
  }
  #app {
    height: 100%;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    background: #f9f9f9;
  }
  .t-header{
    height: 60px;
    margin:0 auto;
    background: #fff;
    .t-header__con{
      width: 1220px;
      margin:0 auto;
      span{
        float: left;
        height: 60px;
        line-height: 65px;
        font-size: 36px;
      }
    }
  }
  .linecolor{
    height:1px;
    background-image:linear-gradient(to right,red,orange,yellow,green,cyan,blue,purple);
  }
  .t-main{
    width: 1220px;
    height: calc(100% - 62px);
    margin:0 auto;
  }
</style>
