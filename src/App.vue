<template>
  <div id="app">
    <AppHeader/>
    <main>
      <AppNav/>
      <router-view/>
    </main>
    <AppFooter/>
  </div>
</template>

<script>
  import AppHeader from "@/components/AppHeader.vue"
  import AppNav from "@/components/AppNav.vue"
  import AppFooter from "@/components/AppFooter.vue"

  export default {
    components: {
      AppHeader,
      AppNav,
      AppFooter
    }
  }
</script>

<style lang="scss">
  body {
    margin: 0;
    padding: 0;
    font-family: 'Indie Flower', 'Arial', cursive;
    overflow-y: scroll;
    background: white;
  }

  ul, li, a {
    margin: 0;
    padding: 0;
    text-decoration: none;
    list-style: none;
  }

  #app {
    margin: 0;
    display: grid;
    min-height: 100vh;
    grid-template-rows: minmax(150px, min-content) 1fr minmax(5vh, auto);
    grid-row-gap: 5px;
    grid-column-gap: 2px;
  }

  #app > *:not(main) {
    background: black;
  }

  main {
    display: flex;
    flex-direction: column;
    background: white;
  }

  @media (min-width: $desktop) {
    #app {
      grid-template-rows: minmax(200px, min-content) 1fr 7vh;
      grid-row-gap: 5px;
      grid-column-gap: 5px;
    }

    main {
      flex-direction: row;
    }
  }
</style>
