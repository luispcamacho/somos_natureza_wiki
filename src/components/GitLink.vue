<template>
  <a href="https://github.com/luispcamacho/somos_natureza_wiki" :class="size" title="Git-repository" aria-label="Somos Natureza on Github">
    <font-awesome-icon icon="user-secret" />
    {{text}}
  </a>
</template>

<script>
import { GithubIcon } from 'vue-feather-icons'

import { library } from '@fortawesome/fontawesome-svg-core'
import { faUserSecret } from '@fortawesome/free-solid-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

export default {
  components: {
    FontAwesomeIcon
  },
  props: {
    size: {
      type: String,
      default: 'small'
    },
    text: {
      type: String,
      default: 'Fork me on Github'
    }
  }
}
</script>

<style lang="scss" scoped>
a {
  display: inline-block;
  padding: 6px 10px;
  text-decoration: none;
  border-radius: 3px;
  font-size: 12px;
  line-height: 18px;
  font-weight: 700;
  transition: color .15s ease-in-out, background .15s ease-in-out;

  &:focus {
    outline: none;
  }

  .dark & {
    color: $textBright;
    background: $backgroundBright;
  }

  .bright & {
    color: $textDark;
    background: $backgroundDark;
  }

  svg {
    width: 18px;
    height: 18px;
    vertical-align: -6px;
    margin-right: 4px;
  }

  &.large {
    @include respond-above(sm) {
      font-size: 18px;
      padding: 12px 20px;
      line-height: 24px;

      svg {
        width: 24px;
        height: 24px;
      }
    }
  }
}
</style>

