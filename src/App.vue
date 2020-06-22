<template>
  <div id="app">
    <form class="form noprint" v-if="!password(v,fi)">
      <p class="noprint">Введите пароль</p>
      <input v-model="fi" required>
    </form>
    <section v-if="password(v,fi)">
      <div id="nav" class="noprint">
        <!-- <router-link to="/">Предварительный договор</router-link> |
        <router-link to="/about">Основной договор</router-link> |
        <router-link to="/about1">Юр. лицо договор</router-link> | -->
        <router-link to="/">Договор на технику (click me please)</router-link>
        <!-- <router-link to="/test">TEST</router-link> -->
      </div>
      <router-view :li="fi"/>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      fi: '',
      v: false
    }
  },
  methods: {
    password(e, elem) {
      elem = Number(elem)

      if (elem === 11 || elem === 12 || elem === 13) {
        return !e
      } else {
        return e
      }
    }
  }
}
</script>

<style lang="stylus">
@import './styles/smart-grid'

#app
  font-family 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  margin-top 60px
  @media print
    font-size 10px !important
    h2
      font-size 18px !important
    h3
      font-size 14px !important

body
  background-color #f6f3eb
  @media print
    background white
section
  margin 0 auto
  reset()

.form
  display flex
  justify-content center
  align-items center
  input
    width 200px

.container
  width 100%
  wrapper()

.table
  mixSize(100%)
  & th, td
    $listTable = 20% 10% 10% 10% 10% 10% 15% 15%
    for item, index in $listTable
      &:nth-child({index + 1})
        mixSize(item)
  &-dostavka
    & th, td
      $listTableDost = 50% 50%
      for item, index in $listTableDost
        &:nth-child({index + 1})
          mixSize(item)

.main
  row-flex()
  flex-direction column
  &-item
    margin 5px 0;
    flex-c()
    col()
    size(12)
    p
      line-height 1.5em;
    select
      margin-left 10px
      background-color $bg
    &-block
      mixSize(50%)
    &__check
      outline none
      margin-left 20px
      position relative
      background-color $bg
      border: 4px solid $border
      mixSize(20px)
      height 20px
      &_good
        &::after
          position absolute
          content ''
          top calc(50% - 7px)
          left calc(50% - 7px)
          mixSize(14px)
          height 14px
          background-color $border

form
  input
    font-size 16px
    margin-left 10px
    padding 0
    display block
    mixSize(100%)
    border none
    border-bottom 1px solid #ccc
    background-color $bg
    &:focus
      outline none

table
  tr
    td
      padding 5px
      mixSize(50%)
      text-align left

.btn
  text-decoration none
  outline none
  display inline-block
  width auto
  border-radius 5px
  margin-bottom 20px
  padding 10px
  font-family 'Montserrat', sans-serif
  font-size 11px
  text-transform uppercase
  text-align center
  letter-spacing 3px
  font-weight 600
  color #524f4e
  background #c4c4c4
  box-shadow 0 8px 15px rgba(0, 0, 0, 0.1)
  transition .3s
  border 0
  &:hover
    cursor pointer
    background #434241
    box-shadow 0 15px 20px rgba(216, 16, 116, 0.4)
    color white
    transform translateY(-7px)

.break
  page-break-before always
  @media print
    page-break-before always
    margin-top 10px!important

@media print
  .noprint
    display: none

h2
  font-size 24px !important
  font-weight bold !important
h3
  margin-top 4px !important
  font-size 18px !important
  font-weight bold !important
.sb
  justify-content space-between
.colum
  flex-direction column
  justify-content flex-start
  align-items flex-start
  text-align left

.ml-40
  margin-left 40px

.ta
  &c
    text-align center
  &r
    text-align right
  &l
    text-align left

.fish
  &-print
    @media print
      margin-top -60px
      margin-right 15px
  &-printmr
    @media print
      margin-right 15px

.ml-20
  margin-left 20px

.error
  border-bottom 1px solid red !important
</style>
