<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
    <div class="wrapper">
    </div>
  </header>

  <main>
    <TabNav :tabs="['Home', 'Settings', 'Profile']" :selected="selected" @selected="setSelected">
      <Tab :isSelected="selected === 'Home'">
        <p>Some test text</p>
      </Tab>
      <Tab :isSelected="selected === 'Settings'">
        <h1>More test text</h1>
      </Tab>
      <Tab :isSelected="selected === 'Profile'">
        <ul>
          <li>list 1</li>
          <li>list 2</li>
          <li>list 3</li>
        </ul>
      </Tab>
    </TabNav>
  </main>
</template>

<script>
import TabNav from './components/TabNav.vue';
import Tab from './components/Tab.vue';

export default {
  name: 'App',
  components: { TabNav, Tab },
  data() {
    return {
      selected: 'Home'
    }
  },
  methods: {
    setSelected(tab) {
      this.selected = tab;
    }
  }
}
</script>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
