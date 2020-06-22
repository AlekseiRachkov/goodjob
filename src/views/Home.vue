<template>
  <div class="home">
    <urtehn :li='li' />
  </div>
</template>

<script>
// @ is an alias to /src
import urtehn from '@/components/urTehn.vue'

export default {
  props: ['li'],
  name: 'about2',
  components: {
    urtehn
  },
  data() {
    return {
      // l: console.log(this.li)
    }
  }
}
</script>
