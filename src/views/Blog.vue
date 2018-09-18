<template>
  <section  class="load-message" v-if="errored">
    <p>We're sorry, we're not able to retrieve this information at the moment, please try back later</p>
  </section>
  <section  v-else>
    <div class="load-message" v-if="loading">Loading...</div>
    <div class="container__blog" v-else>
      <div class="button-list">
        <button type="button" v-for="post in posts" v-bind:key="post.id" v-bind:class="['button-list__button', {active: post == currentPost}]" v-on:click="currentPost = post">
          {{ post.title }}
        </button>
      </div>
      <div class="post" v-if="currentPost" v-bind:class="['post__item']">
        <h2 class="post__title">{{ currentPost.title }}</h2>
        <div class="post__content">{{currentPost.content}}</div>
        <img v-bind:src="currentPost.photo[0]" class="post__image">
      </div>
    </div>
  </section>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'blog',
    data: function() {
      return {
        posts: null,
        currentPost: null,
        loading: true,
        errored: false
      }
    },
    mounted() {
      axios
        .get('https://www.mocky.io/v2/5b6f4b17310000ab14781ad1')
        .then(response => {
          this.posts = response.data;
          this.currentPost = response.data[0];
        })
        .catch(error => {
          error = true;
          this.errored = error;
        })
        .finally(() => (this.loading = false));
    }
  }
</script>

<style lang="scss" scoped>

  .container__blog {
    height: 100%;
  }

  .button-list {
    display: flex;
  }

  .button-list__button {
    background-color: blue;
    color: white;
    font-size: 80%;
    border: none;
    border-top-right-radius: 10px;
    border-top-left-radius: 10px;
    height: minmax(2em, auto);
    width: auto;
    padding: 3px;
    transition: transform, box-shadow;
    transition-delay: 0s, -0.5s;
    word-wrap: break-word;

    @for $i from 0 through 6 {
      &:nth-of-type(#{$i}n) {
        filter: hue-rotate(#{$i*15}deg);
      }
    }
    &.active {
      transform: translateY(-10px);
      box-shadow: 0 10px 0 0 blue;
    }
  }

  .load-message {
    font-size: 40px;
    padding-left: 10px;
  }

  .post {
    padding: 0 10px;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-between;
    text-align: justify;
    background-image: linear-gradient(to bottom, lightgray, transparent);
  }

  .post__title {
    flex-grow: 2;
    width: 100%;
  }

  .post__image {
    width: 100%;
    height: auto;
    align-self: stretch;
    object-fit: cover;
    margin-top: 5px;
  }

  @media (min-width: $tablet) {
    .button-list__button {
      font-size: 100%;
    }
  }

  @media (min-width: $desktop) {
    .post__content {
      width: calc(60% - 10px);
    }

    .post__image {
      width: 40%;
      max-width: 700px;
      max-height: 550px;
    }
  }
</style>
