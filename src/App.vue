<template lang="jade">
  .bracket.clearfix(:style="{width: result.length * 125 + (result.length - 1) * 50 + 15 + 'px'}")
    template(v-for="(index, r) in result")
      .bracket-column
        h4.round 第{{index + 1}}轮
        .bracket-column-game(v-for="p in r.result")
          .bracket-cell(v-for="cell in p", style="width: 125px", :style="{height: Math.pow(2, index) * 40 + 'px'}")
            ul.race
              li
                img(:src="cell.headimgurl", src="http://wx.qlogo.cn/mmopen/PiajxSqBRaEK3OiaEFu3GUzEJsVuBECq3Sl5GPXNBakIQ5yN6po3GP98n2osawuw7SCeQibwJwSB4lU99kssS8gSQ/0")
              li
                span(v-text="cell.nickname")
              li
                span(v-text="cell.score || 0")
      .bracket-arrow(v-if="index < result.length - 1")
        h4(style="visibility: hidden") 1
        div(v-for="el in r.result")
          div(style="width: 25px;", :style="{height: Math.pow(2, index) * 40 + 'px'}")
          div(style="width: 25px;", :style="{height: Math.pow(2, index) * 40 + 'px'}")
          div(style="width: 25px;", :style="{height: Math.pow(2, index) * 40 + 'px'}")
          div(style="width: 25px;", :style="{height: Math.pow(2, index) * 40 + 'px'}")
</template>

<script>
export default {
  props: {
    result: {
      type: Array,
      default () {
        return [
          {
            round: 8,
            result: [
              [
                {
                  nickname: 'grepug'
                }, {
                  nickname: 'sk'
                }
              ],
              [
                {
                  nickname: 'grepug'
                }, {
                  nickname: 'sk'
                }
              ],
              [
                {
                  nickname: 'grepug'
                }, {
                  nickname: 'sk'
                }
              ],
              [
                {
                  nickname: 'grepug'
                }, {
                  nickname: 'sk'
                }
              ]
            ]
          }, {
            round: 4,
            result: [
              [
                {
                  nickname: 'grepug'
                }, {
                  nickname: 'sk'
                }
              ],
              [
                {
                  nickname: 'grepug'
                }, {
                  nickname: 'sk'
                }
              ]
            ]
          }, {
            round: 2,
            result: [
              [
                {
                  nickname: 'grepug'
                }, {
                  nickname: 'sk'
                }
              ]
            ]
          }
        ]
      }
    }
  }
}
</script>

<style scoped>
* {
  box-sizing: border-box;
}
h4 {
  text-align: center;
}
.clearfix:after{
  content: " ";
  display: table;
  height: 0;
  clear: both;
  visibility: hidden;
}
.clearfix{*+height:1%;}
li {
  list-style: none;
}
.event-info {
  border: 1px solid #ddd;
  width: 100%;
}
.event-infobox{
  margin-bottom: 3px;
  margin-right: 0;
}
.event-infobox img {
  width: 100%;
}
.event-infobox:nth-child(2n+1){
  background-color: #eee;
}
.event-infobox .infobox-cell-1 {
  width: calc(50% - 4px);
  float: left
}
.event-infobox .infobox-cell-2 {
  width: calc(50% - 4px);
  float: left
}
.participants .col-xs-4{
  padding-left: 0;
  padding-right: 0;
}
.participants ul {
  padding-left: 15px;
}
.participants li {
  display: inline;
}
.bracket {
  overflow: auto;
}
.bracket .bracket-column{
  /*margin-right: 30px;*/
  float: left;
}
.bracket .bracket-column.bracket-arrow > div{
  width: 20px;
  height: 3px;
  background-color: #000;
}
.bracket .bracket-column .bracket-column-game{
  position: relative;
}
.bracket .bracket-column .bracket-column-game .bracket-cell{
  position: relative;
  height: 50px;
  width: 125px;
}
.bracket .bracket-column .bracket-column-game ul{
  padding-left: 0;
  margin: 0;
  position: absolute;
  left: 0;
  right: 0;
  padding: 3px;
  border: 1px solid #000;
}
.bracket .bracket-column .bracket-column-game .bracket-cell:first-child ul{
  bottom: 0;
  border-bottom: 0;
}
.bracket .bracket-column .bracket-column-game .bracket-cell ul li:nth-child(2)::before {
  content: ',';
  visibility: hidden;
}
.bracket .bracket-column .bracket-column-game ul li{
  display: inline-block;
  height: 100%;
  margin-right: 3px;
}
.bracket .bracket-column .bracket-column-game ul li:nth-child(2){
  /*padding-right: 23px;*/
}
.bracket .bracket-column .bracket-column-game ul li:last-child{
  /*float: right;*/
  border-left: 1px solid #000;
  margin-right: 0;
  position: absolute;
  right: 0;
  top: 0;
}
.bracket .bracket-column .bracket-column-game ul li:last-child span{
  padding: 5px;
  line-height: 34px;
}
.tbd {
  padding: 3.8px !important;
}
.tbd::after{
  content: '0';
  visibility: hidden;
}
.bracket-arrow {
  /*border: 1px solid #000;*/
  width: 50px;
  float: left;
}
.bracket-arrow > div {
  float: left;
  width: 25px;
}
.bracket-arrow > div:nth-child(2n) > div:nth-child(2){
  border-top: 1px solid #999;
  border-right: 1px solid #999;
}
.bracket-arrow > div:nth-child(2n) > div:nth-child(3){
  border-right: 1px solid #999;
}
.bracket-arrow > div:nth-child(2n) > div:nth-child(4){
  border-top: 1px solid #999;
}
.bracket-arrow > div:nth-child(2n+1) > div:nth-child(3){
  border-top: 1px solid #999;
}
.win {
  font-weight: bold;
}
.champion {
  font-weight: bold;
  color: red;
}
.race.p {
  background-color: rgb(184,242,184);
}
.race.t {
  background-color: rgb(184,184,242);
}
.race.z {
  background-color: rgb(242,184,184);
}
img {
  width: 20px;
}
</style>
