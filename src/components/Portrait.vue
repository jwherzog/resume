<template>
  <div v-if='this.$store.getters.basic' class='block' id='portrait'>
    <el-avatar :size='100' @error='errorHandler'>
      <img src='https://media-exp1.licdn.com/dms/image/C4E03AQHX0igP7vr1Mw/profile-displayphoto-shrink_200_200/0?e=1590624000&v=beta&t=gPmMBsileuYzx6FQZFXWRIQrxQQE0lq_MFVQbR5QfV8' />
    </el-avatar>
    <h1>{{ this.$store.getters.basic.name }}</h1>
    <p id='baseInfo'>
     <!--  <span class="dmg-info"><i :class='this.$store.getters.basic.gender.fa' /><span class='info-left'>{{ this.$store.getters.basic.gender.value }}</span></span>
      <span class="dmg-info"><i :class='this.$store.getters.basic.dob.fa' /><span class='info-left'>{{ calcAge(this.$store.getters.basic.dob.value) }}</span></span> -->
      <!-- <span class="dmg-info"><i :class='this.$store.getters.basic.marriage.fa' /><span class='info-left'>{{ this.$store.getters.basic.marriage.value }}</span></span> -->
      <span class="dmg-info">
        <i :class='this.$store.getters.basic.home.fa' />
        <a :href='this.$store.getters.basic.home.link' target='_blank'><span class='info-right'>{{ this.$store.getters.basic.home.value }}</span></a>
      </span>

    </p>
    <p style="color:#fff;">
      <!-- <pre id='motto'><i class='fas fa-quote-left'/>{{ this.$store.getters.basic.motto }}<i class='fas fa-quote-right'/></pre> -->
     
       <pre id='motto'><i class='fas fa-quote-left'/><vue-typer
                   class="typing-list"
                  :text= this.$store.getters.basic.motto 
                  :repeat='Infinity'
                  :shuffle='false'
                  initial-action='typing'
                  :pre-type-delay='70'
                  :type-delay='80'
                  :pre-erase-delay='2000'
                  :erase-delay='60'
                  erase-style='backspace'
                  :erase-on-complete='false'
                  caret-animation='blink'
                  /><i class='fas fa-quote-right'/></pre>
            
    </p>
  </div>
</template>

<script>
import { parseTimeDif, dec } from '@/utils/util'
export default {
  computed: {

  },
  methods: {
    errorHandler () {
      return true
    },
    calcAge (t0, t1 = 'now') {
      const d = parseTimeDif(t0, t1)
      return d['y']
    },
    dec (s) {
      return dec(s)
    }
  },
  components: {
    VueTyper: () => import('vue-typer').then(m => m.VueTyper)
  },
}
</script>

<style lang='scss' scoped>
#portrait {
  text-align: center;
  margin: $mar-md
}
h1, h2, h3, h4, h5, h6, p {
  color: $col-bg
}
h1 {
  font-size: x-large;
  font-weight: thin
}
pre {
  color: #000;
}
#baseInfo i.fas {
  color: $col-main-alt;
  font-size: small
}
#baseInfo a:link {
  color: $col-bg
}
#baseInfo a:visited {
  color: $col-text
}
#baseInfo a:hover {
  color: $col-ok
}
.info-left {
  margin-left: 4px;
  margin-right: $mar-md
}
.info-right {
  margin-left: 4px
}
.typing-list {
  color:#fff;
}
#motto .typed {
   color: $col-text-alt
}
.dmg-info:hover {
  color: $col-ok
}
#motto .fa-quote-left {
  margin-top: -3px;
  margin-right: 8px;
  vertical-align: text-top
}
#motto .fa-quote-right {
  margin-bottom: -1px;
  margin-left: 8px;
  vertical-align: text-bottom
}
</style>
