<template>
  <div id="app">
    <header class="header">
      <div class="header__left">
        <Logo v-if="showLogo" /> 
      </div>
      
      <div class="header__right">        
        <ToggleTheme />
      </div>
    </header>
    <transition name="fade" appear>
      <main class="main">
        <slot/>
      </main>
    </transition>
    <footer class="footer">
      <span class="footer__copyright">Copyright © {{ new Date().getFullYear() }}. </span>
      <span class="footer__links">Powered by <a href="//www.gap1994.xyz"> gap1994 </a></span>
      <span class="footer__beian"><a href="http://beian.miit.gov.cn">粤ICP备19024703号</a></span>
    </footer>

  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import ToggleTheme from '~/components/ToggleTheme.vue'

export default {
  props: {
    showLogo: { default: true }
  },
  components: {
    Logo,
    ToggleTheme
  }
}
</script>

<style lang="scss">
.bg{
  position: absolute;
  width: 100%;
  height: 75%;
  background-image: linear-gradient( 135deg, #65FDF0 10%, #1D6FA3 100%);
  z-index: -1;
}
.quick-menu{
  z-index: 999;
}
.fade-enter-active {
  transition: opacity .5s;
}

.fade-enter {
  opacity: 0;
}
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  min-height: var(--header-height);
  padding: 0 calc(var(--space) / 2);
  top:0;
  z-index: 10;

  &__left,
  &__right {
    display: flex;
    align-items: center;
  }

  @media screen and (min-width: 1300px) {
    //Make header sticky for large screens
    position: sticky;
    width: 100%;
  }
}

.main {
  margin: 0 auto;
  padding: 1.5vw 15px 0;
}

.footer {
  padding: calc(var(--space) / 2);
  text-align: center;
  font-size: .8em;
  float: left;
  width: 100%;
  > span {
    margin: 0 .35em;
  }
  &__beian {
    width: 100%;
    float: left;
  }

  a {
    color: currentColor;
  }
}
</style>
