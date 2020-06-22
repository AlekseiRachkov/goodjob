<template lang="pug">
  .div.mr-20
    .break
    .main-item
      table(border='1' cellspacing="0" cellpadding="2")
        tbody
          tr
            th(v-for="j of title" :key="j.id")
              h3.tac {{j}}
          tr(v-for="j in text" :key="j.id")
            td {{j.name}}
            td {{j.c1}}
            td {{j.c2}}
            td {{j.c3}}
            td {{j.c4}}
            td {{j.c5}}
            td {{j.c6}}
            td {{j.c7}}
</template>

<script>
import {t, tx} from '../lib/table'

export default {
  data() {
    return {
      title: t,
      titless: console.log(t),
      text: tx
    }
  }
}
</script>
