<template>
  <div class="ajax">
    <h1 class="f-name">通过Ajax获取豆瓣接口数据</h1>
    <div class="f-cont">
      <div class="f-tt"><h2>豆瓣电影排行榜</h2></div>
      <ul class="f-lst">
        <li v-for="(film, index) in films" class="f-item">
          {{ index+1 }}. {{film.title}}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {

    data: function() {

      return {

        films: []

      }

    },

    mounted: function() {
      this.$http.jsonp('https://api.douban.com/v2/movie/top250?count=10', {}, {
          headers: {

          },
          emulateJSON: true
      }).then(function(response) {
        // 这里是处理正确的回调

          this.films = response.data.subjects
          // this.articles = response.data["subjects"] 也可以

      }, function(response) {
          // 这里是处理错误的回调
          console.log(response)
      });
    }

  }
</script>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}
.f-cont {
  width: 500px;
  border: 1px solid #D3DCE6;
  border-radius: 4px;
  background-color: #fff;
  overflow: hidden;
}
.f-tt {
  padding: 18px 20px;
  border-bottom: 1px solid #D3DCE6;
  box-sizing: border-box;
}
.f-tt h2 {
  line-height: 36px;
  color: #20A0FF;
}
.f-lst {
  padding: 20px;
}
.f-item {
  font-size: 16px;
  line-height: 26px;
  color: #14A033;
}
</style>