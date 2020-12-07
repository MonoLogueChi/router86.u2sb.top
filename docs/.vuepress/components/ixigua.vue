<template>
  <div>
    <iframe
      class="xgplayer"
      :src="src"
      allowfullscreen="allowfullscreen"
      scrolling="no"
      frameborder="0"
      sandbox="allow-top-navigation allow-same-origin allow-forms allow-scripts allow-popups"
    ></iframe>
    <script>
      var xgplayers = document.getElementsByClassName("xgplayer");
      xgplayers.forEach(function (item, index, arr) {
        item.style.height = item.scrollWidth * 0.7 + "px";
      });
      window.onresize = function () {
        xgplayers.forEach(function (item, index, arr) {
          item.style.height = item.scrollWidth * 0.7 + "px";
        });
      };
    </script>
  </div>
</template>

<script>
export default {
  props: {
    id: {
      type: String,
      default: null,
      required: true,
    },
    autoplay: {
      type: Boolean,
      default: false,
      required: false,
    },
    startTime: {
      type: Number,
      default: 0,
      required: false,
    },
  },
  data() {
    return {
      src: `//www.ixigua.com/iframe/${this.id}?autoplay=${
        this.autoplay ? 1 : 0
      }&startTime=${this.startTime}`,
    };
  },
};
</script>

<style lang="stylus" scoped>
.xgplayer {
  width: 100%;
}
</style>
