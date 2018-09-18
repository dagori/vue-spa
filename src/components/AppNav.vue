<template>
  <nav>
    <h3 class="nav-menu">Menu</h3>
    <ul class="link">
      <router-link class="link__item link__item--gallery" tag="li" to="/" exact>Gallery</router-link>
      <router-link class="link__item link__item--blog" tag="li" to="/blog">Blog</router-link>
      <router-link class="link__item link__item--contacts" tag="li" to="/contacts">Contacts</router-link>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'AppNav'
}
</script>

<style lang="scss">
  nav {
    background: black;
    margin-bottom: 5px;
  }

  .nav-menu {
    margin-top: 5px;
    text-align: center;
    color: white;
  }

  li {
    color: white;
    transition: letter-spacing 1s;
    cursor: pointer;
    font-size: 18px;
  }

  .link__item:hover {
    letter-spacing: 5px;
  }

  .link__item.router-link-active {
    letter-spacing: 5px;
    font-weight: bold;
  }

  .link {
    padding: 0px 20px 10px;
    margin-bottom: 5px;
  }

  .link__item {
    margin-top: 7px;
  }

  .link__item--blog .blog {
    padding-left: 10px;
    display: none;
  }

  .link__item--blog.router-link-active .blog {
    display: block;
  }

  .blog__item.router-link-active {
    color: red;
  }

  @media (min-width: $desktop) {
    nav {
      margin-bottom: 0;
      margin-right: 5px;
      min-width: 200px;
    }

    .link {
      padding: 10px 20px 10px;
    }

    .nav-menu {
      display: none;
    }
  }
</style>
