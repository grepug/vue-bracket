<template lang="jade">
  template(v-for="(index, group) in list")
    h3 第{{index + 1}}组
    table
      tr(v-for="(index2, el) in group.teams")
        td {{index2 + 1}}
        td {{el.nickname}}
        td {{el.scores.join('-')}}
    table
      tr(v-for="(index2, el) in group.matches")
        td(:class="{active: el.winnerIndex === 0}") {{el.teams[0].nickname}}
        td {{scores(el.scores)}}
        td(:class="{active: el.winnerIndex === 1}") {{el.teams[1].nickname}}
</template>

<script>
  export default {
    methods: {
      scores (arr) {
        return arr.map(el => el.join(':')).join(' ')
      }
    },
    props: {
      list: {
        type: Array,
        default () {
          return [
            {
              teams: [
                {
                  nickname: 'sk',
                  objectId: '',
                  scores: [2, 0]
                }, {
                  nickname: 'grepug',
                  scores: [2, 1]
                }, {
                  nickname: 'abc',
                  scores: [1, 2]
                }, {
                  nickname: 'shaokai',
                  scores: [0, 2]
                }
              ],
              matches: [
                {
                  teams: [
                    {
                      nickname: 'sk',
                    }, {
                      nickname: 'grepug',
                    }
                  ],
                  scores: [[11, 15], [15, 13], [15, 12]],
                  winnerIndex: 0
                }, {
                  teams: [
                    {
                      nickname: 'abc',
                    }, {
                      nickname: 'shaokai',
                    }
                  ],
                  scores: [[11, 15], [12, 15]],
                  winnerIndex: 1
                }
              ]
            }
          ]
        }
      }
    }
  }
</script>

<style lang="less" scoped>
  h3 {
    text-align: center;
  }
  table {
    border-collapse:collapse;
    margin: 0 auto;
    tr {
      td {
        border: 1px solid #000;
        padding: 0.5rem 1rem;
      }
      td.active {
        // color: #fff;
        // background-color: red;
        color: red;
      }
    }
  }
</style>
