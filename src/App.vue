<template>
  <div id="app">
    <section class="container content background--white">
      <h4>Curved Gradients</h4>
    </section>
    <div class="gradients">
      <div class="block">
        <h4>Bezier Curve</h4>
      </div>
      <div class="blocks">
        <div
          class="block"
          :class="ease"
          v-for="(ease, index) in easings"
          :key="index"
        >
          <h5>{{ ease }}</h5>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      easings: [
        "easeIn",
        "easeInQuad",
        "easeOutQuad",
        "easeInOutQuad",
        "easeInCubic",
        "easeOutCubic",
        "easeInOutCubic",
        "easeInQuart",
        "easeOutQuart",
        // "easeInOutQuart",
        "easeInQuint",
        "easeOutQuint",
        // "easeInOutQuint",
        "easeInSine",
        "easeOutSine",
        "easeInOutSine",
        "easeInExpo",
        // "easeOutExpo",
        "easeInOutExpo"
        // "easeInCirc",
        // "easeOutCirc",
        // "easeInOutCirc"
      ]
    };
  },
  name: "app"
};
</script>

<style lang="scss">
@import "~@sil/base-style/src/scss/index.full";
@import "assets/scss/easing/ease";
html,
body {
  margin: 0;
  padding: 0;
  width: 100%;
  min-height: 100%;
}

$easings: (
  "easeIn",
  "easeInQuad",
  "easeOutQuad",
  "easeInOutQuad",
  "easeInCubic",
  "easeOutCubic",
  // "easeInOutCubic",
    "easeInQuart",
  "easeOutQuart",
  // "easeInOutQuart",
    "easeInQuint",
  "easeOutQuint",
  // "easeInOutQuint",
    "easeInSine",
  "easeOutSine",
  "easeInOutSine",
  "easeInExpo",
  // "easeOutExpo",
    // "easeInOutExpo",
    // "easeInCirc",
    // "easeOutCirc",
    // "easeInOutCirc"
);
.gradients {
  height: 100%;
  width: 100%;
  .block {
    width: 100%;
    height: 100%;
    padding: 2rem;

    // @each $ease in $easings {
    //   &.#{$ease} {
    //     background-image: ease-gradient(
    //       0deg,
    //       color(Green, 1),
    //       color(Blue, 0.25),
    //       $ease
    //     );
    //   }
    // }
    &.bezier {
      background-image: ease-gradient(
        0deg,
        color(Green, 1),
        color(Blue, 0.25),
        0 0 1 1
      );
    }
  }
  .blocks {
    display: flex;
    flex-wrap: wrap;
    .block {
      width: grid(4);
      height: grid(4);
      @media #{$medium-only} {
        width: grid(6);
        height: grid(6);
      }
      @media #{$small-only} {
        width: grid(12);
        height: grid(6);
      }
    }
  }
}
</style>
