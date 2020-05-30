<template>
  <div id='app'>
    <transition name="fade" mode="out-in" :duration=120>
      <div class="page-wrapper" v-if="hasPlayers">
        <navbar />
        <transition name="fade" mode="out-in" :duration=120>
          <router-view />
        </transition>
      </div>
      <players v-else />
    </transition>
  </div>
</template>

<script>
import {
  mapState,
  mapGetters
} from 'vuex';

import Navbar from './components/atoms/Navbar.vue'
import Players from './components/molecules/Players.vue'

export default {
  name: 'App',
  components:{
    Navbar,
    Players,
  },

  computed: {
    ...mapState([
      'gameHistory'
    ]),
    ...mapGetters([
      'hasPlayers'
    ])
  }
};
</script>

<style lang="scss">
@import 'src/scss/app.scss';
</style>
