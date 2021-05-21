<template>
    <input
      v-if="type"
      :class="classes" 
      :type="type"
      :value="value"
      @click="onClick"
    />

    <a
      v-else-if="href"
      :class="classes"
      :href="href"
      :target="target"
    >
      <slot></slot>
    </a>

    <button
      v-else
      :class="classes"
      @click="onClick"
    > 
      <slot></slot>
    </button>
</template>

<script>
export default {
  name: 'Button',

  props: {
    type: {
      type: String,
      default: null,
    },

    href: {
      type: String,
      default: null,
    },

    target: {
      type: String,
      default: null,
      validator (value) {
        return [
          '_blank', //	Opens the linked document in a new window or tab
          '_self', //	Opens the linked document in the same frame as it was clicked (this is default)
          '_parent', //	Opens the linked document in the parent frame
          '_top', //	Opens the linked document in the full body of the window
          'framename', //	Opens the linked document in the named iframe
        ].indexOf(value) !== -1
      }
    },

    value: {
      type: String,
      required: false,
    },

    isPrimary: {
      type: Boolean,
      default: false,
    },

    isLink: {
      type: Boolean,
      default: false,
    },

    isInfo: {
      type: Boolean,
      default: false,
    },

    isSuccess: {
      type: Boolean,
      default: false,
    },

    isWarning: {
      type: Boolean,
      default: false,
    },

    isDanger: {
      type: Boolean,
      default: false,
    },

    isWhite: {
      type: Boolean,
      default: false,
    },

    isLight: {
      type: Boolean,
      default: false,
    },

    isDark: {
      type: Boolean,
      default: false,
    },

    isBlack: {
      type: Boolean,
      default: false,
    },

    isText: {
      type: Boolean,
      default: false,
    },

    isGhost: {
      type: Boolean,
      default: false,
    },
   
  },

  computed: {
    classes () {
      return {
        'button': true,
        'is-white': this.isWhite,
        'is-light': this.isLight,
        'is-dark': this.isDark,
        'is-black': this.isBlack,
        'is-text': this.isText,
        'is-ghost': this.isGhost,
        'is-primary': this.isPrimary,
        'is-link': this.isLink,
        'is-info': this.isInfo,
        'is-success': this.isSuccess,
        'is-warning': this.isWarning,
        'is-danger': this.isDanger,
      }
    },
  },

  methods: {
    onClick (e) {
      this.$emit('click', e)
    }
  }
}
</script>