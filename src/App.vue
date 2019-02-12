<template>
  <div id="app">
    <section class="container content background--white">
      <div class="row">
        <div class="column small-full">
          <h2><strong>Ease</strong> Gradients</h2>
        </div>
      </div>
    </section>
    <section class="container content background--yellow">
      <div class="row">
        <div class="column small-full">
          <p>
            Easings are cool and so are gradients. So combining them is really
            cool! It is possible using some plugins, but what if you could just
            use them with Sass?
          </p>
        </div>
      </div>
    </section>
    <section class="container content background--white">
      <div class="row">
        <div class="column small-full">
          <h3>Examples</h3>
        </div>
      </div>
    </section>
    <section class="background--white gradients">
      <div class="row blocks">
        <div
          class="column small-half medium-quarter block"
          :class="ease"
          v-for="(ease, index) in easings"
          :key="index"
        >
          <div class="block__example"></div>
          <h5>{{ ease }}</h5>
        </div>

        <div class="column small-half medium-quarter block bezier1">
          <div class="block__example"></div>
          <h5>Bezier Curve &mdash; 0 0 1 1</h5>
        </div>
        <div class="column small-half medium-quarter block bezier2">
          <div class="block__example"></div>
          <h5>Bezier Curve &mdash; 0 1 1 0</h5>
        </div>
        <div class="column small-half medium-quarter block bezier3">
          <div class="block__example"></div>
          <h5>Bezier Curve &mdash; 0.75 0 0.25 1</h5>
        </div>
        <div class="column small-half medium-quarter block bezier4">
          <div class="block__example"></div>
          <h5>Bezier Curve &mdash; 0 0.75 0.25 1</h5>
        </div>
      </div>
    </section>

    <section class="background--dark container installation">
      <div class="row">
        <div class="column small-full">
          <h2>Installation</h2>
        </div>
      </div>
    </section>

    <section class="background--dark installation">
      <div class="row columns">
        <div class="column small-full medium-third">
          <h4>Henris</h4>
          <p>Ease gradients is a included in Henri's, a styling</p>
          <p>
            <code>npm install @henris</code>
          </p>
          <p>Read more about Henri's <a href="https://henris.style">here</a></p>
        </div>
        <div class="column small-full medium-third">
          <h4>Install from NPM</h4>
          <p>Install ease-gradients as a seperate package</p>
          <p>
            <code>npm install @henris/ease-gradients</code>
          </p>
          <p>and import it into your scss.</p>
          <p><code>@import '~@henris/ease-gradients;</code></p>
        </div>
        <div class="column small-full medium-third">
          <h4>Copy the code</h4>
          <p>Below you find the code of this scss function.</p>
        </div>
      </div>
    </section>
    <section class="container background--blue">
      <div class="row">
        <div class="column small-full content">
          <h3>Use</h3>
          <p>
            If you have it installed, you can easily used it instead of your
            normal 'linear-gradients'.
          </p>
          <h5>Predefined gradients:</h5>
          <p>Use any of the gradients above.</p>
          <p>
            <span v-for="(ease, index) in easings" :key="index"
              >{{ ease }},
            </span>
          </p>
          <p>
            <code
              >background-image: ease-gradient(to bottom, red,
              black,'easeOutQuad');
            </code>
          </p>

          <h5>Or beziers!</h5>
          <p>
            You can also use cubic beziers, use them without the function and
            they should work just fine.
          </p>

          <p>
            <code
              >background-image: ease-gradient(to bottom, red, black, 0 0 1 1);
            </code>
          </p>
          <h5>But!</h5>
          <p>
            There are a few limitations (unfortunately). So check this before
            you so keep these in mind:
          </p>
          <ul>
            <li>Maximum of two colors</li>
            <li>No CSS custom properties (Sass can't compile those).</li>
            <li>
              The ease should be the last argument, otherwise the function will
              just respond with a regular linear-gradient.
            </li>
          </ul>
        </div>
      </div>
    </section>
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
        "easeInOutQuart",
        "easeInQuint",
        "easeOutQuint",
        "easeInOutQuint",
        "easeInSine",
        "easeOutSine",
        "easeInOutSine"
      ]
    };
  },
  name: "app"
};
</script>

<style lang="scss">
@import "assets/scss/app.scss";
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
  "easeInOutCubic",
  "easeInQuart",
  "easeOutQuart",
  "easeInOutQuart",
  "easeInQuint",
  "easeOutQuint",
  "easeInOutQuint",
  "easeInSine",
  "easeOutSine",
  "easeInOutSine"
);

.columns {
  .column {
    padding: grid(1);
    &:nth-child(1) {
      background-color: color(Black, 0.25);
    }
    &:nth-child(2) {
      background-color: color(Black, 0.5);
    }
    &:nth-child(3) {
      background-color: color(Black, 0.75);
    }
  }
}
.gradients {
  overflow: scroll;
  padding: grid(1);
  .block {
    @each $ease in $easings {
      &.#{$ease} {
        .block__example {
          background-image: ease-gradient(
            0deg,
            color(Green, 1),
            color(Blue, 0.25),
            $ease
          );
        }
      }
    }
    &.bezier1 .block__example {
      background-image: ease-gradient(
        0deg,
        color(Green, 1),
        color(Blue, 0.25),
        0 0 1 1
      );
    }
    &.bezier2 .block__example {
      background-image: ease-gradient(
        0deg,
        color(Green, 1),
        color(Blue, 0.25),
        0 1 1 0
      );
    }
    &.bezier3 .block__example {
      background-image: ease-gradient(
        0deg,
        color(Green, 1),
        color(Blue, 0.25),
        0.75 0 0.25 1
      );
    }
    &.bezier4 .block__example {
      background-image: ease-gradient(
        0deg,
        color(Green, 1),
        color(Blue, 0.25),
        0 0.75 0.25 1
      );
    }
  }
  .blocks {
    flex-wrap: nowrap;
    .block {
      padding: 1rem;
      flex-shrink: 0;
      &__example {
        display: block;
        width: 100%;
        height: 0;
        padding-bottom: 200%;
        border-radius: 4px;
      }
    }
  }
}
code {
  display: inline-block;
  background-color: color(Black);
  padding: 0.5rem;
  border-radius: 2px;
  font-family: unquote($typography-fonts-mono);
  font-size: 14px;
}
</style>
