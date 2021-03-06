<template>
  <div class="home">
    <div class="hero">
      <img
        v-if="data.heroImage"
        :src="$withBase(data.heroImage)"
        alt="hero"
      >

      <h1>{{ data.heroText || $title }}</h1>

      <p class="description">
        {{ data.tagline || $description }}
      </p>

      <div class="contact" v-if="data.contact">
        <div class="email ml-5" v-if="data.contact.email && data.contact.email.length">
        <p v-if="data.contact.email && data.contact.email.length">
          ✉️ <a :href="'mailto:' + data.contact.email" alt="mail">{{ data.contact.email }}</a>
        </p>
        </div>
        <div class="location ml-5" v-if="data.contact.location && data.contact.location.length">
          <img class="icon" :src="$withBase('./map.png')" :alt="data.contact.location">
          <p>{{ data.contact.location }}</p>
        </div>
        <div class="gh ml-5" v-if="data.contact.github && data.contact.github.length">
          <img class="icon" :src="$withBase('./Octocat.png')" :alt="data.contact.github">
          <a :href="'https://github.com/' + data.contact.github">{{ data.contact.github }}</a>
        </div>
      </div>

      <div id="clk-ih31341" class="hidden"></div>

      <p
        class="action"
        v-if="data.actionText && data.actionLink"
      >
        <NavLink
          class="action-button"
          :item="actionLink"
        />
      </p>
    </div>

    <div
      class="features"
      v-if="data.features && data.features.length"
    >
      <div
        class="feature"
        v-for="feature in data.features"
      >
        <h2>{{ feature.title }}</h2>
        <p>{{ feature.details }}</p>
      </div>
    </div>

    <Content custom/>

    <div
      class="footer"
      v-if="data.footer"
    >
      {{ data.footer }}
    </div>
  </div>
</template>

<script>
import NavLink from "./NavLink.vue";

export default {
  components: { NavLink },

  computed: {
    data() {
      return this.$page.frontmatter;
    },

    actionLink() {
      return {
        link: this.data.actionLink,
        text: this.data.actionText
      };
    }
  }
};
</script>

<style lang="stylus">
@import './styles/config.styl';

.home {
  padding: $navbarHeight 2rem 0;
  max-width: 960px;
  margin: 0px auto;

  .hidden {
    visibility: hidden;
    display: none;
  }

  .ml-5 {
    margin-left: 5px;
  }

  .hero {
    text-align: center;

    img {
      max-height: 280px;
      display: block;
      margin: 3rem auto 1.5rem;
    }

    h1 {
      font-size: 3rem;
    }

    h1, .description, .action {
      margin: 1.8rem auto;
    }

    .description {
      max-width: 35rem;
      font-size: 1.6rem;
      line-height: 1.3;
      color: lighten($textColor, 40%);
    }

    .contact {
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 0px 5px;

      .icon {
        display: block;
        max-height: 25px;
        margin: 0px;
      }

      .email {
        display: flex;
        align-items: center;
      }

      .location {
        display: flex;
        justify-content: flex-start;
        align-items: center;

        p {
          margin-left: 1px;
        }
      }

      .gh {
        display: flex;
        align-items: center;
      }
    }

    .action-button {
      display: inline-block;
      font-size: 1.2rem;
      color: #fff;
      background-color: $accentColor;
      padding: 0.8rem 1.6rem;
      border-radius: 4px;
      transition: background-color 0.1s ease;
      box-sizing: border-box;
      border-bottom: 1px solid darken($accentColor, 10%);

      &:hover {
        background-color: lighten($accentColor, 10%);
      }
    }
  }

  .features {
    border-top: 1px solid $borderColor;
    padding: 1.2rem 0;
    margin-top: 2.5rem;
    display: flex;
    flex-wrap: wrap;
    align-items: flex-start;
    align-content: stretch;
    justify-content: space-between;
  }

  .feature {
    flex-grow: 1;
    flex-basis: 30%;
    max-width: 30%;

    h2 {
      font-size: 1.4rem;
      font-weight: 500;
      border-bottom: none;
      padding-bottom: 0;
      color: lighten($textColor, 10%);
    }

    p {
      color: lighten($textColor, 25%);
    }
  }

  .footer {
    padding: 2.5rem;
    border-top: 1px solid $borderColor;
    text-align: center;
    color: lighten($textColor, 25%);
  }
}

@media (max-width: $MQMobile) {
  .home {
    .contact {
      .location {
        p {
          max-width: 100px;
        }
      }
    }

    .features {
      flex-direction: column;
    }

    .feature {
      max-width: 100%;
      padding: 0 2.5rem;
    }
  }
}

@media (max-width: $MQMobileNarrow) {
  .home {
    padding-left: 1.5rem;
    padding-right: 1.5rem;

    .hero {
      img {
        max-height: 210px;
        margin: 2rem auto 1.2rem;
      }

      h1 {
        font-size: 2rem;
      }

      h1, .description, .action {
        margin: 1.2rem auto;
      }

      .description {
        font-size: 1.2rem;
      }

      .action-button {
        font-size: 1rem;
        padding: 0.6rem 1.2rem;
      }
    }

    .feature {
      h2 {
        font-size: 1.25rem;
      }
    }
  }
}
</style>
