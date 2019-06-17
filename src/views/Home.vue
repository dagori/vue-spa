<template>
  <div class="container__gallery gallery" @click="openImg">
    <div class="overlay" @click="closeImg"></div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-16.jpg">
    </div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-2.jpg">
    </div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-3.jpg">
    </div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-4.jpg">
    </div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-5.jpg">
    </div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-6.jpg">
    </div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-7.jpg">
    </div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-8.jpg">
    </div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-9.jpg">
    </div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-10.jpg">
    </div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-11.jpg">
    </div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-12.jpg">
    </div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-13.jpg">
    </div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-14.jpg">
    </div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-15.jpg">
    </div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-1.jpg">
    </div>
    <div class="gallery__item">
      <img alt="image" src="../assets/gallery/img-17.jpg">
    </div>
  </div>
</template>

<script>
  export default {
    name: 'home',
    data () {
      return {
        imgList: {},
        overlay: {},
        activeImg: false
      }
    },
    mounted: function () {
      this.$nextTick(function () {
        this.imgList = this.$el.querySelectorAll('.gallery__item'),
        this.overlay = this.$el.querySelector('.overlay')
      })
    },
    methods: {
      openImg: function (evt) {
        this.imgList.forEach((item) => {
          if(evt.target.tagName === 'IMG' && evt.target.parentElement === item) {
            this.activeImg = document.createElement('div');
            this.activeImg.className = 'active__img';
            this.activeImg.innerHTML = item.innerHTML;
            item.appendChild(this.activeImg);
            this.overlay.style.display = 'block';
          }
        })
      },
      closeImg: function () {
        if(this.activeImg) {
          this.activeImg.remove();
          this.overlay.style.display = 'none';
        }
      }
    }
  }
</script>

<style lang="scss" scoped>

  .gallery {
    display: grid;
    grid-gap: 3px;
  }

  .gallery__item {
    min-width: 100px;
  }

  .gallery__item img {
    display: block;
    width: 100%;
    height: 200px;
    object-fit: cover;
    filter: grayscale(0.7);
    transition: filter .8s;
  }

  @media (min-width: $tablet) {
    .gallery {
      grid-template-columns: repeat(2, 1fr);
    }

    .gallery__item {
      min-width: 200px;
    }

    .gallery__item img {
      height: 300px;
    }
  }

  @media (min-width: $desktop) {
    .gallery {
      grid-template-columns: repeat(4, 1fr);
    }
  }

  .gallery__item:hover > img:first-child{
    filter: grayscale(0);
  }

  .active__img > img {
    width: auto;
    height: auto;
    max-width: 90vw;
    max-height: 80vh;
    object-fit: contain;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 4;
    filter: grayscale(0);
  }

  .overlay {
    display: none;
    background: rgba(0, 0, 0, 0.7);
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 3;
  }
</style>
